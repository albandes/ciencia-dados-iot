# Ementa: Ciência de Dados na IoT – Foco em Banco de Dados

**Carga horária total:** 10 horas  
**Formato:** Teórico e prático (com uso de notebooks e simulações via Docker)  
**Público-alvo:** Estudantes e profissionais de TI, Ciência de Dados, Engenharia, IoT e áreas afins

---

## 🎯 Objetivo Geral

Capacitar os participantes a coletar, armazenar, processar e visualizar dados de dispositivos IoT, com foco em bancos de dados de séries temporais e ferramentas de análise.

---

## 📘 Conteúdo Programático

### Módulo 1 – Introdução à IoT e à Ciência de Dados (1h)
- Conceitos de IoT e exemplos de aplicações reais
- Arquiteturas típicas de IoT: sensor → gateway → nuvem
- Volume, variedade e velocidade dos dados gerados

### Módulo 2 – Fundamentos de Banco de Dados na IoT (1h)
- Desafios dos dados IoT: séries temporais e granularidade
- Comparação entre InfluxDB, TimescaleDB, MongoDB e SQLite
- Introdução ao InfluxDB

### Módulo 3 – Simulação e Coleta de Dados com MQTT (2h)
- Instalação e uso do Mosquitto como broker MQTT
- Desenvolvimento de simuladores de sensores em Python
- Publicação de dados IoT com `paho-mqtt`

### Módulo 4 – Armazenamento de Dados no InfluxDB (2h)
- Conceitos: bucket, org, token, field, tag
- Inserção de dados via Python com `influxdb-client`
- Persistência e organização de séries temporais

### Módulo 5 – Visualização de Dados com Grafana (2h)
- Conexão do Grafana ao InfluxDB
- Criação de dashboards interativos
- Queries com Flux e painéis com alertas

### Módulo 6 – Pipeline IoT com Docker Compose (2h)
- Construção do ambiente completo: MQTT → InfluxDB → Grafana
- Integração dos serviços em containers
- Execução prática com `docker-compose`

---

## 💻 Metodologia

- Aulas demonstrativas com apoio de slides
- Execução prática com notebooks e containers Docker
- Projeto final integrando todos os componentes

---

## 📚 Recursos Necessários

- Docker e Docker Compose instalados
- Python 3.8+ com bibliotecas `paho-mqtt`, `influxdb-client`
- Navegador moderno (para acesso ao Grafana e InfluxDB UI)

---

## 📈 Projeto Final

Implementar um pipeline funcional de IoT, com simulação de sensores, envio de dados via MQTT, armazenamento no InfluxDB e visualização em dashboards no Grafana.

---

**Autor:** Curso Ciência de Dados na IoT – 2025  
**Licença:** MIT / Creative Commons