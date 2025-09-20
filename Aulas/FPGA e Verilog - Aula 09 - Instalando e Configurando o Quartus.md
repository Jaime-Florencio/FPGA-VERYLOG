# Seu Primeiro Ambiente de Desenvolvimento FPGA: Um Guia Amigável Passo a Passo

## Introdução: Bem-vindo ao Mundo dos FPGAs!
Olá e seja bem-vindo!  
Se você sempre teve curiosidade em criar seus próprios circuitos digitais personalizados, está no lugar certo.  
Este tutorial foi pensado para guiar **um iniciante absoluto** em todo o processo de configuração de hardware e software para o **primeiro projeto em FPGA**.  

Vamos desmistificar cada etapa, desde a conexão dos cabos até a instalação do software, garantindo uma base sólida para começar sua jornada.

---

## Parte 1: Conhecendo seu Hardware

Antes de programar qualquer coisa, precisamos entender as ferramentas físicas que vamos usar: a **placa de desenvolvimento** e o **programador** que a conecta ao computador.

### 1.1 O Cérebro: Placa de Desenvolvimento FPGA
O coração da nossa configuração é um kit baseado no **Altera Cyclone IV FPGA**.  
Essa placa é mais que um chip, é uma plataforma de aprendizado com diversos recursos:

- **Chaves & Botões (Switches/Push-Buttons):** ideais para entradas simples.  
- **Displays de 7 segmentos:** exibem números e letras sem precisar de monitor.  
- **LEDs:** a forma mais simples de saída, dão feedback imediato.  
- **Clock On-board:** já vem com gerador de clock integrado.  
- **Header Pins:** acesso direto aos pinos de I/O do FPGA.  
- **Conectores externos (VGA, PS/2, USB):** habilitam projetos mais avançados.

> 💡 FPGAs da Altera são recomendados para iniciantes por serem acessíveis e fáceis de encontrar.

### 1.2 O Elo: Programador USB Blaster
O **USB Blaster** é a ponte entre o computador e o FPGA.  
Ele transfere o arquivo compilado do PC para a memória do FPGA, efetivamente “programando-o”.

O kit geralmente vem com:
- 1 cabo JTAG flat  
- 1 cabo USB padrão (tipo impressora)

### 1.3 Conectando Tudo
Siga a sequência abaixo:

1. **JTAG → Programador**: conecte o cabo flat.  
2. **JTAG → Placa**: outra ponta no conector JTAG da placa.  
3. **USB → Programador**: conecte o cabo USB.  
4. **USB → PC**: plugue no computador.  
5. **Fonte 5V → Placa**: conecte e ligue na tomada.  

> ⚠️ Importante: a USB serve **somente para programação**. A placa requer **fonte 5V separada**.

---

## Parte 2: Instalando o Software

O principal software será o **Intel Quartus Prime Lite** (antigo Altera).

### 2.1 Baixando o Quartus Prime Lite
1. Acesse: [fpga.software.intel.com](https://fpga.software.intel.com)  
2. Escolha a edição **Lite**  
3. Escolha a versão **20.1**  
4. Baixe o instalador para Windows: `Quartus-lite-20.1.0.711-windows.tar`  
5. Crie/login em uma conta Intel (registro gratuito).  

> 📦 O arquivo é grande (~1.6 GB), pode demorar o download.

### 2.2 Instalando o Quartus
1. Extraia o `.tar` com **7-Zip** ou **WinRAR**.  
2. Abra a pasta extraída.  
3. Execute o `setup.bat`.  
4. Clique em **Next** até concluir (configurações padrão).  

### 2.3 Configuração Inicial: ModelSim
1. Abra o **Quartus Prime Lite**.  
2. Vá em **Tools → Options**.  
3. Clique em **EDA Tool Options**.  
4. Localize o campo vazio ao lado de **ModelSim-Altera**.  
5. Insira o caminho da instalação do ModelSim.  
6. Clique em **OK**.  

---

## Parte 3: Instalando o Driver

O Windows não reconhece automaticamente o USB Blaster.  
Será necessário instalar o driver manualmente.

### 3.1 Instalando o Driver USB Blaster
1. Plugue o USB Blaster no PC.  
2. Abra o **Gerenciador de Dispositivos**.  
3. Em “Outros Dispositivos”, localize **USB-Blaster** (com ícone amarelo).  
4. Clique direito → **Atualizar driver**.  
5. Escolha **Procurar drivers no computador**.  
6. Vá até:  
   `C:\intelFPGA_lite\20.1\quartus\drivers\usb-blaster`  
7. Marque **Incluir subpastas** → **Avançar**.  
8. Aguarde a instalação.  

### 3.2 Verificando a Conexão
1. No Quartus, vá em **Tools → Programmer**.  
2. Clique em **Hardware Setup...**.  
3. Procure na lista se aparece **USB-Blaster**.  

> ❌ Se não aparecer, repita a instalação. Alguns programadores paralelos podem apresentar falhas.

---

## Conclusão: Você Está Pronto!
🎉 Parabéns!  
Agora você tem todo o ambiente configurado — **hardware, software e drivers**.  

Seu PC já se comunica com a placa FPGA, e o ambiente está pronto para seu **primeiro projeto**.  
O próximo passo é aprender uma linguagem de descrição de hardware (**HDL**), como **Verilog**.

👉 Seu caminho para o mundo da lógica digital personalizada está aberto.  
Boa codificação e bons estudos! 🚀
