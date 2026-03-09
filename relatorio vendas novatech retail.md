# 📊 Relatório de Análise de Vendas 2024
**Empresa:** NovaTech Retail | **Área:** Inteligência de Negócios  
**Elaborado por:** Matheus | **Data:** Março 2025

---

## 1. Sumário Executivo

Este relatório apresenta a análise completa dos dados de vendas da NovaTech Retail referentes ao ano de 2024, contemplando **1.000 registros de transações**. O trabalho envolveu etapas de limpeza, padronização, organização dos dados e extração de insights estratégicos por meio de tabelas dinâmicas e visualizações.

### 🔢 Principais Indicadores

| Indicador | Valor |
|---|---|
| 💰 Faturamento Total | R$ 6.744.741,94 |
| 📅 Melhor Mês | Março — R$ 619.472,32 |
| 🏆 Top Categoria | Fotografia — R$ 1.215.245,53 |
| 📱 Top Canal | Aplicativo — R$ 1.248.021,59 |
| 🗺️ Top Estado | SC — R$ 858.607,26 |
| ⚠️ Taxa de Problemas | 52,1% (cancelamentos + devoluções) |

---

## 2. Limpeza e Padronização dos Dados

Os dados originais apresentavam diversas inconsistências típicas de ambientes reais. Abaixo estão os problemas identificados e as correções aplicadas:

| Problema | Qtd Afetados | Solução Aplicada |
|---|---|---|
| 3 formatos de data diferentes | 1.000 linhas | Padronizado para `dd/mm/aaaa` |
| Quantity com valores negativos | 182 registros | Convertido com `=ABS()` |
| Sales Channel vazio | 188 registros | Preenchido com `"Não Informado"` |
| Payment Method inconsistente | ~300 registros | Padronizado com `=PROPER()` |
| Seller Name vazio | 205 registros | Preenchido com `"Não Informado"` |
| Order Status em inglês | 254 registros | `"completed"` → `"Concluído"` |

### Colunas Calculadas Adicionadas

Após limpeza, os dados foram organizados na aba `clean_sales_data` com as seguintes colunas novas:

- `total_sale` = `quantity_clean × unit_price`
- `month` = número do mês extraído da data (`=MÊS()`)
- `weekday` = dia da semana extraído da data (`=TEXTO(...;"dddd")`)

---

## 3. Análise de Faturamento

### 3.1 Faturamento por Mês

| Mês | Faturamento | |
|---|---|---|
| Janeiro | R$ 565.127,17 | |
| Fevereiro | R$ 606.347,64 | |
| **Março** | **R$ 619.472,32** | 🏆 Maior |
| Abril | R$ 582.650,21 | |
| Maio | R$ 551.185,47 | |
| Junho | R$ 594.787,51 | |
| Julho | R$ 549.667,37 | |
| Agosto | R$ 538.550,23 | |
| Setembro | R$ 553.114,01 | |
| Outubro | R$ 555.478,85 | |
| Novembro | R$ 542.010,38 | |
| **Dezembro** | **R$ 486.350,78** | ⚠️ Menor |

> **Insight:** Março foi o pico do ano (R$ 619k) e dezembro o pior mês (R$ 486k). A queda no fim do ano é preocupante pois contraria o padrão do varejo — dezembro costuma ser o mês mais forte. Isso pode indicar problemas com estoque, campanhas ou alta taxa de cancelamentos nesse período.

---

### 3.2 Faturamento por Categoria

| Categoria | Faturamento |
|---|---|
| **Fotografia** | **R$ 1.215.245,53** |
| Celulares | R$ 1.139.710,64 |
| Tablets | R$ 1.134.260,59 |
| Acessórios | R$ 1.133.655,63 |
| Áudio | R$ 1.079.209,89 |
| Informática | R$ 1.042.659,66 |

> **Insight:** Fotografia lidera com R$ 1,21M, mas o portfólio é bastante equilibrado — a diferença entre a primeira e a última categoria é de apenas ~16%, o que indica distribuição saudável das vendas.

---

### 3.3 Faturamento por Canal de Venda

| Canal | Faturamento | % |
|---|---|---|
| Não Informado | R$ 1.295.499,94 | 19,2% |
| **Aplicativo** | **R$ 1.248.021,59** | **18,5%** |
| Marketplace | R$ 1.118.896,39 | 16,6% |
| E-commerce | R$ 1.079.295,94 | 16,0% |
| Televendas | R$ 1.069.874,99 | 15,9% |
| Loja Física | R$ 933.153,09 | 13,8% |

> **Insight:** O maior grupo é "Não Informado" (19,2%) — uma lacuna crítica nos dados que precisa ser corrigida. Entre os canais identificados, o **Aplicativo lidera** com R$ 1,24M. A Loja Física tem o menor desempenho, sugerindo oportunidade de investimento nos canais digitais.

---

### 3.4 Faturamento por Estado

| Estado | Faturamento |
|---|---|
| **SC — Santa Catarina** | **R$ 858.607,26** |
| GO — Goiás | R$ 843.587,83 |
| PR — Paraná | R$ 772.100,20 |
| MG — Minas Gerais | R$ 751.640,97 |
| RS — Rio Grande do Sul | R$ 745.456,12 |
| PE — Pernambuco | R$ 737.964,85 |
| RJ — Rio de Janeiro | R$ 715.765,35 |
| SP — São Paulo | R$ 681.762,97 |
| BA — Bahia | R$ 637.856,39 |

> **Insight:** Santa Catarina e Goiás lideram surpreendentemente à frente de São Paulo, historicamente o maior mercado do Brasil. Vale investigar o que diferencia esses estados — pode haver concentração de grandes clientes ou estratégias regionais mais eficazes.

---

## 4. ⚠️ Análise de Cancelamentos e Devoluções

| Status | Qtd Pedidos | % |
|---|---|---|
| ✅ Concluído | 479 | 47,9% |
| ❌ Cancelado | 265 | 26,5% |
| 🔄 Devolvido | 256 | 25,6% |

### 🚨 ALERTA: Problema Grave Identificado

Apenas **47,9% dos pedidos foram concluídos com sucesso**. Mais da metade (52,1%) representa cancelamentos ou devoluções — ou seja, não geraram receita efetiva.

**Possíveis causas a investigar:**
- Problemas na qualidade dos produtos (alto índice de devoluções)
- Prazo de entrega não cumprido
- Divergência entre produto anunciado e entregue
- Problemas com meios de pagamento
- Processo de compra com fricção excessiva

---

## 5. Recomendações Estratégicas

### 🔴 Ações Imediatas
- Investigar as causas dos cancelamentos (26,5%) e devoluções (25,6%) — **prioridade máxima**
- Regularizar o preenchimento do canal de venda (19,2% sem identificação)
- Criar campanhas específicas para reverter a queda de dezembro

### 🟢 Oportunidades de Crescimento
- Investir no canal **Aplicativo**, que lidera entre os canais identificados
- Replicar as estratégias de SC e GO nos demais estados
- Criar campanhas sazonais para os meses de menor desempenho (ago., nov., dez.)
- Expandir o portfólio de **Fotografia**, categoria líder em receita

---

## 6. Conclusão

A análise dos dados de 2024 revela um negócio com faturamento equilibrado entre categorias e canais, mas com um **problema estrutural crítico**: mais da metade dos pedidos não são concluídos com sucesso.

> Se a taxa de conclusão aumentar de **47,9% para 70%**, o impacto seria superior a **R$ 3 milhões adicionais ao ano** — sem necessidade de aumentar o volume de pedidos.

Resolver o problema de cancelamentos e devoluções é, sem dúvida, a maior alavanca de crescimento disponível para a NovaTech Retail em 2025.

---

*Relatório gerado com base em 1.000 registros do dataset `company_sales_dataset.xlsx` após limpeza e padronização completa dos dados.*
