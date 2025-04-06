# 🌐 Curso: Ciência de Dados na Internet das Coisas (IoT)

Bem-vindos! Este espaço reúne todo o material necessário para acompanhar o curso prático de 10h sobre **Ciência de Dados aplicada à IoT**.

---

## 📦 Downloads

### 🔬 Notebooks e Dados
- [📁 Pacote completo (local + Docker)](./curso_completo_iot_ciencia_dados.zip)
- [📁 Versão adaptada para Google Colab](./curso_iot_colab_version.zip)

### 📊 Dados simulados
- [sensor_temp_umid.csv](./sensor_temp_umid.csv)

---

## 📗 Módulos do Curso

| Módulo | Tópico | Notebook |
|--------|--------|----------|
| 3 | Pré-processamento de Dados | `03_preprocessamento_dados_iot.ipynb` |
| 4 | Análise Exploratória (EDA) | `04_eda_dados_iot.ipynb` |
| 5 | Machine Learning com IoT | `05_ml_iot_basico.ipynb` |
| 6 | Projeto Final | `06_projeto_final_exemplo.ipynb` |

---

## ☁️ Acesso via Google Colab

> Recomendado para quem não deseja instalar nada.

- [Abrir no Colab: Pré-processamento](https://colab.research.google.com/github/SEU_USUARIO/iot-ciencia-dados-repo/blob/main/notebooks/03_preprocessamento_dados_iot_colab.ipynb)
- [Abrir no Colab: EDA](https://colab.research.google.com/github/SEU_USUARIO/iot-ciencia-dados-repo/blob/main/notebooks/04_eda_dados_iot_colab.ipynb)
- [Abrir no Colab: Machine Learning](https://colab.research.google.com/github/SEU_USUARIO/iot-ciencia-dados-repo/blob/main/notebooks/05_ml_iot_basico_colab.ipynb)
- [Abrir no Colab: Projeto Final](https://colab.research.google.com/github/SEU_USUARIO/iot-ciencia-dados-repo/blob/main/notebooks/06_projeto_final_exemplo_colab.ipynb)

---

## 🐳 Rodar localmente com Docker

```bash
docker build -t curso-iot .
docker run -p 8888:8888 -v $(pwd):/home/jovyan curso-iot
