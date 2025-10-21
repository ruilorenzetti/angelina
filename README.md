# Angelina
Angelina: Assistente de estudos  com Python+n8n para transcrição de áudio, sumarização, organização de agenda e geração de exercícios usando LLMs locai
# Angelina 🤖

**Assistente de estudos inteligente e autônomo com arquitetura modular baseada em plugins**

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://python.org)
[![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-green.svg)](https://n8n.io)
[![Open Source](https://img.shields.io/badge/Open%20Source-100%25-brightgreen.svg)](https://opensource.org)
[![Self-Hosted](https://img.shields.io/badge/Self--Hosted-Local_LLMs-orange.svg)](https://github.com/ggerganov/llama.cpp)

## 🌟 Sobre o Projeto

O Angelina é um assistente de estudos completo desenvolvido para operar 100% localmente, sem dependência de serviços cloud proprietários. Combina a potência do Python para processamento de áudio e texto com a flexibilidade do n8n para orquestração de workflows complexos.

## 🏗 Arquitetura Híbrida com Plugins

```
┌─────────────────────────────────────────┐
│           CORE ANGELINA                 │
│  - n8n (Orquestração principal)        │
│  - FastAPI (API Management)            │
│  - SQLite (Estado central)             │
└─────────────────────────────────────────┘
        │              │              │
┌───────▼──────┐ ┌─────▼──────┐ ┌─────▼──────┐
│  Plugin STT  │ │ Plugin LLM │ │Plugin Agenda│
│  - Whisper   │ │ - Local LLM│ │ - CalDAV    │
│  - Vosk      │ │ - BERT etc │ │ - SQL       │
└──────────────┘ └────────────┘ └─────────────┘
```

## 🚀 Funcionalidades Principais

### 🎤 Processamento de Áudio
- **Transcrição automática** de aulas e palestras
- Suporte a múltiplos formatos (MP3, WAV, M4A)
- Modelos locais: Whisper e Vosk

### 📚 Análise e Sumarização
- **Resumo inteligente** de conteúdos textuais
- **Identificação de conceitos-chave**
- Geração de **mapas mentais** automáticos
- Modelos locais: Llama 2, Falcon, BERT

### 📅 Gestão de Estudos
- **Organização automática** de agenda
- **Planejamento** de sessões de estudo
- **Lembretes inteligentes** baseados em conteúdo

### ✍️ Geração de Exercícios
- Criação de **questões práticas** personalizadas
- Exercícios de **revisão espaçada**
- **Simulados** baseados no conteúdo estudado

## 🛠 Stack Tecnológica

| Componente | Tecnologias |
|------------|-------------|
| **Backend** | Python, FastAPI, SQLite |
| **Orquestração** | n8n, Redis |
| **STT** | Whisper, Vosk |
| **LLM** | Llama.cpp, Transformers |
| **NLP** | NLTK, SpaCy, Gensim |
| **Armazenamento** | SQLite, ChromaDB |

## ⚡ Instalação Rápida

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/angelina.git
cd angelina

# Instalação usando Docker (Recomendado)
docker-compose up -d

# Ou instalação manual
pip install -r requirements.txt
python -m spacy download pt_core_news_sm
```

## 📋 Configuração Inicial

1. **Configure os plugins desejados:**
```bash
cp config/plugins.example.yaml config/plugins.yaml
```

2. **Inicie os serviços:**
```bash
# Serviço principal
python src/core/main.py

# n8n (em outro terminal)
n8n start
```

3. **Acesse a interface:**
   - API: http://localhost:8000/docs
   - n8n: http://localhost:5678

## 🔌 Plugins Disponíveis

### 🎙 Plugin STT
- **Whisper**: Alta precisão, requer GPU
- **Vosk**: Leve, totalmente offline

### 🧠 Plugin LLM  
- **Llama 2**: 7B/13B quantizado
- **Falcon**: Alternativa open-source
- **BERT**: Para tarefas específicas

### 📅 Plugin Agenda
- **SQLite**: Armazenamento local
- **CalDAV**: Sincronização com calendários

## 🎯 Exemplos de Uso

### Transcrição e Resumo Automático
```python
from angelina.core import Angelina

angelina = Angelina()
resultado = angelina.processar_aula(
    audio="aula_matematica.mp3",
    acao=["transcrever", "resumir", "exercicios"]
)
```

### Workflow n8n para Estudos
```json
{
  "workflow": "Processamento de Aula",
  "nodes": ["entrada_audio", "transcricao", "sumarizacao", "agendamento_revisao"]
}
```

## 🤝 Contribuição

Contribuições são bem-vindas! Veja nosso [Guia de Contribuição](CONTRIBUTING.md) para detalhes.

## 📄 Licença

Este projeto é licenciado sob a MIT License - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 🙋‍♂️ Suporte

- 📖 [Documentação Completa](docs/)
- 🐛 [Reportar Bugs](https://github.com/seu-usuario/angelina/issues)
- 💡 [Sugerir Funcionalidades](https://github.com/seu-usuario/angelina/issues)

---

**Desenvolvido com ❤️ para a comunidade de aprendizado autodirigido**

*Angelina: Sua assistente de estudos 100% local e open-source*
