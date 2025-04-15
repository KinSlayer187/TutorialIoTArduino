# Tutorial Básico de IoT com Arduino IDE

## 📡 Introdução à Internet das Coisas (IoT)

A **Internet das Coisas (IoT)** é um conceito que descreve a conexão de objetos físicos à internet para coletar e trocar dados. Exemplos comuns incluem sensores ambientais, automação residencial, wearables, entre outros.

Com IoT, é possível criar sistemas inteligentes que respondem ao ambiente e interagem com o usuário de forma remota, segura e eficiente.

---

## 🛠️ O que é o Arduino IDE?

O **Arduino IDE (Integrated Development Environment)** é uma plataforma de código aberto usada para programar placas Arduino e microcontroladores compatíveis (como ESP8266 e ESP32). Ela oferece uma interface simples para escrever, compilar e enviar códigos para os dispositivos.

---

## 🧰 Instalação do Arduino IDE

### 💻 Windows

1. Acesse o site oficial: [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
2. Baixe o instalador para Windows.
3. Execute o instalador e siga as instruções (recomenda-se instalar todos os drivers).
4. Após a instalação, abra o Arduino IDE pelo menu Iniciar.

### 🐧 Linux (via Flatpak)

> Método recomendado por ser compatível com diversas distribuições Linux.

#### 1. Instale o Flatpak (caso ainda não tenha):

```bash
# Debian/Ubuntu (GNOME)
sudo apt install flatpak gnome-software-plugin-flatpak

# Debian/Ubuntu (KDE Plasma)
sudo apt install flatpak plasma-discover-backend-flatpak

# Arch Linux/Manjaro
sudo pacman -S flatpak
```

Acesse [https://flathub.org/](https://flathub.org/) para instalar os pacotes desejados.

```bash
flatpak install nome_do_pacote
```

#### 2. Configuração da Placa e Porta

- Vá em **Ferramentas > Placa** e selecione a placa correta (ex: *Arduino UNO*).
- Vá em **Ferramentas > Porta** e selecione a porta serial correspondente (ex: *COM3*, */dev/ttyUSB0*).

#### 3. (Opcional) Instalando ESP8266/ESP32

Se você for usar placas como ESP8266 ou ESP32:

- Vá em **Arquivo > Preferências** ou clique em `CTRL + ,`
- No campo "URLs Adicionais para Gerenciadores de Placas", adicione:

```
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
https://arduino.esp8266.com/stable/package_esp8266com_index.json
```

#### 4. Permissão de acesso à porta serial no Linux

1. Adicione seu usuário ao grupo dialout:
```bash
sudo usermod -aG dialout $USER
```
   (Se não funcionar, tente: `sudo usermod -a -G dialout $USER`)
   - Reinicie ou faça logout/login

2. Permissão permanente via udev (opcional):
```bash
sudo nano /etc/udev/rules.d/99-arduino.rules
```

Adicione:
```
KERNEL=="ttyACM0[0-9]*", MODE="0666"
KERNEL=="ttyUSB0[0-9]*", MODE="0666"
```

Salve e atualize as regras:
```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

#### 5. Como fazer upload do código

1. Conecte a placa Arduino no computador.
2. Abra o Arduino IDE.
3. Selecione a placa correta em Ferramentas > Placa.
4. Escolha a porta em Ferramentas > Porta.
5. Escreva ou abra um código.
6. Clique no botão Upload (ícone de seta) ou pressione `Ctrl + U`.

#### 6. Dicas Finais

- Verifique se a porta está selecionada sempre que reconectar a placa.
- O uso do Flatpak pode exigir permissões extras para aceitar dispositivos USB.
- Use cabos USB de dados, não apenas de carregamento.
- Se houver problema com permissões, revise o item 4.
- Instale o `tldr` para ver exemplos de comandos do Flatpak.

---

## 🔧 Parte Avançada: Tutorial de IoT com Arduino IDE

### 1. 📦 Gerenciando Bibliotecas Adicionais

- Instale bibliotecas pelo menu **Sketch > Incluir Biblioteca > Gerenciar Bibliotecas**.
- Ou adicione manualmente em `Documentos/Arduino/libraries/`
- Exemplos úteis: `PubSubClient`, `Adafruit Unified Sensor`, `DHT sensor library`

### 2. 🌐 Conectando o ESP8266/ESP32 à Internet

```cpp
#include <WiFi.h>

const char* ssid = "SEU_SSID";
const char* password = "SUA_SENHA";

void setup() {
  Serial.begin(115200);
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("Conectado!");
}
```

### 3. 📤 Enviando dados via MQTT

- Use a biblioteca `PubSubClient`
- Teste com `broker.hivemq.com` ou Mosquitto local
- Integração com sensores e tópicos MQTT

### 4. 🔐 Segurança no IoT

- Armazenar senhas com cuidado (EEPROM ou arquivos `.h` ocultos)
- Use `WiFiClientSecure` para conexões HTTPS (ESP32)
- Nunca exponha credenciais em repositórios públicos

### 5. 📈 Dashboards e Monitoramento

- Use plataformas como:
  - [ThingSpeak](https://thingspeak.com)
  - [Node-RED](https://nodered.org)
  - Grafana com InfluxDB
  - Blynk (mobile)

### 6. 🔁 Atualização OTA (Over-The-Air)

- Atualize o firmware sem precisar de cabo USB
- Requer primeira instalação via cabo
- Use `ArduinoOTA` ou `HTTPUpdateServer`

### 7. 🧪 Testes e Depuração

- Utilize `Serial Monitor` e `Serial Plotter`
- Funções úteis: `Serial.println()`, `millis()`, `delay()`
- Debug remoto via UDP (avançado)

### 8. 🧱 Projeto Estruturado

- Separe em `.ino`, `.h`, `.cpp`
- Modularize sensores, comunicação, lógica
- Use arquivos `config.h` para credenciais e pinos

### 9. 📂 Versionamento com Git

```bash
git init
git add .
git commit -m "primeiro commit"
git remote add origin <URL_DO_REPO>
git push -u origin main
```

Crie um `.gitignore` para ignorar arquivos desnecessários (ex: `.vscode/`, `.DS_Store`)

### 10. ⚙️ Integração com VS Code + PlatformIO

- Benefícios: IntelliSense, build rápido, modularização
- Instale a extensão PlatformIO
- Crie projetos com estrutura avançada

---

Fique à vontade para adaptar essa estrutura conforme seu projeto. Se quiser posso criar links para esses tópicos no índice ou separar em arquivos diferentes!

