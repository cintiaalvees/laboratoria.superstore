# 🛒 Diagnóstico de Rentabilidade Logística — SuperStore

> **Projeto 2 — Análise de Dados | Bootcamp Laboratoria**
> Análise de 19.961 pedidos para identificar quais categorias e modos de envio comprometem a rentabilidade da SuperStore — e onde estão as perdas financeiras reais.

---

## 📌 Sobre o projeto

A SuperStore não sabia quais categorias e modos de envio comprometiam sua rentabilidade. Decisões eram tomadas sem dados concretos. Este estudo de caso cruza dados de pedidos e logística para responder onde estão as perdas, qual categoria opera no prejuízo e qual modal de envio destrói margem.

**Perguntas respondidas:**
1. Existem categorias com prejuízo real?
2. Onde estão as perdas financeiras?
3. Qual modal de envio compromete a margem?

---

## 🗂️ Estrutura do repositório

```
superstore-analise/
├── 📁 data/
│   ├── superstore_order_-_superstore_order.xlsx       ← base original de pedidos (19.961 linhas)
│   ├── superstore_shipping_-_superstore_shipping.xlsx ← base original de envios
│   └── superstore_ordershipping_final.xlsx            ← base combinada e limpa (Order + Shipping)
├── 📁 docs/
│   ├── Apresentacao_CintiaAlves_RotaA_Projeto2.pdf    ← apresentação completa do projeto
│   └── Dashboard_SuperStore.pdf                       ← versão estática do dashboard
└── README.md
```

---

## 🔗 Dashboard interativo

👉 [Acesse o painel no Looker Studio](https://datastudio.google.com/reporting/dd9030df-ac89-4d80-b6d8-6c14558fd375)
📄 [Versão PDF estática](docs/dashboard_superstore.pdf)

---

## 🛠️ Ferramentas utilizadas

| Ferramenta | Uso |
|---|---|
| Google BigQuery | Limpeza, tratamento e modelagem dos dados via SQL |
| SQL | Remoção de duplicatas, correção de tipos, JOIN entre tabelas |
| Looker Studio | Visualização e dashboard interativo |
| Claude & Gemini | Apoio na análise e documentação |

---

## 📋 Etapas do projeto

**1. Coleta**
Duas tabelas independentes: `superstore_order` (19.961 linhas, 15 variáveis — order_id, category, country, profit, sales...) e `superstore_shipping` (dados logísticos complementares, 5 variáveis-chave — ship_mode, shipping_cost, ship_date...).

**2. Limpeza (SQL no BigQuery)**
- 22 valores ausentes em `Sales` → mantidos (distribuição aleatória, sem padrão geográfico)
- 32 registros duplicados removidos com `ROW_NUMBER()`
- Categorias padronizadas (sem inconsistências)
- Campo `profit` corrigido: `STRING` → `FLOAT64 ÷ 1000`
- `LEFT JOIN` final unindo Order + Shipping por `order_id`

**3. Análise**
Evolução temporal do lucro por categoria (2023–2024), lucro por modal de envio dentro da categoria Furniture, e diagnóstico do padrão estrutural de perdas.

**4. Visualização**
Dashboard no Looker Studio com gráfico de linhas por categoria, barras de lucro por modal de envio e painel de diagnóstico financeiro.

---

## 💡 Principais insights

**🚨 Furniture em crise**
Única categoria com resultado negativo recorrente em todo o período 2023–2024. O problema não é pontual — é estrutural.

**📈 Technology cresce de forma consistente**
Única categoria com crescimento sólido e margem positiva ao longo dos dois anos analisados.

**⚠️ Second Class = perda**
Modal intermediário com o pior resultado financeiro da categoria Furniture. A SuperStore absorve custos elevados de envio sem repassá-los ao cliente.

**✅ Same Day é o único modal eficiente**
Único modo de envio com margem positiva em Furniture — porque o cliente absorve o custo.

**📌 Padrão estrutural, não sazonalidade**
Comportamento consistente em 2023–2024 confirma que as perdas são um problema de modelo, não de época do ano.

---

## ✅ Conclusão

**A rentabilidade da SuperStore está sendo comprometida por Furniture + Second Class.**
A presença em múltiplos mercados amplifica o prejuízo sem que haja repasse de custo ao cliente.

**Recomendações:**
1. Suspender temporariamente o Second Class para itens volumosos de Furniture nos mercados deficitários
2. Forçar o cliente a escolher entre Standard Class (prazo maior) ou First Class (custo real repassado)

---

## 📄 Documentação

A apresentação completa com contexto, análises e recomendações está disponível em [`docs/Apresentacao_CintiaAlves_RotaA_Projeto2.pdf`](docs/Apresentacao_CintiaAlves_RotaA_Projeto2.pdf).

---

<p align="center">
  Desenvolvido por <strong>Cintia Alves</strong> &nbsp;·&nbsp;
  <a href="https://www.linkedin.com/in/">LinkedIn</a> &nbsp;·&nbsp;
  Bootcamp de Dados/IA — <strong>Laboratoria</strong>
</p>
