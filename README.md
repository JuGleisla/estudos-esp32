# Meus Primeiros Passos com ESP32 🚀
Este repositório documenta meu aprendizado inicial com a placa de desenvolvimento ESP32 usando a Arduino IDE.

## 🛠️ Hardware e Software
* **Placa:** ESP32 (ESP32-WROOM-DA Module)
* **IDE:** Arduino IDE 2.0+
* **Drivers:** Instalei o driver correto para o chip USB (CP2102, versão 32 bites).
  > **Observação:** Site utilizado para baixar o drive "https://www.robocore.net/tutoriais/instalando-driver-do-nodemcu?gad_source=1&gad_campaignid=16509321328&gbraid=0AAAAADzrkI7ELsb6bBCyny25qu9FuDS1M&gclid=CjwKCAiA3fnJBhAgEiwAyqmY5cPO3QxVMGHPJBs3A7I1_YavxZjOa59Oz_AYaLInMrW3zlLGJk2xGBoCBp4QAvD_BwE"

## 1. Configuração Inicial
Para o computador reconhecer a placa:
1.  Conectei o ESP32 via cabo USB de dados no computador.
2.  Verifiquei no **Gerenciador de Dispositivos** se a porta COM apareceu.
> **Observação:** A porta foi reconhecida pelo computador após a instalação do "https://dl.espressif.com/dl/package_esp32_index.json" e o fechamento da IDE. 
3.  Na Arduino IDE, selecionei a placa **ESP32-WROOM-DA Module** e a porta **COM4** (no meu caso).

> **Dica:** Se der erro ao carregar, segure o botão **BOOT** na placa quando aparecer "Connecting..." na IDE.

## 2. Projeto: Acender Led 💡
O primeiro teste foi fazer o LED do próprio ESP (pino 2) acender e se manter acesso.

```cpp
int pinoLed = 2; // Pino do LED interno

void setup() {
  pinMode(pinoLed, OUTPUT);
  digitalWrite(pinoLed, HIGH);  // Acende
  delay(1000);                  // Espera 1s 
}

void loop() {
// Não precisa fazer nada aqui, o LED já está ligado!           
}
```

## 3. Projeto: Hello World (Blink) 💡
O segundo teste foi fazer o LED do próprio ESP (pino 2) piscar (consulte o datasheet).

```cpp
int pinoLed = 2; // Pino do LED interno

void setup() {
  pinMode(pinoLed, OUTPUT);
}

void loop() {
  digitalWrite(pinoLed, HIGH);  // Acende
  delay(1000);                  // Espera 1s
  digitalWrite(pinoLed, LOW);   // Apaga
  delay(1000);                  // Espera 1s
}
```

## 4. Projeto: Comunicação com monitor serial
O terceiro teste foi fazer o LED do próprio ESP (pino 2) piscar e informar seu estado por meio do monitor serial.

```cpp
int pinoLed = 2;

void setup() {

  pinMode (pinoLed, OUTPUT); // Definição de saída do Led
  Serial.begin(115200); // Inicializar comunicação serial com velocidade de 115200 bits por segundo
  Serial.println("ESP32 ligado, pronto para uso!"); // Envia uma mensagem quando ligado (apenas uma vez)
  
}

void loop() {
  digitalWrite(pinoLed, HIGH); // Estado do LED ligado
  Serial.println("LED ligado"); // Envio de texto para o pc
  delay(1000); // Espera de 1s
  digitalWrite(pinoLed, LOW); // Estado do LED desligado
  Serial.print("LED desligado"); // Envio de texto para o pc
  delay(1000); // Espera de 1s

}
```
> **Observação:** Caso o "Serial.begin()" esteja dando erro, verifique a velocidade no canto inferior direito que está pré selecionada e ajuste com a do código. 
