# 📊 NovaTech Retail — Análise de Vendas 2024

Projeto de análise de dados de vendas da NovaTech Retail, cobrindo limpeza, organização, criação de tabelas dinâmicas e extração de insights estratégicos a partir de 1.000 registros reais de 2024.

---Link do dado limpo e analisado aqui: https://docs.google.com/spreadsheets/d/1u5Stms85ph6zAISEDUH8WkqZGMjHardsgh6AeYu4TmA/edit?usp=sharing

## 🗂️ Estrutura do Repositório

```
📁 novatech-sales-analysis
├── README.md                           ← você está aqui
├── relatorio vendas novatech retail.md   ← análise completa com insights
└── company_sales_dataset.xlsx          ← dataset original
└── clean_sales_data.csv         ← dado limpo
└── Graficos                       ←Prints dos Graficos
```

---

## 🎯 Objetivo

Organizar, limpar e analisar um dataset de vendas bagunçado (como acontece no mundo real) para responder perguntas de negócio como:

- Qual mês teve maior faturamento?
- Qual categoria vende mais?
- Qual canal gera mais receita?
- Existe algum estado que se destaca?
- Existe problema de cancelamento?

---

## 🛠️ Ferramentas Utilizadas

- **Google Sheets** — limpeza, organização, tabelas dinâmicas e gráficos
  

---

## 🧹 Etapas do Projeto

### 1. Limpeza dos Dados
Identificação e correção de problemas no dataset original:

| Problema | Solução |
|---|---|
| 3 formatos de data diferentes | Padronizado para `dd/mm/aaaa` |
| 182 registros com quantity negativa | Convertido com `=ABS()` |
| 188 registros sem canal de venda | Preenchido com `"Não Informado"` |
| Métodos de pagamento inconsistentes | Padronizado com `=PROPER()` |
| 205 registros sem vendedor | Preenchido com `"Não Informado"` |
| Status `"completed"` em inglês | Convertido para `"Concluído"` |

### 2. Organização
- Dados limpos organizados na aba `clean_sales_data`
- Colunas calculadas adicionadas: `total_sale`, `month`, `weekday`

### 3. Tabelas Dinâmicas (Pivot Tables)
- Faturamento por mês
- Faturamento por categoria
- Faturamento por canal de venda
- Faturamento por estado
- Status dos pedidos (cancelamentos e devoluções)

### 4. Gráficos
- Linha — faturamento mensal
- Barras — vendas por categoria
- Pizza — vendas por canal
- Barras — vendas por estado
- Pizza — status dos pedidos

---

## 📈 Principais Resultados

| Indicador | Resultado |
|---|---|
| Faturamento Total | R$ 6.744.741,94 |
| Melhor mês | Março (R$ 619.472,32) |
| Categoria líder | Fotografia (R$ 1.215.245,53) |
| Canal líder | Aplicativo (R$ 1.248.021,59) |
| Estado líder | SC — R$ 858.607,26 |
| Taxa de conclusão | ⚠️ apenas 47,9% |

> 🚨 **Principal alerta:** 52,1% dos pedidos foram cancelados ou devolvidos. Resolver esse problema pode gerar mais de R$ 3 milhões adicionais ao ano.


---

## 👤 Autor

**Matheus**  
Projeto desenvolvido como parte de um desafio de análise de dados para a NovaTech Retail(empresa ficticia) com ajuda de IA.
