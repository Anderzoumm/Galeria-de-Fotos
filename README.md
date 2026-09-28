# 📷 Galeria de Imagens — Django

Sistema web para cadastro e organização de imagens em categorias, com filtro, ordenação e paginação. Desenvolvido com **Django** e **PostgreSQL**.

## ✨ Funcionalidades

- Cadastro, listagem, edição e exclusão de imagens (**CRUD** completo)
- Organização das imagens por **categorias**
- **Filtro** por categoria
- **Ordenação** por mais recentes, mais antigas ou título (A-Z)
- **Paginação** (6 imagens por página)
- Painel administrativo do Django para gerenciar categorias e imagens

## 🛠️ Tecnologias

- [Python](https://www.python.org/)
- [Django](https://www.djangoproject.com/)
- [PostgreSQL](https://www.postgresql.org/)
- [Pillow](https://pypi.org/project/pillow/) — suporte a upload e validação de imagens
- [psycopg2-binary](https://pypi.org/project/psycopg2-binary/) — conexão do Django com o PostgreSQL
- [python-dotenv](https://pypi.org/project/python-dotenv/) — variáveis de ambiente

## 📁 Estrutura do projeto

```
projeto/
├── manage.py
├── .env                        # variáveis de ambiente (não versionado)
├── media/                      # imagens enviadas pelos usuários
├── core/                       # configurações gerais do projeto
│   ├── settings.py
│   └── urls.py
└── galeria/                    # app principal
    ├── models.py                # models Categoria e Imagem
    ├── views.py                 # views de listar, ver, criar, editar e excluir
    ├── urls.py                  # rotas do app
    ├── admin.py                 # registro no painel admin
    ├── templatetags/
    │   └── galeria_extras.py    # tag personalizada url_replace
    └── templates/galeria/
        ├── base.html
        ├── imagem_list.html
        ├── imagem_detail.html
        ├── imagem_form.html
        └── imagem_confirm_delete.html
```

## 🚀 Como rodar o projeto localmente

### Pré-requisitos

- Python 3.10 ou superior
- PostgreSQL instalado e em execução

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

### 2. Crie e ative o ambiente virtual

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux / macOS
source venv/bin/activate
```

### 3. Instale as dependências

```bash
pip install django pillow psycopg2-binary python-dotenv
```

> Se o projeto tiver um arquivo `requirements.txt`, use `pip install -r requirements.txt` no lugar do comando acima.

### 4. Configure o banco de dados

Crie um banco no PostgreSQL:

```sql
CREATE DATABASE galeria_db;
```

Crie um arquivo `.env` na raiz do projeto com:

```env
DB_NAME=galeria_db
DB_USER=postgres
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=5432
```

### 5. Aplique as migrações

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Crie um superusuário (para acessar o admin)

```bash
python manage.py createsuperuser
```

### 7. Rode o servidor

```bash
python manage.py runserver
```

Acesse:

- **Site:** http://127.0.0.1:8000/
- **Painel admin:** http://127.0.0.1:8000/admin/

## 📝 Cadastrando categorias e imagens

1. Acesse `/admin/` e faça login com o superusuário criado.
2. Cadastre algumas **Categorias** (ex.: Paisagens, Animais, Viagens).
3. Volte para o site e clique em **"+ Nova Imagem"** para cadastrar imagens vinculadas a essas categorias.

## 🗺️ Rotas principais

| Rota | Descrição |
|---|---|
| `/` | Lista de imagens, com filtro, ordenação e paginação |
| `/imagem/<id>/` | Detalhes de uma imagem |
| `/imagem/novo/` | Formulário de cadastro |
| `/imagem/<id>/editar/` | Formulário de edição |
| `/imagem/<id>/deletar/` | Confirmação de exclusão |
| `/admin/` | Painel administrativo do Django |

## ⚠️ Observações

Este é um projeto de estudo. Antes de usar em produção, é recomendado:

- Mover a `SECRET_KEY` do `settings.py` para o `.env`
- Definir `DEBUG = False` e preencher `ALLOWED_HOSTS`
- Adicionar autenticação para restringir quem pode criar, editar e excluir imagens
- Remover o arquivo físico da pasta `media/` ao excluir uma imagem

## 📄 Licença

Projeto de estudo desenvolvido para fins acadêmicos.
