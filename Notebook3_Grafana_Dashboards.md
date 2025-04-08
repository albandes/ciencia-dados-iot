# Notebook 3 – Dashboards com Grafana

Este guia orienta a criação de dashboards no Grafana utilizando dados armazenados no InfluxDB.

## ✅ Pré-requisitos

- Grafana e InfluxDB rodando em containers
- InfluxDB configurado com bucket, token e organização
- Dados armazenados no InfluxDB pela simulação anterior

## ▶️ Passo a Passo

1. Acesse o Grafana: [http://localhost:3000](http://localhost:3000)
2. Faça login com usuário `admin` e senha `admin`
3. Vá em **⚙️ Configuration → Data Sources → Add data source**
   - Escolha **InfluxDB**
   - URL: `http://influxdb:8086`
   - Token: `meu-token`
   - Organization: `minha-org`
   - Bucket: `iot-dados`
4. Clique em **Save & Test**

## 📊 Criar Dashboard

1. Vá em **+ Create → Dashboard → Add new panel**
2. Insira a seguinte query Flux:

```flux
from(bucket: "iot-dados")
  |> range(start: -1h)
  |> filter(fn: (r) => r._measurement == "medidas")
  |> filter(fn: (r) => r._field == "temperatura")
```

3. Escolha o tipo de visualização (gráfico de linha, gauge, etc.)
4. Clique em **Apply** para adicionar ao dashboard
5. Repita para outros campos como `umidade`

## 💡 Dica Extra

Você pode configurar alertas e salvar snapshots dos dashboards.

---

**Autor:** Curso Ciência de Dados na IoT – 2025