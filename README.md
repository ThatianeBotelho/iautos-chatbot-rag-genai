# iAutosBot — Chatbot RAG com GenAI e VectorDB

Este projeto implementa um simulador de chatbot para atendimento de usuários de um marketplace fictício de veículos, chamado **iAutos**.

A solução utiliza **LangChain**, **OpenAI**, **ChromaDB** e arquitetura **RAG (Retrieval-Augmented Generation)** para responder perguntas com base em um documento de políticas versionado no próprio repositório.

O foco do projeto é demonstrar como uma base documental pode ser transformada em um assistente conversacional capaz de recuperar contexto relevante, manter memória da conversa e reduzir respostas fora do escopo.

---

## Objetivo

O objetivo do projeto é construir um chatbot baseado em documentos, capaz de responder perguntas sobre regras de uso, publicação de anúncios, fraude, mau uso e políticas da plataforma iAutos.

A proposta não é apenas gerar respostas com IA, mas controlar o comportamento do modelo a partir de uma base de conhecimento específica, usando recuperação semântica e instruções de escopo.

---

## Como funciona

O chatbot utiliza um PDF com políticas da plataforma como fonte de conhecimento.

O fluxo principal é:

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
Chatbot RAG com memória conversacional
```

A base vetorial é criada localmente com ChromaDB durante a execução do notebook. Ela não é versionada no GitHub porque pode ser reconstruída a partir do PDF.

---

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

---

## Tecnologias utilizadas

- Python
- LangChain
- OpenAI API
- ChromaDB
- PyPDFLoader
- Jupyter Notebook
- python-dotenv

---

## Configuração das chaves

As chaves de API não são armazenadas no notebook nem versionadas no repositório.

Para executar o projeto, crie um arquivo `.env` a partir do exemplo:

```bash
cp .env.example .env
```

Depois, preencha a variável:

```env
OPENAI_API_KEY=sua_chave_aqui
```

O arquivo `.env` está incluído no `.gitignore`.

---

## Como executar

Clone o repositório:

```bash
git clone https://github.com/ThatianeBotelho/iautos-chatbot-rag-genai.git
cd iautos-chatbot-rag-genai
```

Crie o ambiente virtual:

```bash
python -m venv .venv
```

Ative o ambiente virtual.

Linux/Mac:

```bash
source .venv/bin/activate
```

Windows:

```bash
.venv\Scripts\activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Configure a chave da OpenAI:

```bash
cp .env.example .env
```

Depois, edite o arquivo `.env` com sua chave local.

Execute o notebook:

```text
notebooks/iautos-chatbot-rag-genai.ipynb
```

---

## O que o projeto demonstra

- Construção de pipeline RAG com LangChain.
- Leitura de PDF como base de conhecimento.
- Divisão de documentos em chunks.
- Criação de embeddings com OpenAI.
- Persistência de vetores com ChromaDB local.
- Recuperação de contexto com estratégia MMR.
- Prompt Engineering para reduzir respostas fora de escopo.
- Memória conversacional com LangChain.
- Testes com perguntas diretas, ambíguas, fora de escopo e tentativas de indução.

---

## Observação sobre o VectorDB

O VectorDB é gerado localmente durante a execução do notebook e **não deve ser versionado** no GitHub.

A pasta `chromadb_iautos_final/` está no `.gitignore` porque é um artefato reproduzível a partir do PDF e do notebook.

---

## Autoria

Projeto desenvolvido em coautoria por:

<table>
  <tr>
      <td align="center">
      <img style="border-radius: 50%;" 
           src="https://avatars.githubusercontent.com/ThatianeBotelho" 
           width="100px;" 
           alt="Thatiane Botelho"/>
      <br/>
      <b>Thatiane Botelho</b>
      <br/>
      <a href="https://github.com/ThatianeBotelho">GitHub</a>
    </td>
    <td align="center">
      <img style="border-radius: 50%;" 
           src="https://avatars.githubusercontent.com/tatiane-ss" 
           width="100px;" 
           alt="Tatiane Silva"/>
      <br/>
      <b>Tatiane Silva</b>
      <br/>
      <a href="https://github.com/tatiane-ss">GitHub</a>
    </td>    
    <td align="center">
      <img style="border-radius: 50%;" 
           src="https://avatars.githubusercontent.com/vivianecorrea" 
           width="100px;" 
           alt="Viviane Corrêa"/>
      <br/>
      <b>Viviane Corrêa</b>
      <br/>
      <a href="https://github.com/vivianecorrea">GitHub</a>
    </td>
    <td align="center">
      <img style="border-radius: 50%;" 
           src="https://avatars.githubusercontent.com/alef-and" 
           width="100px;" 
           alt="Alef Anderson Silva"/>
      <br/>
      <b>Alef Anderson Silva</b>
      <br/>
      <a href="https://github.com/alef-and">GitHub</a>
    </td>
  </tr>
</table>
