
# Docker: Containers na Prática
_Introdução, Instalação e Execução de Imagens Prontas_  
👨‍🏫 Nome do Professor – Disciplina

---

## 📊 Objetivos da Aula

- Entender o que é Docker e para que serve  
- Instalar e configurar o Docker  
- Utilizar imagens prontas (com foco em Apache)  
- Rodar um container localmente  
- Conhecer os principais comandos do Docker

---

## 📦 O que é Docker?

Docker é uma plataforma para empacotar, distribuir e executar aplicações em **containers**.

Containers são unidades leves e isoladas que contêm tudo que a aplicação precisa para funcionar.

🚣 **Analogia com container de navio**  
Padroniza, organiza e funciona em qualquer ambiente: do notebook à nuvem.

---

## ✅ Por que usar Docker?

- Elimina o problema do "funciona na minha máquina"
- Ambientes de desenvolvimento mais rápidos e consistentes
- Menor consumo de recursos que máquinas virtuais
- Portabilidade: roda em qualquer lugar com Docker instalado
- Ideal para DevOps, CI/CD e microserviços

---

## 🔧 Conceitos Básicos do Docker

### 🧱 Imagem
Uma imagem é um **modelo imutável** que contém tudo que a aplicação precisa: sistema, código, dependências, etc.

### 📦 Container
Um container é uma **instância em execução** de uma imagem. Ele é leve, rápido e isolado, compartilhando recursos com o host.

### 📅 Dockerfile
Arquivo de texto com instruções para criar uma imagem personalizada (ex: FROM, RUN, COPY, EXPOSE).

### ☁️ Docker Hub
Repositório público de imagens prontas para uso. Permite buscar, baixar e compartilhar imagens.

---

## 🏗️ Arquitetura Docker

### 🔧 Docker Engine
Componente principal que executa containers. Inclui:
- **Daemon (`dockerd`)**: gerencia containers
- **API**: permite comunicação com ferramentas externas

### 💻 Docker CLI
Interface de linha de comando usada para interagir com o Docker Engine. Ex: `docker run`, `docker pull`.

### ☁️ Docker Hub (Registry)
Repositório público e gratuito para armazenar e buscar imagens. Ex: `httpd`, `mysql`, `node`.

### 🖥️ Host
Sistema onde o Docker está instalado (ex: seu notebook ou um servidor). É onde os containers de fato rodam.

---

## 💻 Instalação do Docker

**Windows / macOS:**  
- Baixar de: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

**Linux (Ubuntu):**
```bash
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

Verifique se está funcionando:
```bash
docker --version
```

---

## 🔤 Comandos Básicos do Docker

```bash
docker pull httpd         # Baixa imagem do Apache
docker run httpd          # Roda container Apache
docker ps                 # Containers ativos
docker ps -a              # Todos containers
docker stop <id>          # Para container
docker rm <id>            # Remove container
docker images             # Lista imagens
docker rmi <id>           # Remove imagem
```

Esses comandos permitem baixar, executar e gerenciar containers.

---

## 🌐 Executando Apache com Docker

```bash
docker run -d -p 8080:80 httpd
```

Acesse no navegador:  
[http://localhost:8080](http://localhost:8080)

📄 Você verá a página padrão do Apache rodando dentro de um container.

---

## 🧪 Exemplo com Página HTML Personalizada

1. Criar uma pasta e um arquivo HTML:
```bash
mkdir meu-site
echo "<h1>Bem-vindo ao meu site!</h1>" > meu-site/index.html
```

2. Executar container com volume:
```bash
docker run -d -p 8080:80 -v "$PWD/meu-site":/usr/local/apache2/htdocs/ httpd
```

3. Recarregue o navegador: sua própria página será exibida!

---

## 🔍 Explorando o Docker Hub

- Site oficial: [https://hub.docker.com](https://hub.docker.com)
- Use o comando:
```bash
docker search apache
```
- Exemplos populares: `httpd`, `mysql`, `node`, `python`, `wordpress`

🌐 Milhares de imagens públicas e atualizadas!

---

## 🎯 Conclusão e Próximos Passos

- Containers trazem agilidade, consistência e portabilidade
- Vimos como rodar o Apache via Docker
- Explore mais: Docker Compose, Dockerfile e orquestração com Kubernetes
- Comece a criar seu próprio ambiente isolado e replicável com Docker!

---
