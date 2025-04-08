
# Tutorial Visual Completo: Visualizando Dados no InfluxDB e Grafana

Este guia mostra, passo a passo, como acessar, consultar e visualizar os dados coletados em seu ambiente IoT, utilizando tanto a interface gráfica do InfluxDB quanto o Grafana para dashboards.

---

## 📘 Parte 1 – Usando a interface web do InfluxDB (UI)

### ✅ Acesso
1. Abra seu navegador e acesse:
   - **http://localhost:8086**

### ✅ Login
2. Faça login com as credenciais definidas no `docker-compose.yml`, por exemplo:
   - **Username:** `admin`
   - **Password:** `admin123`

Se for seu primeiro acesso, você será guiado para configurar um token, bucket e organização. Use:
- **Org:** `minha-org`
- **Bucket:** `iot-dados`
- **Token:** `meu-token`

### ✅ Navegação básica
3. Após o login:
   - Vá no menu lateral e clique em **Explore** (ícone de bússola)
   - No painel esquerdo, selecione:
     - **Bucket:** `iot-dados`
     - **Measurement:** `medidas`
     - Campos: `temperatura`, `umidade`

### ✅ Query com Flux (opcional)
4. Você pode alternar para o modo Flux e escrever sua própria consulta:
```flux
from(bucket: "iot-dados")
  |> range(start: -1h)
  |> filter(fn: (r) => r._measurement == "medidas")
  |> filter(fn: (r) => r._field == "temperatura")
```
5. Clique em **Submit** para visualizar a saída em tabela ou gráfico.

### ✅ Exportar dados
- Clique no botão de 3 pontos (...) para exportar os dados como CSV, JSON, ou copiar como tabela.

---

## 📊 Parte 2 – Visualização com Grafana

### ✅ Acesso
1. No navegador, vá para:
   - **http://localhost:3000**

### ✅ Primeiro login
2. Use as credenciais padrão:
   - **Username:** `admin`
   - **Password:** `admin`
   - Ao entrar, será solicitado que você altere a senha.

### ✅ Adicionar InfluxDB como fonte de dados
3. No menu lateral:
   - Vá em **⚙️ Settings → Data Sources → Add data source**
   - Selecione **InfluxDB**

4. Configure os campos:
   - **URL:** `http://influxdb:8086`
   - **Organization:** `minha-org`
   - **Token:** `meu-token`
   - **Bucket:** `iot-dados`

Clique em **Save & Test** para confirmar a conexão.

### ✅ Criar painel com dados do sensor
5. Menu lateral → **+ Create → Dashboard → Add new panel**
6. Na aba **Query**, insira:
```flux
from(bucket: "iot-dados")
  |> range(start: -30m)
  |> filter(fn: (r) => r._measurement == "medidas")
  |> filter(fn: (r) => r._field == "temperatura")
```
7. Visualize o gráfico e clique em **Apply**.

### ✅ Personalização
- Altere o título do gráfico
- Escolha o tipo de visualização: linha, gauge, barras, etc
- Defina alertas se necessário

---

## 📁 Outras funcionalidades

### 🔍 Consulta Avançada
- Use agregações com `aggregateWindow()`:
```flux
from(bucket: "iot-dados")
  |> range(start: -1h)
  |> filter(fn: (r) => r._field == "temperatura")
  |> aggregateWindow(every: 5m, fn: mean)
```

### ⏱ Ajuste do período
- No topo direito do dashboard Grafana, altere o intervalo de tempo (ex: última 1h, 6h, 24h)

### 💾 Exportar imagens
- Clique no ícone de engrenagem do painel → Share → Export como PNG

---

## 📌 Resumo
| Ferramenta    | Acesso                 | Função principal                   |
|---------------|------------------------|------------------------------------|
| **InfluxDB UI** | http://localhost:8086 | Consulta, exportação, tokens       |
| **Grafana**     | http://localhost:3000 | Dashboards e visualização gráfica  |

---

**Autor:** Curso Ciência de Dados na IoT – 2025
