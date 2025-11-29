
---

# 🎨 **FakePinterest — Projeto Fullstack com Flask**

Um projeto inspirado no Pinterest, desenvolvido para estudo de **Flask**, **bancos de dados**, **autenticação**, **upload de imagens** e **deploy em produção**.
A aplicação permite criar contas, fazer login, postar imagens e visualizar um feed similar ao Pinterest.

---

## 🚀 **Tecnologias Utilizadas**

### 🔹 **Backend**

* **Python 3.11**
* **Flask** — microframework web principal

---

### 🔹 **Frontend**

* **HTML5**
* **CSS3**
* Templates com **Jinja2**
* Arquivos estáticos servidos pelo Flask (`/static/css`, `/static/img`)

---

### 🔹 **Banco de Dados**

* **SQLite (ambiente local)**
* **PostgreSQL (produção)** — via Render

O SQLAlchemy detecta o banco automaticamente através da variável de ambiente:

```python
app.config["SQLALCHEMY_DATABASE_URI"] = os.getenv("DATABASE_URL", "sqlite:///comunidade.db")
```

---

### 🔹 **Servidor / Deploy**

O projeto foi publicado usando:

## 🌐 **Render**

* Servidor WSGI configurado automaticamente
* Deploy contínuo via GitHub
* Suporte a ambiente virtual e variáveis de ambiente
* Banco de dados PostgreSQL integrado

---

## 📌 **Funcionalidades**

### 🧑‍🤝‍🧑 **Autenticação**

* Criar conta
* Login e Logout
* Hash de senhas com Bcrypt
* Proteção de rotas com Flask-Login

### 🖼 **Postagem de Imagens**

* Upload de fotos usando WTForms e Flask
* Salvamento seguro com `secure_filename`
* Armazenamento em `/fotos_posts`

### 📷 **Feed de Fotos**

* Mostra fotos de todos os usuários
* Ordenação por data
* Cada usuário tem seu próprio perfil

### 👤 **Perfil do Usuário**

* Upload de fotos pessoais
* Visualização de imagens enviadas
* Permissões: só o dono pode postar no próprio perfil

---

## 📁 **Estrutura do Projeto**

```
fakepinterest/
│
├── static/
│   ├── css/
│   ├── fotos_site/
│   └── fotos_posts/
│
├── templates/
│   ├── homepage.html
│   ├── criarconta.html
│   ├── perfil.html
│   └── feed.html
│
├── __init__.py
├── routes.py
├── models.py
├── forms.py
└── criar_banco.py (opcional)
└── main.py
```

---

## 🛠 **Como Rodar o Projeto Localmente**

### 1. Clonar o repositório:

```bash
git clone https://github.com/seu-usuario/fakepinterest.git
cd fakepinterest
```

### 2. Criar ambiente virtual:

```bash
python -m venv venv
```

### 3. Ativar o ambiente:

#### Windows:

```bash
venv\Scripts\activate
```

#### Linux/Mac:

```bash
source venv/bin/activate
```

### 4. Instalar dependências:

```bash
pip install -r requirements.txt
```

## **5. Ajustar o banco de dados para rodar localmente**

Por padrão, o projeto usa a variável de ambiente do Render:

```python
app.config["SQLALCHEMY_DATABASE_URI"] = os.getenv("DATABASE_URL")
```

Para rodar localmente com **SQLite**, faça o seguinte:

### ➤ Abra o arquivo `fakepinterest/__init__.py`

Localize estas linhas:

```python
app.config["SQLALCHEMY_DATABASE_URI"] = os.getenv("DATABASE_URL")
#app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///comunidade.db"
```

### ➤ Agora altere assim:

* **Comente** a linha com `os.getenv("DATABASE_URL")`
* **Descomente** a linha do SQLite

Fica assim:

```python
#app.config["SQLALCHEMY_DATABASE_URI"] = os.getenv("DATABASE_URL")
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///comunidade.db"
```

---

## **6. Criar o banco de dados local**

Execute o arquivo:

```bash
python criar_banco.py
```

### 6. Rodar o servidor:

```bash
python main.py
```

---

## 🌎 **Deploy**

A aplicação foi publicada no Render com:

* Build automático via GitHub
* Variáveis de ambiente configuradas
* Banco PostgreSQL
* Servidor WSGI padrão

Link da aplicação:
👉 *(https://pinterestfake-3owr.onrender.com)*

---

## 📜 **Licença**

Projeto desenvolvido apenas para fins educacionais. Sinta-se livre para estudar, modificar e usar como referência.

---





