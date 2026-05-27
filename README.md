# iAutosBot - Simulador de ChatBot com GenAI e VectorDB

Projeto demonstrativo de um chatbot para atendimento de usuários de um marketplace fictício de veículos, utilizando **IA Generativa**, **LangChain**, **ChromaDB** e arquitetura **RAG - Retrieval Augmented Generation**.

O objetivo é responder dúvidas sobre regras de uso, publicação de anúncios, fraude, mau uso e políticas da plataforma iAutos com base em um documento PDF versionado no próprio repositório.

## Visão geral

```text
PDF de políticas em data/
        ↓
Leitura com PyPDFLoader
        ↓
Chunking com RecursiveCharacterTextSplitter
        ↓
Embeddings com OpenAI
        ↓
VectorDB local com ChromaDB
        ↓
Retriever com MMR
        ↓
Prompt controlado + LLM
        ↓
ChatBot RAG com memória conversacional
```

## Estrutura do repositório

```text
iautos-chatbot-rag-genai/
│
├── data/
│   └── politicas_iautos.pdf
│
├── notebooks/
│   └── iautos-chatbot-rag-genai.ipynb
│
├── .env.example
├── .gitignore
├── README.md
└── requirements.txt
```

## Base de conhecimento

A base documental usada pelo chatbot está na pasta `data/`:

```text
data/politicas_iautos.pdf
```

Esse PDF é utilizado para criar os chunks, gerar embeddings e construir o VectorDB local com ChromaDB.

## Segurança das chaves

As chaves de API **não ficam salvas no notebook**.

Para executar o projeto localmente, copie o arquivo `.env.example` para `.env` e preencha a variável abaixo:

```bash
OPENAI_API_KEY=sua_chave_aqui
```

O arquivo `.env` está protegido pelo `.gitignore` e não deve ser enviado ao GitHub.

## Como executar

1. Clone o repositório:

```bash
git clone https://github.com/ThatianeBotelho/iautos-chatbot-rag-genai.git
cd iautos-chatbot-rag-genai
```

2. Crie e ative um ambiente virtual:

```bash
python -m venv .venv
source .venv/bin/activate      # Linux/Mac
.venv\Scripts\activate       # Windows
```

3. Instale as dependências:

```bash
pip install -r requirements.txt
```

4. Configure a chave da OpenAI:

```bash
cp .env.example .env
```

Depois, edite o arquivo `.env` com sua chave local.

5. Execute o notebook:

```text
notebooks/iautos-chatbot-rag-genai.ipynb
```

## O que o projeto demonstra

- Construção de pipeline RAG com LangChain.
- Leitura de PDF como base de conhecimento.
- Divisão de documentos em chunks.
- Criação de embeddings com OpenAI.
- Persistência de vetores com ChromaDB local.
- Recuperação de contexto com MMR.
- Prompt Engineering para reduzir respostas fora de escopo.
- Memória conversacional com LangChain.
- Testes com perguntas diretas, ambíguas, fora de escopo e tentativas de indução.

## Observação sobre o VectorDB

O VectorDB é gerado localmente durante a execução do notebook e **não deve ser versionado** no GitHub.

A pasta `chromadb_iautos_final/` está no `.gitignore` porque é um artefato reproduzível a partir do PDF e do notebook.

## Autoria

Projeto desenvolvido como parte do MBA em Engenharia de Dados - FIAP.

**Participantes:**

- RM 368317 - Alef Anderson Fernandes Clarindo da Silva
- RM 367285 - Tatiane Santana da Silva
- RM 367559 - Thatiane Martins Batista Botelho
- RM 366443 - Viviane Corrêa Nunes
