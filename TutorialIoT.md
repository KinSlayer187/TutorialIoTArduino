# Tutorial Básico de IoT com Arduino IDE

## 📡 Introdução à Internet das Coisas (IoT)

A **Internet das Coisas (IoT)** é um conceito que descreve a conexão de objetos físicos à internet para coletar e trocar dados. Exemplos comuns incluem sensores ambientais, automação residencial, wearables, entre outros.

Com IoT, é possível criar sistemas inteligentes que respondem ao ambiente e interagem com o usuário de forma remota, segura e eficiente.

---

## 🛠️ O que é o Arduino IDE?

O **Arduino IDE (Integrated Development Environment)** é uma plataforma de código aberto usada para programar placas Arduino e microcontroladores compatíveis (como ESP8266 e ESP32). Ela oferece uma interface simples para escrever, compilar e enviar códigos para os dispositivos.

Você pode baixar o Arduino IDE aqui:  
🔗 https://www.arduino.cc/en/software

---

## ⚙️ Requisitos Básicos

- Placa Arduino (UNO, Nano, etc.) ou microcontrolador como ESP8266/ESP32
- Cabo USB para conexão
- Sensor ou componente (como LED, resistor, sensor DHT22, etc.)
- Arduino IDE instalado no computador
- Drivers da placa instalados (CH340 ou CP2102, dependendo da placa)

---

## 🔌 Instalando e Configurando a Arduino IDE

### 1. Instalação
- Faça o download do Arduino IDE para seu sistema operacional.
- Siga as instruções de instalação.

### 2. Configuração da Placa e Porta
- Vá em **Ferramentas > Placa** e selecione a placa correta (ex: *Arduino UNO*).
- Vá em **Ferramentas > Porta** e selecione a porta serial correspondente (ex: *COM3*, */dev/ttyUSB0*).

### 3. (Opcional) Instalando ESP8266/ESP32
Se você for usar placas como ESP8266 ou ESP32:
- Vá em **Arquivo > Preferências**
- No campo "URLs Adicionais para Gerenciadores de Placas", adicione:
- https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
- https://arduino.esp8266.com/stable/package_esp8266com_index.json
- Depois, vá em **Ferramentas > Placa > Gerenciador de Placas**, procure e instale:
- *ESP by Espressif Systems*
- *ESP by ESP Community*
- Ou clique em CTRL + , e adicione os links, colocando vírgula entre eles

## 🧰 Instalação do Arduino IDE

### 💻 Windows

1. Acesse o site oficial: [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
2. Baixe o instalador para Windows.
3. Execute o instalador e siga as instruções (recomenda-se instalar todos os drivers).
4. Após a instalação, abra o Arduino IDE pelo menu Iniciar.

### 🐧 Linux (via Flatpak)

> Método recomendado por ser compatível com diversas distribuições Linux.

1. Instale o Flatpak (caso ainda não tenha):
   ```bash
   sudo apt install flatpak           # Debian/Ubuntu
   sudo pacman -S flatpak             # Arch/Manjaro
   No Fedora, o flatpak já é nativo
   ```
2. Instalar os plugins:
    ```bash
        sudo apt install gnome-software-plugin-flatpak  #Ubuntu/Debian (GNOME)
        sudo apt install plasma-discover-backend-flatpak #Debian (KDE Plasma)
    ```
3. Adicionar o repositório (Opcional):
    ```bash
        sudo apt install plasma-discover-backend-flatpak
    ```
4. Instale o Arduino IDE:
    ```bash
        flatpak install flathub cc.arduino.arduinoide
    ```
