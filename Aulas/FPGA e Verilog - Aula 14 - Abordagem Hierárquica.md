# FPGA e Verilog — **Aula 14: Abordagem Hierárquica**

> **Objetivo:** mostrar como **montar circuitos maiores** reutilizando **módulos menores** já descritos (blocos), e as duas formas de **mapeamento de portas** ao instanciar submódulos.

---

## 1) O que é **descrição por hierarquia**?

- Você **constrói blocos menores** (módulos) e depois **combina** esses blocos para formar um sistema maior.  
- É parecido com a **abordagem estrutural**, mas em vez de usar **primitivas** (`and`, `or`, `xor`…), aqui usamos **módulos** que **nós mesmos** definimos (ou de uma biblioteca).  
- Vantagens:
  - **Reutilização** (DRY): escreve uma vez, usa onde precisar.
  - **Organização**: cada bloco faz uma tarefa clara.
  - **Teste incremental**: simule/verifique cada módulo separadamente.

---

## 2) Como **instanciar** um módulo?

Forma geral:

```verilog
<nome_do_modulo> nome_da_instancia (mapeamento_de_portas);
```

- **`<nome_do_modulo>`**: exatamente o nome definido no `module`.
- **`nome_da_instancia`**: identificador único daquela cópia.
- **`mapeamento_de_portas`**: como as portas do submódulo conectam aos sinais do módulo “pai”.

Duas formas de mapeamento:

### 2.1. Mapeamento **por posição** (positional)

- As portas são passadas **na mesma ordem** em que foram declaradas no submódulo.
- **A ordem importa**.

```verilog
module half_adder (a, b, s, c);
//           ordem ↑  ↑  ↑  ↑
    input  a, b;
    output s, c;
    assign s = a ^ b;
    assign c = a & b;
endmodule

// Instanciação por posição:
half_adder ha1 (a1, b1, s1, c1); 
//             |   |   |   |
//             a   b   s   c  (mesma ordem do module)
```

### 2.2. Mapeamento **por nome** (named)

- As portas são **associadas pelo nome**, então **a ordem não importa**.
- Mais **legível** e **seguro** em módulos grandes.

```verilog
// Instanciação por nome:
half_adder ha2 (.a(a2), .b(b2), .s(s2), .c(c2));

// Ordem pode mudar sem problemas:
half_adder ha3 (.a(a3), .s(s3), .b(b3), .c(c3));
```

> **Boa prática:** prefira **mapeamento por nome** em projetos maiores.

---

## 3) Exemplo hierárquico: **Full Adder** a partir de **Half Adders**

Montar um **somador completo** usando **dois half adders** + **OR**.

### 3.1. Bloco básico: `half_adder.v`
```verilog
// half_adder.v
module half_adder (input  wire a,
                   input  wire b,
                   output wire s,
                   output wire c);
    assign s = a ^ b; // soma de meio bit
    assign c = a & b; // carry de meio bit
endmodule
```

### 3.2. Topo hierárquico: `full_adder.v`
```verilog
// full_adder.v
module full_adder (input  wire a,
                   input  wire b,
                   input  wire cin,
                   output wire s,
                   output wire cout);

    // fios internos
    wire s_ha1, c_ha1;
    wire s_ha2, c_ha2;

    // 1º half-adder: soma a e b
    half_adder HA1 (.a(a), .b(b),      .s(s_ha1), .c(c_ha1));

    // 2º half-adder: soma (a⊕b) com cin
    half_adder HA2 (.a(s_ha1), .b(cin), .s(s_ha2), .c(c_ha2));

    // saída final
    assign s    = s_ha2;
    assign cout = c_ha1 | c_ha2;

endmodule
```

> **Hierarquia em ação:** combinamos **blocos reutilizáveis** para criar um bloco maior.

---

## 4) Organização de arquivos e **Top-Level**

- Todos os submódulos instanciados devem estar **no mesmo projeto** (adicione os `.v`) ou **no mesmo arquivo**.  
- **Top-level** = **módulo principal** (aquele cujas portas vão para os pinos via **Pin Planner**).  
  - Configure em **Assignments > Settings > General > Top-level entity**.
- Boas práticas:
  - **Um arquivo por módulo** (`half_adder.v`, `full_adder.v`).
  - Nomes consistentes de instâncias (`HA1`, `HA2`, `FA0`…).
  - Considere `default_nettype none` para evitar fios implícitos.

```verilog
`default_nettype none
```

---

## 5) Dicas técnicas e pitfalls

- **Conflitos de nome**: instâncias distintas precisam de nomes distintos.  
- **Largura de barramentos**: para **N bits**, use vetores `[N-1:0]` e **`generate`** para replicar blocos.  
- **Parâmetros**: use `parameter` para módulos reutilizáveis.  
- **Mistura**: é válido instanciar **módulos** e **primitivas** na mesma hierarquia.  
- **Simulação**: teste **cada bloco** e depois o **top-level**.  
- **Síntese**: evite construções não sintetizáveis (ex.: `#delays` em lógica combinacional).

---

## 6) Exercício sugerido

1. Construa um **somador ripple-carry de 4 bits** (`rca4`) encadeando 4 `full_adders`.  
2. Escreva um **testbench** para `rca4` (varra `A[3:0]`, `B[3:0]`, `Cin`).  
3. Generalize para **N bits** com parâmetro e `generate`.

---

### TL;DR

- **Hierarquia** = reuso de módulos para compor sistemas maiores.  
- Instanciação por **posição** (ordem importa) ou por **nome** (ordem não importa; recomendado).  
- **Full adder** a partir de **half adders** é o exemplo clássico.
