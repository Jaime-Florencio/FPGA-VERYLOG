# FPGA e Verilog – Aula 08  
## Arranjo de Portas Programáveis em Campo (FPGA)

📅 Data: 20/09/2025  
📚 Tema: Estrutura e funcionamento dos FPGAs  

---

## Introdução
Os **FPGAs (Field Programmable Gate Arrays)** são semelhantes aos CPLDs, porém incorporam um grau de complexidade muito maior.  
São dispositivos lógico-programáveis mais avançados, com muito mais recursos e funções.

---

## Estrutura Geral do FPGA
![Estrutura geral de um FPGA](./Aulas/Imagens/fpga-estrutura-geral.png)

Um FPGA é composto por:  
- **Logic Blocks (LAB/LE):** agrupamento de elementos lógicos.  
- **Interconnect (Matriz de chaveamento):** conecta os blocos lógicos entre si.  
- **I/O Blocks:** agrupam os pinos de entrada e saída.  
- **Embedded Array Block (EAB):** bloco de memória interna (opcional, depende do modelo).  

---

## FPGA vs CPLD
- **Entradas dos blocos lógicos**  
  - FPGA: tipicamente 3 a 5 entradas por bloco lógico.  
  - CPLD: funções lógicas implementadas por **soma de produtos**.  
  - FPGA: funções lógicas implementadas por **Lookup Tables (LUTs)**.  

- **Complexidade**  
  - FPGA: milhares a milhões de portas lógicas.  
  - CPLD: menor escala, voltado para média complexidade.  

- **Memória**  
  - FPGA: pode ter blocos de memória interna (RAM/EAB), geralmente reconfiguráveis.  
  - CPLD: normalmente não possui memória interna.  

- **Atrasos (delays)**  
  - CPLD: mais previsíveis.  
  - FPGA: mais difíceis de prever devido à interconexão mais complexa.  

- **Volatilidade**  
  - FPGA: **voláteis** (precisam ser reconfigurados a cada inicialização).  
  - CPLD: **não-voláteis** (mantêm a configuração mesmo desligados).  

---

## Lookup Table (LUT)
As LUTs são o coração da implementação lógica nos FPGAs.  
Basicamente, são **tabelas verdade armazenadas em memória**.

Exemplo: implementar a função **F = x'y' + xy**

Tabela-verdade:  
| x | y | F |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

Implementação com LUT:  
![Exemplo de LUT](./Aulas/Imagens/fpga-lut.png)

Cada combinação de entrada (x,y) corresponde a um endereço na memória.  
A saída da LUT é o valor da função **F**.

---

## Elemento Lógico (LE)
O **Logic Element (LE)** combina:  
- **LUT:** gera lógica **combinacional**.  
- **Flip-Flop (FF):** permite armazenar estado, criando lógica **sequencial**.  
- Controle via memória **SRAM** para configurar o comportamento.  

![Elemento Lógico: LUT + FF](./Aulas/Imagens/fpga-le.png)

📌 Diferença importante:  
- **LUT sozinho → lógica combinacional (depende só das entradas).**  
- **LE (LUT + FF) → lógica sequencial (pode guardar estados no tempo).**

---

## Embedded Array Block (EAB)
Os FPGAs podem incluir blocos de memória interna chamados **EABs**.  
Eles permitem:  
- Criar **RAM interna**.  
- Implementar funções mais complexas como **filtros digitais** ou **buffers de dados**.  

🔎 O EAB pode ser visto como uma "LUT muito maior", porque também funciona como uma tabela de consulta, mas em escala expandida.

---

## Resumo
- FPGAs são mais complexos e versáteis que CPLDs.  
- Implementam lógica via **LUTs** em vez de soma de produtos.  
- Elementos Lógicos (LE = LUT + FF) permitem tanto lógica combinacional quanto sequencial.  
- Podem ter blocos de memória interna (EAB).  
- São **voláteis**, exigindo configuração a cada inicialização.

---
