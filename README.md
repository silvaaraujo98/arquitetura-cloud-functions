
# 🚀 Python Cloud Function Template

Este é um template profissional para o desenvolvimento de **Google Cloud Functions** utilizando Python. Ele segue boas práticas de modularização, separando a lógica de negócio das integrações de infraestrutura.

## 📁 Estrutura do Projeto

```text
.
├── functions/              # Código fonte da função
│   ├── core/               # Lógica principal e regras de negócio
│   ├── services/           # Integrações (DB, APIs, Storage)
│   ├── utils/              # Helpers e utilitários
│   ├── main.py             # Entry point da função
│   └── requirements.txt    # Dependências
├── tests/                  # Testes unitários e integração
├── .gcloudignore           # Arquivos ignorados no deploy
├── .gitignore              # Arquivos ignorados pelo Git
└── README.md               # Documentação

```

## 🛠️ Configuração Local

### 1. Pré-requisitos

* Python 3.9 ou superior
* [Google Cloud SDK (gcloud CLI)](https://cloud.google.com/sdk/docs/install)
* Ambiente virtual (venv)

### 2. Instalação

Clone o repositório e configure o ambiente:

```bash
# Criar ambiente virtual
python -m venv venv

# Ativar ambiente (Linux/macOS)
source venv/bin/activate

# Ativar ambiente (Windows)
.\venv\Scripts\activate

# Instalar dependências
pip install -r functions/requirements.txt

```

### 3. Execução Local

Para testar a função localmente, utilizamos o `functions-framework`:

```bash
functions-framework --target=handler --debug

```

A função estará disponível em `http://localhost:8080`.

## ☁️ Deploy

Para enviar a função para o Google Cloud, utilize o comando abaixo ajustando os parâmetros:

```bash
gcloud functions deploy NOME_DA_FUNCAO \
  --gen2 \
  --runtime=python310 \
  --region=southamerica-east1 \
  --source=./functions \
  --entry-point=handler \
  --trigger-http \
  --allow-unauthenticated

```

## 🧪 Testes

Os testes são gerenciados pelo `pytest`. Para rodar:

```bash
pytest

```

## 📝 Notas

* Mantenha o arquivo `main.py` o mais limpo possível.
* Utilize a pasta `services/` para qualquer chamada de API externa ou banco de dados.
* Variáveis de ambiente sensíveis devem ser configuradas via **Secret Manager**.

```

---

### Dicas para o seu Template:

1.  **`.gcloudignore`:** Não esqueça de criar este arquivo na raiz. Ele funciona como o `.gitignore`, mas evita que o Google suba gigabytes de lixo (como a pasta `venv/`) para a nuvem. No mínimo, coloque `venv/` e `__pycache__/` nele.
2.  **`requirements.txt`:** Certifique-se de que ele está **dentro** da pasta onde o `main.py` reside, caso contrário o deploy do Google Cloud falhará por não encontrar as dependências.

Deseja que eu escreva também um arquivo de **GitHub Action** para automatizar o deploy sempre que você fizer um push na `main`?

```
