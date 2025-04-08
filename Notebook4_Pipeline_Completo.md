# Notebook 4 – Pipeline Completo: Sensor → MQTT → InfluxDB → Grafana

Este ambiente executa todos os componentes de um pipeline IoT via Docker Compose.

---

## 🚀 Componentes

- **Simulador de sensores (Python)**: envia dados via MQTT
- **Mosquitto (MQTT Broker)**: recebe os dados no tópico `iot/sensores`
- **Subscriber MQTT (Python)**: escuta o tópico e grava os dados no InfluxDB
- **InfluxDB 2.x**: armazena os dados de sensores
- **Grafana**: permite visualizar os dados em tempo real

---

## ▶️ Como usar

1. Descompacte o diretório
2. No terminal, execute:

```bash
docker-compose up --build
```

Isso irá:

- Iniciar o broker MQTT
- Subir o simulador e o subscriber (ambos containers Python)
- Inicializar InfluxDB e Grafana

---

## 🌐 Acessos

- **InfluxDB UI**: http://localhost:8086  
  (Org: `minha-org`, Bucket: `iot-dados`, Token: `meu-token`)

- **Grafana**: http://localhost:3000  
  (Usuário: `admin`, Senha: `admin`)

---

## 📂 Estrutura de Pastas

```
.
├── simulador/        # Simulador MQTT
│   ├── simulador.py
│   ├── requirements.txt
│   └── Dockerfile
├── subscriber/       # Subscriber que grava no InfluxDB
│   ├── subscriber.py
│   ├── requirements.txt
│   └── Dockerfile
├── docker-compose.yml
└── README.md
```

---

## 📌 Observações

- O simulador envia dados a cada 5 segundos.
- O subscriber grava os dados recebidos no InfluxDB com precisão de nanosegundos.
- O Grafana pode ser configurado com dashboards baseados nas medições `medidas`.

---

**Autor:** Curso Ciência de Dados na IoT – 2025  
**Licença:** MIT