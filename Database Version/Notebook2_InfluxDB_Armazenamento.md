# Notebook 2 – Armazenamento com InfluxDB

Este notebook recebe dados simulados (como temperatura e umidade) e os grava em um banco InfluxDB 2.x.

**Pré-requisitos:**
- InfluxDB rodando em http://localhost:8086
- Token, organização e bucket já criados
- Biblioteca: `pip install influxdb-client`

```python
from influxdb_client import InfluxDBClient, Point, WriteOptions, WritePrecision
from datetime import datetime
import random

# Configurações do InfluxDB
url = "http://localhost:8086"
token = "meu-token"
org = "minha-org"
bucket = "iot-dados"

# Criar cliente
client = InfluxDBClient(url=url, token=token, org=org)
write_api = client.write_api(write_options=WriteOptions(batch_size=1))

# Simular dados
temperatura = round(random.uniform(22, 28), 2)
umidade = round(random.uniform(40, 60), 2)
timestamp = datetime.utcnow().isoformat()

# Criar ponto de dados
ponto = (
    Point("medidas")
    .tag("sensor", "simulado")
    .field("temperatura", temperatura)
    .field("umidade", umidade)
    .time(timestamp, WritePrecision.NS)
)

# Escrever no InfluxDB
write_api.write(bucket=bucket, org=org, record=ponto)
print(f"Dados inseridos: {ponto}")

# Encerrar cliente
client.close()
```