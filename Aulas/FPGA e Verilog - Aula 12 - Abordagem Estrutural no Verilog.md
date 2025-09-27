# 📚 FPGA e Verilog – Aula 11  
## Estrutura Básica do Verilog  

**📅 Data:** 27/09/2025  
**📚 Tema:** Estrutura de um Módulo em Verilog  

---

### 📖 Resumo da Aula
Nesta aula, estudamos a **estrutura básica de um código em Verilog**, entendendo como declarar módulos, portas, parâmetros, dados internos (wire e reg) e diferentes formas de descrição de circuitos.  

---

## 🔹 Estrutura Geral de um Módulo

```verilog
module nome_modulo (lista_de_portas);

    // Declaração das portas (entradas, saídas, bidirecionais)
    // Declaração de dados intermediários
    // Descrição do funcionamento do circuito

endmodule
```

- Todo código em Verilog começa com **`module`** e termina com **`endmodule`**.  
- O nome do módulo é como se fosse o **nome do circuito**.  
- A lista de portas (entradas/saídas) aparece entre parênteses, separadas por vírgulas.  

---

## 🔹 Regras Importantes
- **Case-sensitive** → diferencia maiúsculas de minúsculas.  
- **Palavras-chave** → sempre em minúsculas (`module`, `input`, `output`, etc.).  
- **Espaços em branco** → não são interpretados.  
- **Fim de instruções** → sempre com `;` (ponto e vírgula).  
- **Comentários**:  
  - `// comentário em uma linha`  
  - `/* comentário em múltiplas linhas */`  

---

## 🔹 Exemplo: Meio Somador (Half Adder)

```verilog
module halfadder (a, b, s, cout);
    input a, b;       // Entradas
    output s, cout;   // Saídas
endmodule
```

---

## 🔹 Tipos de Portas

- `input`  → entrada  
- `output` → saída  
- `inout`  → bidirecional  

### Porta simples (1 bit)
```verilog
input a, b;
output s, cout;
```

### Porta de múltiplos bits (barramento)
```verilog
input [3:0] a, b;   // 4 bits cada
output [3:0] s;     // 4 bits
output cout;        // 1 bit
```

📌 *MSB (Most Significant Bit)* → bit mais significativo  
📌 *LSB (Least Significant Bit)* → bit menos significativo  

---

## 🔹 Parâmetros (Constants)

Permitem definir constantes reutilizáveis dentro do módulo.

```verilog

module adder (a, b, cin, s, cout);
    parameter largura = 4;
    input [largura-1:0] a, b;
    input cin;
    output [largura-1:0] s;
    output cout;
endmodule
```

Vantagens:
- Torna o código mais **legível**.  
- Facilita a **atualização** (mudar apenas o parâmetro altera todo o módulo).  

---

## 🔹 Dados Intermediários

São variáveis internas ao módulo, não ligadas diretamente às portas.  
Existem dois tipos principais:

### 1. **Wire (conexão física)**
- Representa uma ligação simples (como um fio real).  
- Não armazena valor.  
- Exemplo:  
  ```verilog
  wire [7:0] soma;
  ```

Tipos de wire:  
- `wire` → conexão simples  
- `tri` → conexão tri-state (pode ser “desconectado”)  
- `supply0` → constante nível lógico 0  
- `supply1` → constante nível lógico 1  

---

### 2. **Reg (registrador)**
- Armazena valor temporário.  
- Usado em atribuições dentro de blocos `always`.  
- Exemplos:  
  ```verilog
  reg [7:0] resultado;
  integer count;
  ```

Tipos:  
- `reg` → valor sem sinal  
- `reg signed` → valor com sinal  
- `integer` → inteiro com sinal de 32 bits  
- `real`, `time`, `realtime` → usados apenas em simulação (não sintetizáveis)  

📌 **Sintetizável** = pode ser transformado em hardware real pela ferramenta de síntese.  
📌 Tipos como `real` ou `time` só funcionam em simulação → não viram hardware.  

---

## 🔹 Tabela de uso de variáveis

| Tipo   | Entrada | Saída | Inout |
|--------|---------|-------|-------|
| `reg`  | ❌      | ✅    | ❌    |
| `wire` | ✅      | ✅    | ✅    |

---

## 🔹 Abordagens de Descrição de Circuitos em Verilog

- **Estrutural** → descreve portas e conexões explicitamente.  
- **Fluxo de dados (RTL)** → descreve relações entre sinais (ex.: `assign`).  
- **Hierárquica** → organiza o projeto em submódulos.  
- **Comportamental** → descreve o funcionamento usando construções como `if`, `case`, `always`.  

---

### 🏁 Conclusão
O **Verilog** permite descrever hardware em diferentes níveis de abstração:  
- Desde a conexão de portas até o comportamento completo de um sistema digital.  
- O entendimento da estrutura `module ... endmodule` é o **primeiro passo** para escrever circuitos em HDL.
