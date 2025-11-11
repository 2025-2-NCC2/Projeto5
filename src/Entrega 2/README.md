# 🚀 Projeto Interdisciplinar – Lideranças Empáticas

## 📌 Descrição do Projeto

O **Lideranças Empáticas** é uma aplicação web desenvolvida como projeto interdisciplinar do 2º semestre de 2025, curso de Ciência da Computação.

A plataforma permite gerenciar equipes, atividades e usuários envolvidos no projeto, promovendo **transparência, organização e acompanhamento de ações sociais**.

**Entrega 2 contempla:**

* Backend funcional com **Node.js + Express + MySQL**
* Frontend em **React** com layout responsivo (Flexbox/Grid)
* CRUD básico de usuários (Create, Read, Update, Delete)
* Integração parcial frontend ↔ backend via **Axios**
* Autenticação com **JWT**
* Upload de imagens (Multer)
* Dashboard com gráficos de desempenho
* Relatórios em PDF
* Sistema de notificações
* Área de comunicação mentor ↔ equipe

---

## 🛠 Tecnologias Utilizadas

**Frontend:** React, React Router DOM, Recharts, Framer Motion, Bootstrap, Axios, Vite
**Backend:** Node.js, Express, MySQL, MSSQL, CORS, dotenv
**DevTools:** VSCode, Postman, Netlify (frontend), Render (backend)

**Links de Deploy:**

* Backend: [https://twosemestre.onrender.com/](https://twosemestre.onrender.com/)
* Frontend: [https://warm-baklava-3e9f5f.netlify.app/](https://warm-baklava-3e9f5f.netlify.app/)

---

## 📂 Estrutura do Projeto

```
├── 📁 backend
│ ├── 📁 src
│ │ ├── 📄 app.js
│ │ ├── 📄 db.js
│ │ ├── 📄 db.test.js
│ │ ├── 📄 routes.js
│ │ └── 📄 server.js
│ ├── ⚙️ package-lock.json
│ └── ⚙️ package.json
├── 📁 frontend
│ ├── 📁 .netlify
│ │ ├── 📁 blobs-serve
│ │ ├── 📁 functions-internal
│ │ ├── 📁 v1
│ │ │ └── 📁 functions
│ │ └── ⚙️ state.json
│ ├── 📁 public
│ │ ├── 📄 _redirects
│ │ └── 🖼️ vite.svg
│ ├── 📁 src
│ │ ├── 📁 assets
│ │ │ └── 🖼️ react.svg
│ │ ├── 📁 context
│ │ │ └── 📄 AuthContext.jsx
│ │ ├── 📁 css
│ │ │ ├── 🎨 App.css
│ │ │ ├── 🎨 Doacoes.css
│ │ │ ├── 🎨 Equipes.css
│ │ │ ├── 🎨 Eventos.css
│ │ │ ├── 🎨 Home.css
│ │ │ ├── 🎨 HomePage.css
│ │ │ ├── 🎨 Login.css
│ │ │ ├── 🎨 NotFound.css
│ │ │ ├── 🎨 TopMenu.css
│ │ │ ├── 🎨 dashboard.css
│ │ │ ├── 🎨 index.css
│ │ │ └── 🎨 usuarios.css
│ │ ├── 📄 App.jsx
│ │ ├── 📄 Dashboard.jsx
│ │ ├── 📄 Doacoes.jsx
│ │ ├── 📄 Equipes.jsx
│ │ ├── 📄 Eventos.jsx
│ │ ├── 📄 HomePage.jsx
│ │ ├── 📄 Login.jsx
│ │ ├── 📄 NotFound.jsx
│ │ ├── 📄 TopMenu.jsx
│ │ ├── 📄 home.jsx
│ │ ├── 📄 main.jsx
│ │ └── 📄 usuarios.jsx
│ ├── ⚙️ .gitignore
│ ├── 📝 README.md
│ ├── 📄 eslint.config.js
│ ├── 🌐 index.html
│ ├── ⚙️ netlify.toml
│ ├── ⚙️ package-lock.json
│ ├── ⚙️ package.json
│ └── 📄 vite.config.js
├── ⚙️ .gitignore
└── 📝 README.md
```


> Clique nos links para acessar as pastas diretamente no repositório.

---

## 🛣 Rotas da API (/api)

### Usuários

| Método | Rota            | Descrição                     |
| ------ | --------------- | ----------------------------- |
| GET    | /api/users      | Lista todos os usuários       |
| POST   | /api/users      | Cria um novo usuário          |
| PUT    | /api/users/\:id | Atualiza um usuário existente |
| DELETE | /api/users/\:id | Deleta um usuário pelo ID     |

### Funções

| Método | Rota         | Descrição              |
| ------ | ------------ | ---------------------- |
| GET    | /api/funcoes | Lista todas as funções |

### Login

| Método | Rota       | Descrição                            |
| ------ | ---------- | ------------------------------------ |
| POST   | /api/login | Autentica usuário por e-mail e senha |

---

## 💻 Como Rodar o Projeto Localmente

### Backend

```bash
cd src/Entrega\ 2/Backend
npm install
npm run dev
```

Servidor disponível em: `http://localhost:5000/api`

> Configure o banco de dados em `db.js` antes de rodar.

### Frontend

```bash
cd src/Entrega\ 2/Frontend
npm install
npm run dev
```

Frontend disponível em: `http://localhost:5173`

---

## 🔗 Integração

* O frontend se comunica com a API usando **Axios**
* CRUD de usuários implementado e testado via Postman

---

---

## 🎥 Vídeo Demonstrativo

O vídeo demonstrativo do sistema está disponível dentro da pasta:

```
src/Entrega 1/video-demo.mp4
```

> Abra o arquivo localmente para visualizar o funcionamento do sistema.

---

## 📝 Observações

* Código modularizado, legível e comentado
* Layout responsivo (Flexbox/Grid)
* Testado em navegadores modernos (Chrome, Edge, Firefox)
* Deploy obrigatório: Frontend (Netlify), Backend (Railway/Render)
