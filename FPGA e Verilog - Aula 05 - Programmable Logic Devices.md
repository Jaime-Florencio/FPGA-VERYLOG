# 📚 FPGA e Verilog – Aula 05  
## Programmable Logic Devices (PLD)  

**📅 Data:** 05/09/2025  
**📚 Tema:** Última técnica de implementação de circuitos digitais – PLD  

---

### 📖 Resumo da Aula
O **PLD (Programmable Logic Device)** é um circuito integrado que já possui **vários blocos lógicos prontos** (portas lógicas, somadores, funções lógicas, etc.).  
A programação de um PLD consiste em **criar ou destruir conexões internas** de acordo com a lógica desejada.  

Para trabalhar com PLDs é necessário:  
- **Hardware (o próprio PLD);**  
- **Ambiente de desenvolvimento do fabricante**, que fornece ferramentas para escrever e sintetizar os circuitos digitais.  

Dessa forma, os PLDs permitem implementar circuitos digitais sem precisar passar por uma fábrica de ASICs.  

---

### 🔎 Conceitos Importantes
- Estrutura semelhante a um CI, mas com **conexões internas programáveis** pelo usuário.  
- Diferença para ASIC:  
  - **PLD:** conexões podem ser refeitas → permite modificar o hardware após a programação.  
  - **ASIC:** conexões são fixas e feitas em fábrica → após pronto, não pode ser alterado.  
- Existem **PLDs simples e complexos**, que se diferenciam pela quantidade de funções já integradas.  
- PLDs são muito utilizados em **protótipos e testes**, e muitas empresas projetam em PLD antes de enviar para fabricar um **ASIC definitivo**.  

---

### ✅ Vantagens do PLD
- **Baixo custo de projeto** → reutilização em diferentes implementações.  
- **Rápido desenvolvimento** → ferramentas de software permitem síntese e testes ágeis.  
- **Flexibilidade** → conexões podem ser refeitas para corrigir erros ou adicionar novas funcionalidades.  
- **Ideal para prototipagem** antes da fabricação de um ASIC.  

---

### ⚠️ Desvantagens do PLD
- **Maior tamanho físico** em comparação a ASICs.  
- **Custo unitário mais alto** → embora o projeto seja mais barato, a produção em larga escala é menos vantajosa que um ASIC.  
- **Alto consumo de energia** → por incluir várias funcionalidades integradas.  
- **Desempenho inferior** ao ASIC → embora a tecnologia venha melhorando ao longo dos anos.  

---

### 📌 Observação
- PLDs são normalmente usados para **protótipos funcionais**.  
- Quando o projeto está validado no PLD, pode ser enviado para fabricação de um **ASIC**, visando maior desempenho e menor consumo.  

---

### ❓ Qual escolher: ASIC ou PLD?
Depende do objetivo:  
- **Disponibilidade rápida e baixo custo inicial** → PLD é a melhor escolha.  
- **Alta performance, menor consumo de energia e otimização máxima** → ASIC é mais indicado (embora mais caro e demorado).  
