# Trabalho Final – Curso Ciência de Dados na IoT

## 🎯 Objetivo

Desenvolver um pipeline IoT completo para monitoramento de um ambiente simulado, com sensores virtuais, armazenamento no InfluxDB e visualização via Grafana.

---

## 🧩 Componentes obrigatórios

1. **Simulador de sensores (Python)**
   - Deve gerar 3 tipos de dados (ex: temperatura, umidade, luminosidade)
   - Publicar os dados via MQTT

2. **Subscriber MQTT**
   - Receber os dados do simulador
   - Inserir no InfluxDB com organização adequada

3. **Banco de dados InfluxDB**
   - Bucket, org e token devidamente configurados

4. **Dashboard no Grafana**
   - Pelo menos 2 gráficos interativos
   - Um painel com agregação (ex: média por 10min)

5. **Ambiente Docker Compose**
   - Integrar todos os serviços (Mosquitto, InfluxDB, Grafana, simulador, subscriber)

---

## 📦 Entrega

Entregar um `.zip` contendo:

- Código fonte (simulador e subscriber)
- docker-compose.yml
- README.md com instruções claras
- Capturas de tela dos dashboards

Deve rodar com:

```bash
docker-compose up --build
```

---

## 🎓 Critérios de Avaliação

| Critério                          | Peso  |
|----------------------------------|-------|
| Simulação coerente de sensores   | 20 pts|
| Armazenamento correto no InfluxDB| 20 pts|
| Dashboard funcional e informativo| 20 pts|
| Organização e documentação       | 20 pts|
| Uso adequado do Docker Compose   | 20 pts|

---

## 💡 Dica Extra

Adicione alertas, exportações de dados ou dashboards adicionais se desejar.

---

**Autor:** Curso Ciência de Dados na IoT – 2025  
**Licença:** MIT