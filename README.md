# 🩺 Medical AI Assistant — Tech Challenge Fase 3
> **Framework Híbrido de Assistência Clínica: Fine-Tuning, RAG e Orquestração por Grafos**

[![Python](https://img.shields.io/badge/python-3.10-blue?logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Colab](https://img.shields.io/badge/OpenIn-Colab-orange?logo=googlecolab)](https://colab.research.google.com/)
[![GPU](https://img.shields.io/badge/GPU-T4-red?logo=nvidia)](https://www.nvidia.com/)
[![Status](https://img.shields.io/badge/status-experimental-yellow)](README.md)
[![Model Version](https://img.shields.io/badge/model-TinyLlama--1.1B-blue)](https://huggingface.co/)
[![GPU Cost](https://img.shields.io/badge/estimated-GPU%20T4%20~$0.35/hr-lightgrey)](https://colab.research.google.com/)

---

## 📌 Visão Geral
Este projeto apresenta um Assistente Médico avançado, desenvolvido no âmbito da Pós-Graduação em Inteligência Artificial. 
A solução combina **Fine-Tuning** local, **RAG (Retrieval-Augmented Generation)** 
e orquestração via **LangGraph** para auxiliar em condutas clínicas, 
com foco em precisão, rastreabilidade e segurança na análise de exames e no suporte à decisão médica.

---

## 🎯 Objetivos
- **Personalização:** Fine-tuning com protocolos hospitalares internos (QLoRA)  
- **Precisão Clínica:** Classificação de toxicidade CTCAE  
- **Segurança:** *Guardrails* contra prescrições automáticas  
- **Auditoria:** Logs estruturados em CSV

---

## 🏗️ Arquitetura
Fluxo de decisão **não-linear** via LangGraph:

- FAQ / Protocolos  
- Análise de exames  
- Encaminhamento para Expert LLM (GPT-4o API)

| Componente | Tecnologia | Função |
|-----------------|-----------------|--------|
| **LLM Local** | TinyLlama-1.1B | NLP médico |
| **Fine-Tuning** | PEFT / QLoRA | Especialização clínica |
| **Vector Store** | FAISS | RAG (recuperação semântica) |
| **Expert LLM** | GPT-4o (API) | Análise clínica avançada |
| **Orquestrador** | LangGraph | Controle de fluxo baseado em estados |

---

## 🛠️ Tecnologias
- **IA/ML:** `transformers`, `peft`, `bitsandbytes`, `sentence-transformers`  
- **Orquestração:** `langchain`, `langgraph`  
- **Processamento:** `pandas`, `numpy`, `regex`  
- **Banco Vetorial:** `faiss-cpu`  

---

## 🚀 Executando
### Pré-requisitos
- **Google Colab** (GPU T4 recomendada)  
- **Chave OpenAI:** `OPENAI_API_KEY`  

### ▶️ Passos
1. [Abrir notebook no Colab](https://colab.research.google.com/)  
2. Garantir arquivos JSON em `data/`  
3. Executar células sequencialmente  

---

## 💬 Exemplo de Uso

**Entrada:**  
Pergunta > "Você é paciente ou médico?"
Pergunta > "Qual o seu nome?"
Pergunta > "Assunto:"
Resposta > "Paciente com náusea persistente e perda de apetite."

**Saída:**  
- **CTCAE:** Grau 2 (moderado)  
- **Interpretação:** Toxicidade moderada, impacto nas atividades diárias  
- **Recomendação:** Avaliação clínica necessária — **sem prescrição automática**

---

## 🛡️ Segurança
- **Anonimização:** CPF, CRM, nomes mascarados
- **Filtro de saída:** Bloqueio de prescrições
- **Supervisão humana obrigatória**

---

## 📉 Limitações
- **Dados sintéticos** apenas  
- **Não usar em produção clínica**  
- Possível *hallucinations*  
- Sistema de suporte, não substituto de julgamento humano

---

## 📊 Estrutura do Projeto
```text
├── data/
│ ├── protocolos.json
│ ├── faq_medica.json
│ └── historico_pacientes/
├── logs/
│ ├── operacoes.csv
│ └── consultas.csv
├── notebooks/
│ └── assistente_medico.ipynb
└── README.md

---

📚 Referências

​CTCAE: Common Terminology Criteria for Adverse Events (NIH).
​QLoRA: Efficient Finetuning of Quantized LLMs.
​LangGraph: Stateful Multi-Agent Orchestration.
​FAISS: Facebook AI Similarity Search.

---

​👨‍💻 Autor

​Projeto desenvolvido para o Tech Challenge Fase 3 — 7IADT (FIAP).