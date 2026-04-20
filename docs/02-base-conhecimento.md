# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
| --- | --- | --- |
| ``historico_atendimento.csv`` | CSV | Contextualizar interações anteriores com o empresário (ex: dúvidas já respondidas, alertas enviados). |
| ``perfil_empresa.json`` | JSON | Guardar informações sobre porte da empresa, regime tributário (Simples, Lucro Presumido, Lucro Real) e setor de atuação. |
| ``obrigacoes_fiscais.json`` | JSON | Listar prazos e tipos de impostos aplicáveis (ISS, ICMS, IRPJ, CSLL, DAS etc.). |
| ``transacoes_pj.csv`` | CSV | Analisar fluxo de caixa, entradas e saídas da conta PJ, sem julgamento de gastos. |
| ``alertas_contabeis.csv`` | CSV | Histórico de lembretes enviados (ex: vencimento de impostos, necessidade de provisionamento). |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Expansão dos dados mockados para incluir regimes tributários brasileiros.

Inclusão de campos específicos para prazos fiscais (ex: vencimento do DAS, IRPJ trimestral).

Normalização dos dados de transações para diferenciar entradas recorrentes (ex: vendas) de saídas obrigatórias (ex: impostos, folha de pagamento).

Criação de categorias de alertas (ex: “Impostos”, “Folha”, “Obrigações acessórias”) para facilitar a consulta.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Como os dados são carregados?
Os arquivos JSON/CSV são carregados no início da sessão.

Dados do cliente são incluídos no contexto do prompt para personalizar respostas.

Integração dinâmica com APIs oficiais (Receita Federal, SEFAZ) para manter prazos e regras atualizadas.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Informações críticas (perfil da empresa, regime tributário, prazos fiscais) entram no system prompt para orientar o tom e a precisão.

Transações e histórico são consultados dinamicamente conforme a interação, para gerar recomendações personalizadas e proativas.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados da Empresa:
- Nome: Padaria Pão Quente Ltda
- Regime Tributário: Simples Nacional
- Setor: Alimentação
- Porte: Pequena Empresa

Últimas transações:
- 05/04: Venda balcão - R$ 2.500
- 06/04: Compra de insumos - R$ 1.200
- 07/04: Pagamento de energia - R$ 800

Obrigações fiscais próximas:
- DAS Simples Nacional: vencimento em 20/04 - estimado R$ 1.500
- Folha de pagamento: vencimento em 30/04 - estimado R$ 5.000

Alertas anteriores:
- 15/03: Lembrete de provisionamento para folha
...
```
