Problema

A modalidade de comércio no meio digital é um dos canais e alternativas mais utilizados atualmente, e fundamental para qualquer empresa que deseja aumentar, expandir e alavancar seu alcance de vendas em níveis nacionais e internacionais. 
Empresas de e-commerce como a Amazon, que realizam milhares de transações diariamente nesse modelo, precisam de uma gestão cada vez mais precisa, eficiente e que abranja o maior número possível de dados, buscando antecipar o comportamento das vendas ao longo do tempo para apoiar decisões estratégicas como gestão de estoque, planejamento de campanhas promocionais e definição de preços.
Entretanto, o volume de vendas pode variar de acordo com sazonalidade, comportamento regional dos consumidores, estratégias de desconto e características dos produtos.
Diante disso, torna-se relevante investigar como fatores temporais e características dos produtos influenciam a quantidade de unidades vendidas, bem como desenvolver um modelo capaz de prever esse comportamento.

Contexto

O conjunto de dados utilizados (dataset) neste projeto consiste em um compilado de transações de vendas do e-commerce da Amazon, no período de 2022 e 2023, disponível na plataforma Kaggle.
Ele contém aproximadamente 50.000 registros de transações ao longo desse período, que inclui informações pertinentes às transações como categoria do produto, preço, quantidades vendidas, regiões, formas de pagamento, dentre outras.

A escolha da base justifica-se adequada devido a diversos fatores, dentre eles:

•	Contém variáveis relevantes para análise de negócios;

•	Permite aplicar modelos de análise estatística e machine learning;

•	Possibilita identificar métricas e requisitos importantes como padrões de consumo, receita e lucratividade;

•	Identificar desempenho de vendas por categoria de produto;

•	Impacto de descontos nas vendas;

•	Comportamento de compra por região;

•	Relação entre avaliações e volume de vendas.


A presença da variável temporal (order_date) permite investigar padrões sazonais de vendas, possibilitando análises relacionadas à evolução das vendas ao longo do tempo.


Objetivo Geral

Realizar uma análise exploratória dos dados e desenvolver um modelo inicial de machine learning capaz de prever a quantidade de unidades vendidas (quantity_sold) considerando fatores temporais e características dos produtos.

Objetivos Específicos

•	Investigar padrões temporais nas vendas, identificando possíveis comportamentos sazonais;

•	Analisar a relação entre descontos aplicados e volume de vendas e na receita total;

•	Avaliar se categorias de produtos apresentam padrões distintos de vendas ao longo do tempo;

•	Explorar a influência de avaliações e número de reviews no desempenho comercial;

•	Verificar quais métodos de pagamento são mais utilizados;

•	Avaliar diferenças de comportamento de compra entre regiões;

•	Construir um modelo inicial de regressão capaz de prever a quantidade de unidades vendidas.
