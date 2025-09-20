# 📚 FPGA e Verilog – Aula 09  
## Instalando e Configurando o Quartus II 13.1 Web Edition  

**📅 Data:** 20/09/2025  
**📚 Tema:** Ambiente de Desenvolvimento FPGA – Quartus II + ModelSim  

---

### 📖 Resumo da Aula
Nesta aula, foi apresentado o processo de instalação do **Quartus II 13.1 Web Edition** e do **ModelSim-Altera Starter Edition**, preparando o ambiente de desenvolvimento para aprender Verilog e realizar simulações, mesmo sem possuir uma placa FPGA física.  

---

## Parte 1: Instalando o Quartus II

1. Rode o instalador **`QuartusSetupWeb-13.1.0.162.exe`**.  
2. Aceite a licença e escolha a pasta de instalação (padrão recomendado).  
3. Marque os seguintes componentes:  
   - ✅ Quartus II Software  
   - ✅ Suporte 64 bits  
   - ✅ ModelSim-Altera Starter Edition (Free)  
   - ❌ Não selecionar ModelSim pago  
4. Clique em **Next** até concluir a instalação.  

---

## Parte 2: Aplicando o Patch

1. Após a instalação, rode o arquivo **`QuartusPatchSetup-13.1.4.182.exe`**.  
2. Esse patch atualiza o Quartus II para o **Update 4**, corrigindo falhas e aumentando a estabilidade.  

---

## Parte 3: Suporte a Dispositivos (opcional)

- O Quartus II pode pedir para instalar suporte a FPGAs (*devices*).  
- Isso não é necessário para **simulação**, mas se quiser compilar projetos completos pode instalar o **Cyclone IV** que já está na pasta:  
  1. Abra o **Device Installer** pelo Menu Iniciar do Windows.  
  2. Aponte para o arquivo **`cyclone-13.1.0.162.qdz`**.  
  3. Conclua a instalação.  

---

## Parte 4: Configurando o ModelSim

1. Abra o **Quartus II 13.1**.  
2. Vá em **Tools → Options → EDA Tool Options**.  
3. Em **ModelSim-Altera**, coloque o caminho da instalação, por exemplo:  

C:\altera\13.1\modelsim_ase\win32aloem

4. Clique em **OK**.  

---

## Conclusão: Ambiente Pronto 🎉
Agora você já tem o **Quartus II + ModelSim** funcionando no seu PC:  

- Pode escrever códigos em **Verilog**.  
- Compilar (se instalar devices).  
- E, principalmente, **simular no ModelSim** sem precisar de uma placa FPGA física.  

👉 O próximo passo é criar o **primeiro projeto em Verilog** (exemplo: porta lógica AND) e rodar a simulação para validar a instalação. 🚀

---

## 📂 Arquivos e Links Utilizados

Nesta aula utilizei os seguintes arquivos de instalação (mantidos localmente, não incluídos no repositório devido ao tamanho):

- `QuartusSetupWeb-13.1.0.162.exe` → Instalador principal do Quartus II 13.1 Web Edition  
- `QuartusPatchSetup-13.1.4.182.exe` → Patch para Update 4  
- `ModelSimSetup-13.1.0.162.exe` → Instalador do ModelSim-Altera Starter Edition  
- `cyclone-13.1.0.162.qdz` → Arquivo de suporte para dispositivos Cyclone  
- `DE0_Default.qsf` → Projeto de exemplo  

📌 Para quem deseja baixar os instaladores oficiais e atuais, seguem os links diretos da Intel:

- [Quartus Prime Lite Edition – Downloads](https://www.intel.com/content/www/us/en/software/programmable/quartus-prime/download.html)  
- [ModelSim-Intel FPGA Starter Edition](https://www.intel.com/content/www/us/en/software/programmable/quartus-prime/model-sim.html)  


