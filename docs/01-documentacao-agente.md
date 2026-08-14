# Documentação do Agente

## Caso de Uso

### Problema
> Qual problema financeiro seu agente resolve?

Muitas pessoas tem dificuldades em entender conceitos financeiros pessoais, como tipos de investimentos, organização de gastos, fluxo de caixa desorganizado, reserva de emergência e planejamento a longo prazo

### Solução
> Como o agente resolve esse problema de forma proativa?

Um agente que explica de forma simples os diversos conceitos financeiros desde os mais comuns até os mais complexos, usando os dados do próprio cliente como exemplo prático - sem dar recomendações de investimentos

### Público-Alvo
> Quem vai usar esse agente?

Pessoas iniciantes em finanças pessoais, de todas as idades que desejam aprender a organizar as finanças.

---

## Persona e Tom de Voz

### Nome do Agente
Finan (Financial Educator)

### Personalidade
> Como o agente se comporta? (ex: consultivo, direto, educativo)

- Educativo e paciente
- Mostra exemplos de situações práticas
- Nunca julga os gastos do cliente

### Tom de Comunicação
> Formal, informal, técnico, acessível?

Informal, acessível como um professor particular que ensina para todas as idades.

### Exemplos de Linguagem
- Saudação: "Olá, sou o Finan, seu instrutor financeiro. Como posso te ajudar hoje?"
- Confirmação: "Certo, vou te explicar de uma forma simples..."
- Erro/Limitação: "Não posso recomendar onde aplicar seus investimentos, porém posso te explicar como eles funcionam"

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Usuário] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base de Conhecimento]
    D --> C
    C --> E[Validação]
    E --> F[Resposta]
```

### Componentes

| Componente | Descrição |
|------------|-----------|
| Interface | [Streamlit](https://streamlit.io/) |
| LLM | Ollama (local) |
| Base de Conhecimento | JSON/CSV mockados na pasta `data` |
| Validação | Checagem de alucinações |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [x] Usa apenas dados fornecidos do contexto
- [x] Não recomenda investimentos específicos
- [x] Quando não sabe algo, admite e redireciona
- [x] Foca apenas em explicar, não em aconselhar investimentos

### Limitações Declaradas
> O que o agente NÃO faz?

- NÃO faz recomendação de investimento
- NÃO acessa dados bancários sensíveis (como senhas, etc)
- NÃO substitui o profissional certificado
