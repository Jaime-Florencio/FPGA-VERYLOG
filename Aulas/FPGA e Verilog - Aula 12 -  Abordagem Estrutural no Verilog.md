# 📚 FPGA e Verilog – Aula 12  
## Abordagem Estrutural no Verilog  

**📅 Data:** 27/09/2025  
**📚 Tema:** Descrição estrutural (portas, blocos e interconexões)

---

### 📖 Resumo da Aula
A **abordagem estrutural** descreve o circuito em termos de **portas lógicas**, **blocos/módulos** e suas **interconexões**.  
É a forma de descrição que **mais se assemelha ao diagrama de portas** de um circuito digital.

---

## 🔧 Primitivas do Verilog
No Verilog, **primitivas** são portas embutidas na linguagem (não precisam de módulo externo):

| Tipo                         | Primitivas                          |
|-----------------------------|-------------------------------------|
| Portas multi‐entrada        | `and`, `or`, `nand`, `nor`, `xor`, `xnor` |
| Porta de uma entrada        | `not`, `buf`                        |
| Portas tri‐state (não usaremos no curso) | `bufif0`, `bufif1`, `notif0`, `notif1` |

**Sintaxe geral de instanciação:**
```verilog
<primitiva> nome_instancia (ligacoes);
```
- **ligacoes**: lista separada por vírgulas. **O primeiro sinal é SEMPRE a saída** da porta.
- **nome_instancia** é recomendado (ex.: `u0`, `u1`), mas não obrigatório.

**Exemplos:**
```verilog
// AND de duas entradas
and  u0 (x, a, b);   // x = a AND b

// NOT (inversor)
not  u1 (y, x);      // y = ~x

// XOR de três entradas
xor  u2 (s, a, b, cin); // s = a ^ b ^ cin
```

> Para conectar saídas e entradas entre portas, declare **variáveis do tipo `wire`** (fios internos).

---

## 🧩 Estrutura básica (relembrando)
```verilog
module nome_modulo (lista_de_portas);
    // declarações de portas (input/output/inout)
    // declarações internas (wire, reg, parameters)
    // instanciação de portas/módulos (conexões estruturais)
endmodule
```

---

## 🧠 Exemplo 1 — Meio Somador (Half Adder) em abordagem estrutural
```verilog
module half_adder (a, b, s, cout);
    input  a, b;
    output s, cout;

    // s = a XOR b
    xor u0 (s, a, b);

    // cout = a AND b
    and u1 (cout, a, b);
endmodule
```

---

## 🧠 Exemplo 2 — Somador Completo (Full Adder) com portas
```verilog
module full_adder (a, b, cin, s, cout);
    input  a, b, cin;
    output s, cout;

    wire axb, g1, g2;

    // axb = a XOR b
    xor u0 (axb, a, b);

    // soma: s = (a XOR b) XOR cin
    xor u1 (s, axb, cin);

    // carry: cout = (a AND b) OR (cin AND (a XOR b))
    and u2 (g1, a, b);
    and u3 (g2, cin, axb);
    or  u4 (cout, g1, g2);
endmodule
```

> Observação: a descrição acima é **100% estrutural** (apenas portas).  
> Alternativamente, poderíamos montar o `full_adder` **hierarquicamente** instanciando **dois `half_adder`** e uma porta `or`.

---

## 🗂️ Projeto da Aula
Nesta aula iniciamos o projeto:

**`Projeto/Projeto 01 - O primeiro circuito em Verilog`**  
Tarefa: **Descrever o Somador Completo (Full Adder) em Verilog** usando **abordagem estrutural** (portas).

**Imagem do diagrama:**  
Coloque a figura em `Aulas/Imagens/primeiroprojetoverilog.png` e referencie assim:

```markdown
![Diagrama – Full Adder](./Imagens/primeiroprojetoverilog.png)
```

> Lembre-se: o caminho acima é relativo ao arquivo da **Aula 12** dentro da pasta `Aulas/`.

---

## ✅ Dicas práticas
- Declare **`wire`** para todas as interligações internas entre portas.  
- O **primeiro sinal** na lista de uma primitiva é sempre a **saída**.  
- Nomeie as instâncias (`u0`, `u1`, …) para facilitar depuração.  
- Para testar no **ModelSim**, crie um **testbench** simples que varie `a`, `b`, `cin` e confira `s`, `cout`.

---

## 🏁 Conclusão
A abordagem **estrutural** constrói o circuito **porta a porta**, espelhando o diagrama lógico.  
É ideal para **compreensão de conexões** e **verificação de topologia**; nas próximas aulas veremos **fluxo de dados (RTL)** e **comportamental**, que agilizam a descrição quando o circuito cresce.
