# 📚 FPGA e Verilog – Aula 06  
## Dispositivos Lógicos Programáveis Simples (SPLD)  

**📅 Data:** 06/09/2025  
**📚 Tema:** SPLDs – Estrutura e Funcionamento  

---

### 📖 Resumo da Aula
Nesta aula foi discutido como os **dispositivos lógicos programáveis (PLDs)** podem ser construídos, com foco nos **SPLDs (Simple Programmable Logic Devices)**.  

Os PLDs são classificados em três categorias principais:  
- **SPLDs** – *Simple Programmable Logic Devices*  
- **CPLDs** – *Complex Programmable Logic Devices*  
- **FPGAs** – *Field-Programmable Gate Arrays*  

---

### 🔎 Breve explicação de cada um
- **SPLD:** dispositivos simples, como **PAL**, **PLA** e **GAL**, usados para implementar funções lógicas básicas.  
- **CPLD:** conjunto de vários SPLDs interligados; permite implementar circuitos mais complexos mantendo previsibilidade de desempenho.  
- **FPGA:** arranjo massivo de blocos lógicos e flip-flops, altamente flexível, ideal para projetos complexos e aplicações modernas.  

---

### 💡 Ideia Básica dos SPLDs
- Estrutura formada por portas **AND** e **OR** com entradas configuráveis.  
- Toda função lógica pode ser implementada nesse arranjo, queimando fusíveis ou programando células de memória.  
- Os **transistores programáveis** funcionam como chaves:
  - **Sinal alto:** chave fechada (conexão ativa).  
  - **Sinal baixo:** chave aberta (sem conexão).  
- Os valores de programação são armazenados em **memória** ou definidos por **fusíveis**.  

---

### 📌 Diferença entre memória e fusíveis
- **Baseado em memória (RAM/EEPROM):**
  - Reprogramável.  
  - Permite correções e alterações no projeto.  
  - Pode sofrer influência de **ruídos** ou até radiação (exemplo: em satélites).  

- **Baseado em fusíveis (OTP – One Time Programmable):**
  - Programado apenas **uma vez**.  
  - Não sofre alteração por ruídos.  
  - Usado quando é necessária maior confiabilidade (ex.: aplicações aeroespaciais).  

---

### ✅ Classificação dos SPLDs

#### 1. **PAL (Programmable Array Logic)**  
- Primeiro tipo de SPLD.  
- Estrutura: arranjo **AND programável** + arranjo **OR fixo**.  
- Apenas as entradas das portas AND podem ser configuradas (com fusíveis).  
- Exemplo de implementação:  
  - Função lógica **F = ab'c + a'bc** → queima de fusíveis define quais variáveis entram negadas ou não.  
- Só permite **lógica combinacional** (não há elementos de memória).  

---

#### 2. **PLA (Programmable Logic Array)**  
- Estrutura: arranjo **AND programável** + arranjo **OR programável**.  
- Mais flexível que o PAL, pois permite definir entradas de ambas as portas.  
- Implementa lógica **combinacional**.  

---

#### 3. **GAL (Generic Array Logic)**  
- Evolução dos PALs, com suporte a **reprogramação**.  
- Estrutura: arranjo **AND programável** + arranjo **OR programável**.  
- Inclui **OLMCs (Output Logic Macrocell)**, que permitem implementar:  
  - **Lógica combinacional**  
  - **Lógica sequencial** (com flip-flops integrados).  
- Compatível com projetos feitos para PALs.  
- Família famosa: **Lattice GAL**, como o **GAL18V10** (18 entradas, 10 saídas).  

---

### 🔄 Introdução: Lógica Combinacional x Sequencial
- **Lógica Combinacional:**  
  - Saída depende apenas das **entradas atuais**.  
  - Exemplos: somadores, multiplexadores, decodificadores.  

- **Lógica Sequencial:**  
  - Saída depende das **entradas atuais + estado anterior (memória)**.  
  - Exemplos: flip-flops, registradores, contadores, máquinas de estado.  

---

### 📌 Observação
Os **SPLDs** são fundamentais porque servem como base para entender os **CPLDs**, que serão tratados na próxima aula.  

---
