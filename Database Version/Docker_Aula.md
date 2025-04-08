
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

### Pré-requisitos
- Docker Desktop instalado no Windows
- Terminal (PowerShell ou Prompt de Comando)

### Passo a passo

1. Baixar a imagem oficial do Apache
```powershell
docker pull httpd:latest
```

2. Criar diretório para os arquivos HTML
```powershell
mkdir C:\apache-html
```

3. Criar arquivo HTML de teste
```powershell
echo "<h1>Meu servidor Apache no Docker funciona!</h1>" > C:\apache-html\index.html
```

4. Executar o container Apache
```powershell
docker run -dit --name meu-apache -p 8080:80 -v C:\apache-html:/usr/local/apache2/htdocs/ httpd:latest
```

Explicação dos parâmetros:

* `-dit`: Executa o container em segundo plano (detached) e fornece um terminal interativo.
* `--name meu-apache`: Define o nome do container como `meu-apache`. Isso facilita referenciar o container em comandos futuros.
* `-p 8080:80`: Mapeia a porta `8080` da sua máquina host para a porta `80` dentro do container. Isso permite acessar o servidor web rodando no container através do endereço `http://localhost:8080` (ou o IP da sua máquina seguido por `:8080`).
* `-v C:\apache-html:/usr/local/apache2/htdocs/`: Monta um volume. Isso significa que o diretório local `C:\apache-html` na sua máquina será sincronizado com o diretório `/usr/local/apache2/htdocs/` dentro do container. Quaisquer arquivos que você colocar em `C:\apache-html` estarão disponíveis no servidor web dentro do container, e vice-versa.

**Em resumo:**

O comando `docker run` com estes parâmetros irá:

1.  Criar e iniciar um container em segundo plano.
2.  Nomear este container como `meu-apache`.
3.  Tornar o servidor web (rodando na porta 80 dentro do container) acessível na porta 8080 da sua máquina.
4.  Permitir que você modifique os arquivos do servidor web através do diretório local `C:\apache-html`.
   
5. Verificar se o container está rodando

```powershell
docker ps
```

6. Acessar no navegador
   
[http://localhost:8080](http://localhost:8080)

**Comandos úteis adicionais***

* `docker stop meu-apache`: Parar o container
* `docker start meu-apache`: Iniciar o container 
* `docker exec -it meu-apache bash`: Acessar o shell do container (para troubleshooting)
* `docker rm -f meu-apache`: Remover o container (quando não for mais necessário)

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
