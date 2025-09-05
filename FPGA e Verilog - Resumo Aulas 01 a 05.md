# 📚 FPGA e Verilog – Resumo das Aulas 01 a 05  

**📅 Data:** 05/09/2025  

---

## 🔎 Panorama Geral
As cinco primeiras aulas do curso apresentaram as principais formas de implementação de circuitos digitais, desde os **CIs de lógica padrão** até os **PLDs**, passando por **Full-Custom** e **ASIC**.  
Esse bloco inicial mostra a evolução histórica e tecnológica dos dispositivos, destacando vantagens, desvantagens e aplicações de cada abordagem.  

---

## 📖 Aula 01 – Introdução ao Curso
- **Tema:** Verilog e FPGA.  
- Pré-requisito: **Sistemas Digitais / Eletrônica Digital II**.  
- Foco do curso: **dispositivos lógico-programáveis** com a linguagem **Verilog**.  
- Conceitos aplicáveis a outras linguagens de descrição de hardware.  

---

## 📖 Aula 02 – Circuitos Integrados de Lógica Padrão
- Funcionamento de **CIs físicos** de lógica padrão.  
- Desvantagens em relação a FPGAs:
  - Pouca flexibilidade.  
  - Consumo de energia por portas não utilizadas.  
  - Maior espaço físico.  
- Relação com experiências práticas (Máquina de café, jogo de ação).  

---

## 📖 Aula 03 – Full-Custom IC
- Projeto **totalmente customizado** a nível de transistor.  
- **Conceitos principais:**
  - Alocação e tamanho dos transistores (litografia).  
  - Roteamento interno.  
- **Vantagens:** alto desempenho, tamanho reduzido, baixo consumo.  
- **Desvantagens:** alto custo, processo demorado e sujeito a erros.  

---

## 📖 Aula 04 – ASIC (Application Specific Integrated Circuit)
- Circuito integrado **para uma aplicação específica**.  
- Diferença do CI padrão: interligações são **internas ao chip**.  
- **Vantagens:** equilíbrio entre custo, desempenho e consumo.  
- **Desvantagens:** exige fábrica, custo ainda elevado, limitado para pequenas empresas.  

---

## 📖 Aula 05 – PLD (Programmable Logic Device)
- Circuito integrado **programável pelo usuário**.  
- Estrutura com blocos lógicos prontos (portas, somadores, etc.).  
- Conexões internas podem ser **refeitas** → permite correções e novas funcionalidades.  
- **Vantagens:** baixo custo de projeto, rapidez de desenvolvimento, ideal para prototipagem.  
- **Desvantagens:** maior tamanho físico, maior consumo de energia, desempenho inferior ao ASIC.  
- Muito usado para **protótipos** que depois dão origem a um ASIC definitivo.  

---

## 📝 Breve descrição de cada tecnologia

- **CI Padrão (Standard Logic IC):** chip com portas lógicas fixas; barato e rápido de usar, mas inflexível.  
- **Full-Custom IC:** projetado transistor por transistor; máximo desempenho e mínimo consumo, mas caro e demorado.  
- **ASIC:** circuito integrado feito sob medida para uma aplicação; mais acessível que full-custom, porém ainda exige fábrica.  
- **PLD:** dispositivo programável pelo usuário; permite modificações rápidas e baixo custo de desenvolvimento, mas consome mais energia e ocupa mais espaço.  

---

## 📊 Comparativo Resumido
| Tecnologia        | Flexibilidade | Custo Projeto | Custo Unitário | Consumo | Desempenho | Tempo p/ Mercado |
|-------------------|--------------|---------------|----------------|---------|------------|-----------------|
| **CI Padrão**     | Nenhuma      | Baixo         | Médio          | Médio   | Médio      | Rápido          |
| **Full-Custom**   | Nenhuma      | Muito alto    | Muito baixo    | Muito baixo | Muito alto | Muito lento     |
| **ASIC**          | Nenhuma      | Alto          | Baixo          | Baixo   | Alto       | Médio-lento     |
| **PLD**           | Alta         | Baixo         | Alto           | Alto    | Médio      | Rápido          |

---

✅ Esse resumo fecha o **primeiro bloco** do curso: formas de implementar circuitos digitais.  
A partir da próxima aula, a tendência é mergulhar mais em **FPGA e Verilog na prática**.
