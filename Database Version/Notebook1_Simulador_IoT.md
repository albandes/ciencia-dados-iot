# Notebook 1 – Simulação de Sensores IoT com Python via Docker

Este projeto simula sensores de temperatura e umidade e envia os dados via MQTT para um broker Mosquitto em container Docker.

## ▶️ Como usar

1. Descompacte este diretório
2. Execute:

```bash
docker-compose up --build
```

O simulador enviará mensagens ao tópico `iot/sensores` a cada 5 segundos.

## 🔧 Serviços

- `mosquitto`: broker MQTT na porta 1883
- `simulador`: envia dados simulados para o tópico MQTT

## 📦 Requisitos

- Docker
- Docker Compose