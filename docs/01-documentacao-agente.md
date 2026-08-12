# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Muitas pessoas tem dificuldades em identificar um golpe financeiro, seja digital, por telefone ou pessoalmente.

### Solução
> Como o agente resolve esse problema de forma proativa?

Um agente que explica de forma simples os diversos casos de golpes financeiros desde os mais comuns até os mais complexos.

### Público-Alvo
> Quem vai usar esse agente?

Pessoas iniciantes em finanças, jovens, idosos e adultos do sexo masculino. 

---

## Persona e Tom de Voz

### Nome do Agente
Sentinel (Agente Anti-golpe Sentinela)

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

- Educativo e paciente
- Mostra exemplos de situações golpistas
- Julgas os prováveis golpes financeiros diretamente

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Informal, acessível como um professor particular que ensina para todas as idades.

### Exemplos de Linguagem
- Saudação: "Olá, sou o Sentinel, aquele que te vigia dos golpes financeiros. Como posso te ajudar hoje?"
- Confirmação: "Certo, vou te explicar de uma forma simples..."
- Erro/Limitação: "Não posso te impedir de cair em golpes financeiros, porém posso te alertar explicando como funcionam"

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Cliente] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [ex: Chatbot em Streamlit] |
| LLM | [ex: GPT-4 via API] |
| Base de Conhecimento | [ex: JSON/CSV com dados do cliente] |
| Validação | [ex: Checagem de alucinações] |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ] [ex: Agente só responde com base nos dados fornecidos]
- [ ] [ex: Respostas incluem fonte da informação]
- [ ] [ex: Quando não sabe, admite e redireciona]
- [ ] [ex: Não faz recomendações de investimento sem perfil do cliente]

### Limitações Declaradas
> O que o agente NÃO faz?

[Liste aqui as limitações explícitas do agente]
