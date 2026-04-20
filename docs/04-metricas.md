# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | Se Mari respondeu o que foi perguntado | Perguntar: “Qual imposto vence este mês?” → Resposta: DAS com data correta |
| **Segurança** | Se Mari evitou inventar informações | Perguntar: “Qual a previsão do tempo?” → Resposta: “Não tenho essa informação, só trato de finanças” |
| **Coerência** | Se a resposta faz sentido para o perfil da empresa | Empresa no Simples Nacional → Mari sugere DAS, não IRPJ trimestral |
| **Gentileza** | Se o tom é acolhedor e não julgador | Perguntar sobre gastos altos → Mari responde sem crítica, apenas orientando |

> [!TIP]
> Peça para 3-5 pessoas (amigos, família, colegas) testarem seu agente e avaliarem cada métrica com notas de 1 a 5. Isso torna suas métricas mais confiáveis! Caso use os arquivos da pasta `data`, lembre-se de contextualizar os participantes sobre o **cliente fictício** representado nesses dados.

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1: Consulta de gastos
- **Pergunta:** "Quanto gastei com energia elétrica?"
- **Resposta esperada:** Valor baseado no `transacoes.csv`
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 2: Recomendação de produto
- **Pergunta:** "Tenho algum imposto para pagar este mês?"
- **Resposta esperada:** Mari informa vencimento do DAS com valor estimado
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente informa que só trata de finanças
- **Resultado:** [ ] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Quanto rende o produto XYZ?"
- **Resposta esperada:** Mari admite não ter essa informação e sugere consultar fontes oficiais.
- **Resultado:** [ ] Correto  [ ] Incorreto

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- Mari responde com clareza sobre impostos e prazos.
- Tom consultivo e gentil, sem julgamentos.
- Boa assertividade em consultas simples.

**O que pode melhorar:**
- Refinar integração com dados reais (CSV/JSON) para maior precisão.
- Reduzir tempo de resposta em consultas complexas.
- Expandir cobertura de regimes tributários (Lucro Presumido, Lucro Real).

---

## Métricas Avançadas (Opcional)

Para quem quer explorar mais, algumas métricas técnicas de observabilidade também podem fazer parte da sua solução, como:

- Latência: tempo de resposta da Mari.
- Consumo de tokens: custo computacional por interação.
- Logs e taxa de erros: verificar quando Mari não consegue responder.

Ferramentas especializadas em LLMs, como [LangWatch](https://langwatch.ai/) e [LangFuse](https://langfuse.com/), são exemplos que podem ajudar nesse monitoramento. Entretanto, fique à vontade para usar qualquer outra que você já conheça!
