
# 📊 Análise RFM para Segmentação de Clientes


A TechShop (empresa fictícia) é um e-commerce especializado na venda de eletrônicos, vestuário, alimentos, produtos de beleza e livros. Fundada há cinco anos, a empresa cresceu rapidamente, atendendo clientes de todo o país por meio de sua plataforma online, aplicativo e lojas físicas. Com um grande volume de pedidos diários e um público diversificado, a TechShop busca otimizar suas estratégias de marketing e retenção de clientes.

Nos últimos meses, a equipe de marketing identificou um problema: apesar do aumento no número de visitantes no site, a taxa de recompra tem diminuído. Muitos clientes compram uma única vez e não retornam, enquanto outros realizam compras recorrentes, mas não recebem um tratamento diferenciado. Essa falta de segmentação gera campanhas genéricas, com baixo retorno sobre investimento (ROI).

Diante desse cenário, a TechShop decidiu implementar um modelo de análise RFM (Recency, Frequency, Monetization) para entender melhor o comportamento dos clientes e personalizar suas campanhas de marketing.

# Objetivos

Este projeto tem como objetivo analisar o comportamento de compra dos clientes da TechShop utilizando a metodologia RFM, classificando-os em diferentes segmentos com base em sua recência, frequência e valor monetário gasto.

A partir dessa análise, a empresa poderá:

✅ Identificar clientes de alto valor e direcionar ofertas exclusivas para aumentar a fidelização.

✅ Reconhecer clientes inativos e criar estratégias para reengajá-los.

✅ Personalizar campanhas de marketing de acordo com o perfil de cada grupo de clientes.

✅ Otimizar o orçamento de marketing, garantindo que os recursos sejam aplicados nos segmentos mais estratégicos.
Com essa abordagem baseada em dados, a TechShop espera aumentar a taxa de retenção, melhorar o relacionamento com os clientes e, consequentemente, impulsionar as vendas.

# Passo a Passo 

#### 📌 Passo 1: Tratamento Inicial e Cálculo do Recency

1️.1 Remoção da Hora da Compra:

•	Ajustei a coluna "Data da Compra", removendo a informação de hora para manter apenas a data.

2️ Criação do ID Único de Cliente:

•	Copiei a coluna "ID Cliente" e removi as duplicatas, garantindo uma lista única de clientes para análise posterior.

3️ Cálculo do Recency (R):

•	Criei uma nova coluna chamada "Última Compra", onde identifiquei a data mais recente de compra para cada cliente.

•	Para isso, utilizei a função MÁXIMOSES, permitindo automatizar o processo ao buscar a maior (mais recente) data dentro do intervalo de compras do cliente.

4️ Atribuição das Notas de Recency:

Após calcular a última compra de cada cliente, classifiquei-os com notas de 1 a 5 com base no tempo decorrido desde essa compra:

*	5 → Última compra em até 30 dias
*	4 → Última compra entre 31 e 90 dias
*	3 → Última compra entre 91 e 180 dias
*	2 → Última compra entre 181 e 360 dias
*	1 → Última compra há mais de 360 dias


#### 📌 Passo 2: Cálculo da Frequência de Compras (Frequency - F)

1️ Criação da Coluna de Frequência:

•	Analisei o histórico de compras de cada cliente para calcular quantas vezes ele comprou ao longo do período analisado.

•	Para isso, utilizei a função CONT.VALORES ou CONT.SES no Excel, somando o número de compras para cada ID Cliente.

2️ Atribuição das Notas de Frequency:

Baseado no total de compras, atribuí notas de 1 a 5:

*	5 → Clientes com 7 ou mais compras
*	4 → Clientes com 5 a 6 compras
*	3 → Clientes com 3 a 4 compras
*	2 → Clientes com 2 compras
*	1 → Clientes com 1 única compra

#### 📌 Passo 3: Cálculo do Valor Monetário (Monetization - M)

1️ Cálculo do Faturamento Total por Cliente:

Criei uma nova coluna para calcular o total gasto por cada cliente ao longo do tempo.

Para isso, utilizei a função SOMASE no Excel, somando os valores de compra para cada ID Cliente.

2️ Atribuição das Notas de Monetization:

Classifiquei os clientes em 5 categorias com base no faturamento total:

*	5 → Clientes que gastaram acima de R$3.500
*	4 → Clientes com gastos entre R$2.500 e R$3.499
*	3 → Clientes com gastos entre R$1.500 e R$2.499
*	2 → Clientes com gastos entre R$500 e R$1499
*	1 → Clientes que gastaram menos de R$500

#### 📌 Passo 4: Cálculo do Score Final e Classificação dos Clientes

1️ Cálculo do Score Total (Média Ponderada):

Para definir a nota total, utilizei uma média ponderada, atribuindo pesos diferentes para cada métrica RFM:

*	Recency (R): 20%
*	Frequency (F): 40%
*	Monetization (M): 40%
*	A fórmula utilizada no Excel foi:
    
            = (D2 * 0.2) + (E2 * 0.4) + (F2 * 0.4)

Onde:

*	D2 = Nota de Recência
*	E2 = Nota de Frequência
*	F2 = Nota de Monetização

2️ Classificação dos Clientes:

Após calcular o score total, classifiquei os clientes em três segmentos principais:
*	Inativo → Nota ≤ 3
*	Regular → Nota entre 3 e 4
*	VIP → Nota ≥ 5



#### 📌 Passo 5: Visualização e Segmentação de Dados no Power BI

Após o tratamento dos dados no Excel, seguimos para a visualização e segmentação utilizando o Power BI, onde foram criados diversos gráficos e painéis interativos para facilitar a análise do comportamento dos clientes.

Os principais elementos desenvolvidos no Power BI foram:

1️⃣ Resumo Geral

Total de clientes cadastrados na base de dados.
Faturamento total gerado por todas as compras.
Ticket médio dos clientes, representando o valor médio gasto por cliente.

2️⃣ Segmentação de Clientes

Gráfico de barras exibindo a quantidade de clientes classificados como Inativos, Regulares e VIPs, conforme o modelo RFM.
Filtro de Data permitindo selecionar períodos específicos para análise de compras e clientes ativos.

3️⃣ Análises Geográficas e de Categoria

Mapa de Concentração de Clientes, identificando regiões com maior número de compras.
Gráfico de Colunas com Quantidade de Compras por Categoria, destacando os produtos mais adquiridos e os segmentos mais rentáveis.



![image](https://github.com/user-attachments/assets/5b5b616b-560e-46b6-938e-6f47ab26373b)



Com essa estrutura, permitiu uma análise completa e interativa, possibilitando a criação de estratégias de retenção e campanhas personalizadas para cada segmento de cliente.
## Tecnologias Utilizadas


![image](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![image](https://img.shields.io/badge/PowerBI-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=white)
