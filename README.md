# baumannzinho-upload
Gerenciador de arquivos
npx npm i -g @nestjs/cli
npx nest new upload
npm run start
http://localhost:3000/
cd ./upload/
npm install @types/multer
# 📁 API de Upload de Arquivos - NestJS

API desenvolvida com NestJS para upload, listagem e remoção de arquivos, incluindo:

- Upload de imagens
- Restrição de tamanho (máximo 5MB)
- Validação de formatos
- Exclusão de arquivos
- Tratamento de erros HTTP

---

# 🚀 Tecnologias Utilizadas

- NestJS
- TypeScript
- Multer
- Node.js
- File System (fs)

---

# 📦 Pré-requisitos

Antes de começar, você precisa ter instalado:

- Node.js
- npm
- Git

---

# ⚙️ Instalação e Execução

## 1. Clonar o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
```

---

## 2. Entrar na pasta do projeto

```bash
cd seu-repositorio
```

---

## 3. Instalar as dependências

```bash
npm install
```

---

## 4. Rodar o projeto

```bash
npm run start:dev
```

A aplicação estará rodando em:

```txt
http://localhost:3000
```

---

# 📂 Estrutura de Upload

Os arquivos enviados são armazenados automaticamente na pasta:

```txt
/drive
```

---

# 📌 Endpoints da API

# 1️⃣ Upload de Arquivo

Faz upload de uma imagem.

## Endpoint

```http
POST /arquivo/upload
```

---

## FormData

| Campo | Tipo |
|---|---|
| file | Arquivo |

---

## Formatos Permitidos

- JPG
- JPEG
- PNG
- TIFF

---

## Limite Máximo

```txt
5MB
```

---

## Exemplo de Sucesso

### Status HTTP

```http
201 Created
```

### Resposta

```json
{
  "message": "Arquivo enviado com sucesso!",
  "filename": "file-1747766000.png",
  "originalname": "imagem.png",
  "size": 120000
}
```

---

## Exemplo de Erro - Arquivo Maior que 5MB

### Status HTTP

```http
413 Payload Too Large
```

### Resposta

```json
{
  "statusCode": 413,
  "message": "Arquivo excede o limite máximo de 5MB."
}
```

---

## Exemplo de Erro - Formato Inválido

### Status HTTP

```http
400 Bad Request
```

### Resposta

```json
{
  "statusCode": 400,
  "message": "Formato inválido. Envie apenas JPG, JPEG, PNG ou TIFF.",
  "error": "Bad Request"
}
```

---

## Exemplo de Erro - Nenhum Arquivo Enviado

### Status HTTP

```http
400 Bad Request
```

### Resposta

```json
{
  "statusCode": 400,
  "message": "Nenhum arquivo enviado."
}
```

---

# 2️⃣ Listar Arquivos

Lista todos os arquivos armazenados.

## Endpoint

```http
GET /arquivo
```

---

## Exemplo de Sucesso

### Status HTTP

```http
200 OK
```

### Resposta

```json
{
  "total": 2,
  "files": [
    {
      "filename": "file-1747766000.png",
      "size": 120000,
      "criado": "2026-05-20T18:00:00.000Z"
    },
    {
      "filename": "file-1747766010.jpg",
      "size": 98000,
      "criado": "2026-05-20T18:01:00.000Z"
    }
  ]
}
```

---

## Exemplo de Erro

### Status HTTP

```http
400 Bad Request
```

### Resposta

```json
{
  "statusCode": 400,
  "message": "Não foi possível listar os arquivos."
}
```

---

# 3️⃣ Remover Arquivo

Remove um arquivo utilizando o nome dele.

## Endpoint

```http
DELETE /arquivo/:filename
```

---

## Parâmetro da URL

| Parâmetro | Descrição |
|---|---|
| filename | Nome do arquivo |

---

## Exemplo

```http
DELETE /arquivo/file-1747766000.png
```

---

## Exemplo de Sucesso

### Status HTTP

```http
200 OK
```

### Resposta

```json
{
  "mensagem": "Arquivo removido com sucesso!"
}
```

---

## Exemplo de Erro - Arquivo Não Encontrado

### Status HTTP

```http
404 Not Found
```

### Resposta

```json
{
  "statusCode": 404,
  "message": "Arquivo file-1747766000.png não encontrado",
  "error": "Not Found"
}
```

---

# 📌 Regras Implementadas

✅ Upload de imagens  
✅ Restrição de tamanho máximo (5MB)  
✅ Validação de formatos  
✅ Remoção de arquivos  
✅ Tratamento de erros HTTP  
✅ Respostas em JSON  

---

# 👨‍💻 Autor

Projeto desenvolvido para fins acadêmicos utilizando NestJS.