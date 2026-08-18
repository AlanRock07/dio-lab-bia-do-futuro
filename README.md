# 🤖 Finan — Educador Financeiro com IA Generativa

Agente conversacional que ensina conceitos de finanças pessoais de forma simples e didática, usando os dados do próprio cliente como exemplo prático — **sem recomendar investimentos**.

Projeto desenvolvido a partir do desafio [`dio-lab-bia-do-futuro`](https://github.com/digitalinnovationone/dio-lab-bia-do-futuro) da Digital Innovation One.

---

## 💡 O Problema

Muitas pessoas têm dificuldade em entender conceitos financeiros básicos — tipos de investimento, organização de gastos, reserva de emergência e planejamento de longo prazo.

## ✅ A Solução

O **Finan** explica esses conceitos de forma simples, do básico ao avançado, usando o histórico e o perfil do próprio cliente como exemplo. Ele **nunca recomenda onde investir**: seu papel é apenas educar.

**Público-alvo:** pessoas iniciantes em finanças pessoais, de todas as idades.

---

## 🧠 Como o Agente Funciona

| Componente | Descrição |
| --- | --- |
| Interface | [Streamlit](https://streamlit.io/) |
| LLM | Ollama (execução local) |
| Base de conhecimento | Arquivos JSON/CSV mockados na pasta `data/` |
| Validação | Regras anti-alucinação no system prompt |

```
Usuário → Interface (Streamlit) → LLM → Base de Conhecimento → Validação → Resposta
```

### Personalidade

Educado, paciente, didático e sem julgamentos sobre os gastos do cliente. Tom informal e acessível, como um professor particular.

### Regras de segurança

- Usa apenas os dados fornecidos no contexto
- Nunca recomenda investimentos específicos
- Admite quando não sabe algo, em vez de inventar
- Não acessa nem compartilha dados sensíveis (ex: senhas)

---

## 📚 Base de Conhecimento

Os dados mockados da pasta `data/` alimentam o agente:

| Arquivo | Uso |
| --- | --- |
| `perfil_investidor.json` | Personalizar respostas conforme o perfil do cliente |
| `transacoes.csv` | Analisar padrão de gastos de forma didática |
| `historico_atendimento.csv` | Dar continuidade a atendimentos anteriores |
| `produtos_financeiros.json` | Explicar produtos disponíveis (inclui Fundo Imobiliário, adicionado à base original) |

Os dados são injetados diretamente no prompt para garantir o máximo de contexto ao agente.

---

## 🗣️ Exemplos de Interação

**"O que é CDI?"**
> Explica o conceito de forma simples, relacionando com a Selic.

**"Onde estou gastando mais?"**
> Analisa as transações do cliente e aponta as maiores categorias de gasto.

**"Devo investir em ações?"**
> Explica como funciona o produto, mas não recomenda a decisão — reforça que isso cabe ao cliente.

O agente também trata bem perguntas fora de escopo (ex: previsão do tempo) e tentativas de acessar dados sensíveis de outros clientes, sempre redirecionando a conversa para finanças.

---

## 📊 Avaliação

O agente foi validado com testes estruturados cobrindo consulta de gastos, pedidos de recomendação (recusados corretamente), perguntas fora de escopo e informações inexistentes. Não foram observadas alucinações nos testes com ChatGPT, Copilot e Claude usando o mesmo system prompt — cada modelo respondeu em um estilo levemente diferente, mas dentro das regras definidas.

---

## 📁 Estrutura do Repositório

```
├── README.md
├── data/                          # Dados mockados (perfil, transações, atendimentos, produtos)
├── docs/
│   ├── 01-documentacao-agente.md  # Caso de uso, persona e arquitetura
│   ├── 02-base-conhecimento.md    # Estratégia de dados e integração
│   ├── 03-prompts.md              # System prompt, exemplos e edge cases
│   ├── 04-metricas.md             # Testes e avaliação de qualidade
│   └── 05-pitch.md                # Roteiro do pitch
└── src/                           # Código da aplicação (Streamlit + Ollama)
```

---

## 🛠️ Ferramentas Utilizadas

- **LLM:** Ollama (local)
- **Interface:** Streamlit
- **Dados:** JSON/CSV mockados

---

## 📎 Documentação Completa

Para o detalhamento de cada etapa, veja a pasta [`docs/`](./docs):
[Documentação do Agente](./docs/01-documentacao-agente.md) · [Base de Conhecimento](./docs/02-base-conhecimento.md) · [Prompts](./docs/03-prompts.md) · [Métricas](./docs/04-metricas.md) · [Pitch](./docs/05-pitch.md)
