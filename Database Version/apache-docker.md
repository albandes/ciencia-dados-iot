Aqui está o arquivo único `.md` completo com todas as instruções:

```markdown
# Guia Completo: Servidor Apache no Docker para Windows

## Pré-requisitos
- Docker Desktop instalado e configurado no Windows
- Terminal (PowerShell ou Prompt de Comando) com permissões administrativas
- 2GB de espaço livre em disco (mínimo recomendado)

## 1. Configuração Inicial

### 1.1 Verifique a instalação do Docker
```powershell
docker --version
```

### 1.2 Crie a estrutura de diretórios
```powershell
mkdir C:\docker-apache
mkdir C:\docker-apache\html
mkdir C:\docker-apache\conf
mkdir C:\docker-apache\logs
```

## 2. Configuração do Apache

### 2.1 Crie um arquivo HTML de teste
```powershell
@"
<!DOCTYPE html>
<html>
<head>
    <title>Apache no Docker</title>
</head>
<body>
    <h1>Servidor Apache rodando no Docker!</h1>
    <p>Esta é uma página de teste.</p>
</body>
</html>
"@ | Out-File -FilePath "C:\docker-apache\html\index.html" -Encoding UTF8
```

### 2.2 (Opcional) Crie um arquivo de configuração personalizado
```powershell
docker run --rm httpd:latest cat /usr/local/apache2/conf/httpd.conf > C:\docker-apache\conf\httpd.conf
```

## 3. Execução do Container

### 3.1 Comando básico de execução
```powershell
docker run -dit `
  --name meu-apache `
  -p 8080:80 `
  -v C:\docker-apache\html:/usr/local/apache2/htdocs `
  -v C:\docker-apache\conf:/usr/local/apache2/conf `
  -v C:\docker-apache\logs:/usr/local/apache2/logs `
  httpd:latest
```

### 3.2 Verificação do container
```powershell
docker ps -a --filter "name=meu-apache"
```

## 4. Gerenciamento do Servidor

### 4.1 Comandos úteis
```powershell
# Parar o container
docker stop meu-apache

# Iniciar o container
docker start meu-apache

# Reiniciar o container
docker restart meu-apache

# Acessar o terminal do container
docker exec -it meu-apache bash

# Remover o container
docker rm -f meu-apache
```

### 4.2 Monitoramento
```powershell
# Ver logs do Apache
docker logs meu-apache

# Ver consumo de recursos
docker stats meu-apache
```

## 5. Configurações Avançadas

### 5.1 Usando Docker Compose
Crie um arquivo `docker-compose.yml`:
```yaml
version: '3.8'
services:
  apache:
    image: httpd:latest
    container_name: meu-apache
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/local/apache2/htdocs
      - ./conf:/usr/local/apache2/conf
      - ./logs:/usr/local/apache2/logs
    restart: unless-stopped
```

Execute com:
```powershell
docker-compose up -d
```

### 5.2 Configuração de hosts virtuais
1. Edite o arquivo `C:\docker-apache\conf\httpd.conf`
2. Descomente a linha:
   ```apache
   Include conf/extra/httpd-vhosts.conf
   ```
3. Crie/edite `C:\docker-apache\conf\extra\httpd-vhosts.conf`

## 6. Solução de Problemas

### 6.1 Erros comuns
- **Porta em uso**: Use `netstat -ano | findstr 8080` e mude a porta ou libere a atual
- **Problemas de permissão**: Execute o terminal como administrador
- **Arquivos não atualizados**: Pare e reinicie o container após alterações

### 6.2 Limpeza
```powershell
# Remover container parado
docker container prune

# Remover imagens não utilizadas
docker image prune -a
```

## Conclusão
Agora você tem um servidor Apache completo rodando no Docker no Windows, com:
- Mapeamento de portas
- Persistência de arquivos HTML
- Configuração personalizável
- Sistema de logs
- Opção para Docker Compose
```

