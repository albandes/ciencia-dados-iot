# Curso: Ciência de Dados na Internet das Coisas (IoT)

Este pacote contém os notebooks práticos e dados simulados utilizados no curso de 10h sobre Ciência de Dados aplicada à Internet das Coisas.

## 📦 Conteúdo

- `sensor_temp_umid.csv`: dados simulados de sensores (temperatura e umidade).
- `03_preprocessamento_dados_iot.ipynb`: limpeza, reamostragem e normalização.
- `04_eda_dados_iot.ipynb`: análise exploratória de dados (gráficos, outliers).
- `05_ml_iot_basico.ipynb`: modelos de machine learning (regressão e clusterização).
- `06_projeto_final_exemplo.ipynb`: exemplo guiado de projeto final.

## 🚀 Como usar

1. Acesse os notebooks em Jupyter ou Google Colab.
2. Certifique-se de que o arquivo `sensor_temp_umid.csv` esteja na mesma pasta.
3. Siga a ordem numérica dos notebooks para melhor aprendizado.

## 💡 Requisitos

- Python 3.x
- Bibliotecas: pandas, matplotlib, seaborn, scikit-learn, scipy

Para instalar as dependências:

```bash
pip install -r requirements.txt
```

Ou rode tudo via Docker (veja abaixo).

## 🐳 Docker (ambiente completo)

1. Clone ou baixe este repositório.
2. Execute:

```bash
docker build -t curso-iot .
docker run -p 8888:8888 -v $(pwd):/home/jovyan curso-iot
```

3. Acesse o Jupyter pelo navegador em: `http://localhost:8888`

## 👨‍🏫 Sugestão de Projeto Final

Use o notebook `06_projeto_final_exemplo.ipynb` como guia para:
- Previsão de variáveis com base em sensores
- Identificação de falhas ou padrões usando ML
- Aplicações em saúde, energia, agricultura, etc.

---

Bons estudos! 🚀
