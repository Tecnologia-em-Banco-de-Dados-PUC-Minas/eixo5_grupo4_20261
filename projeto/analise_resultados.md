ANÁLISE DE PREÇO

Foi utilizada uma base de dados de vendas da plataforma Amazon, com transações no período de 01/2022 à 12/2023.
A base de dados possui 50.000 registros e 14 variáveis (colunas), sem valores nulos, o que a princípio, tornou sua estrutura adequada para implementação das bibliotecas de análises de dados, bem como os modelos de aprendizagem.
Em uma visão estruturada, podemos extrair algumas estatísticas básicas do conjunto de dados:


<img width="886" height="263" alt="image" src="https://github.com/user-attachments/assets/dbbb8f3a-8834-4b40-acb9-d9cd9a758172" />


A análise descritiva mostrou que os preços dos produtos apresentam variação entre 5,01 e 499,99. A quantidade vendida possui média próxima de 3 unidades por pedido, indicando distribuição relativamente equilibrada das vendas. A receita média observada foi de 657,33, enquanto o lucro médio foi de 32,87.

Preço médio dos produtos       252,51
Preço mínimo	                           5,01
Preço máximo 	                           499,99
Quantidade média vendida      3 unidades
Receita média por venda           657,33
Lucro médio por venda              32,87

O gráfico de receita por categoria permitiu identificar se algum segmento apresentava maior participação no faturamento da empresa. Na base de dados analisada, podemos observar uma homogeneidade muito grande na relação entre receita e categorias de produtos. Em outras palavras, percebeu-se um forte equilíbrio nos valores vendidos com relação as diversas categorias:

Categoria	Quantidade
Beauty	25.422
Books	25.065
Electronics	24.898
Fashion	25.089
Home & Kitchen	24.743
Sports	24.753


<img width="696" height="613" alt="image" src="https://github.com/user-attachments/assets/ccc96388-c98f-4e02-a342-a26aecc08044" />


Essa igualdade também acontece no gráfico de receita por período. A distribuição relativamente uniforme da receita entre os períodos sugere estabilidade nas vendas ao longo do tempo.
Mesmo com a coluna “Normal” apresentando significativa discrepância dos demais períodos, vale ressaltar que esta coluna contempla os meses do ano que que foram considerados como datas não comemorativas. Assim, ela representa a soma de vendas de cinco meses do ano.


<img width="729" height="559" alt="image" src="https://github.com/user-attachments/assets/769cb94f-e1dd-419f-9aee-2dd0f2aae690" />

 
Acompanhando as tendencias anteriores, o gráfico de lucro por categoria também sugere que as categorias não apresentam interferências significativas no o lucro da empresa.


<img width="731" height="571" alt="image" src="https://github.com/user-attachments/assets/f7ad3a58-3399-42db-aedf-5fa4fc1c1f52" />


Modelos de Aprendizado

Modelo de Regressão Linear

Um dos modelos utilizados foi o Modelo de Regressão Linear. Tal modelo apresentou coeficiente de determinação (R²) de aproximadamente 0,505. Isso significa que apenas cerca de 50,5% da variação observada na receita total pode ser explicada pelas variáveis utilizadas no treinamento.


<img width="773" height="154" alt="image" src="https://github.com/user-attachments/assets/4c2e05db-22f3-4395-8a47-cf01e75c3d86" />


Com isso, o resultado indica capacidade preditiva moderada do modelo para com os dados utilizados, podendo sugerir que que outras variáveis não consideradas na análise também podem estar influenciando significativamente o faturamento.


<img width="696" height="118" alt="image" src="https://github.com/user-attachments/assets/dcac78ce-7392-4a1c-8774-82af6e80065f" />


Modelo Random Forest Regressor

O modelo Random Forest apresentou R² de aproximadamente 0,339, desempenho inferior ao obtido pela Regressão Linear.


<img width="696" height="144" alt="image" src="https://github.com/user-attachments/assets/7ca55c5c-449d-4ed7-a0c2-f79c97a8ba19" />


Esse resultado sugere que, como vimos nas análises exploratórias dos dados, a relação entre as variáveis utilizadas e a receita total possui comportamento relativamente linear, não justificando a maior complexidade do algoritmo Random Forest neste cenário.


<img width="696" height="103" alt="image" src="https://github.com/user-attachments/assets/7c797e4b-1d99-400a-b10e-964520c1b7d4" />


Árvore de Decisão
O modelo de Arvore de decisão estava tentando classificar as vendas em categorias:
Classe 0 = Baixa, Classe 1 = Média


<img width="707" height="124" alt="image" src="https://github.com/user-attachments/assets/b19be00c-20ef-4742-93e5-95ec48280ebb" />


Ou seja, a pergunta do modelo foi: Com base nas características do produto, ele pertence à categoria de vendas Baixa ou Média?"
Note que, o modelo está configurado para classificar também vendas consideradas na categoria “Alta”.
Porém, na base de dados, a variável quantity_sold vai apenas até 5.
Assim, a classe “Alta” não existe nos resultados.
Seguindo a análise, o modelo de Árvore de Decisão alcançou acurácia de 51,85%, indicando capacidade limitada de classificação dos níveis de venda. Observa-se melhor desempenho na identificação da classe "Baixa" em comparação à classe "Média". Os resultados sugerem que as variáveis utilizadas possuem baixo poder discriminatório para prever com precisão o nível de vendas dos produtos.


<img width="713" height="113" alt="image" src="https://github.com/user-attachments/assets/20e5de6b-5921-4c37-bbe5-40635bd5c61c" />


De maneira geral, de cada 100 produtos analisados, aproximadamente 52 foram classificados corretamente.
Em Machine Learning, isso não é considerado um resultado muito bom.
A coluna Precision = 0.60 / 0.41, significa que quando o modelo disse que uma venda era "Baixa", ele acertou 60% das vezes, já quando o modelo disse que uma venda era "Média", ele acertou apenas 41% das vezes.
A coluna Recall = 0.60 / 0.41, significa que O modelo encontrou 60% de todas as vendas realmente baixas e encontrou apenas 41% das vendas realmente médias.


<img width="631" height="241" alt="image" src="https://github.com/user-attachments/assets/e0838726-e732-4949-87db-c15622e78334" />


Matriz de Confusão

A matriz de confusão é dividida em quatro quadrantes.
1 Verdadeiros Negativos (Acerto)
São produtos que:
•	Eram realmente "Baixa"
•	O modelo previu "Baixa"

2 Falsos Positivos (Erro)
São produtos que:
•	Eram realmente "Baixa"
•	O modelo previu "Média"

3 Falsos Negativos (Erro)
São produtos que:
•	Eram realmente "Média"
•	O modelo previu "Baixa"

4 Verdadeiros Positivos (Acerto)
São produtos que:
•	Eram realmente "Média"
•	O modelo previu "Média"

Dessa forma, temos uma matriz disposta da seguinte forma:
ACERTO	ERRO
ERRO	ACERTO

Substituindo pelos resultados do modelo, temos:
14321	9659
9601	6419

Com a acurácia de 51,85%, o modelo indica desempenho limitado na tarefa de classificação dos dados. A análise da matriz de confusão mostra que a quantidade de erros é próxima à quantidade de acertos, evidenciando dificuldades do modelo em distinguir adequadamente as classes.
A classe "Baixa" apresentou melhores indicadores de precisão, recall e F1-score (0,60), enquanto a classe "Média" apresentou desempenho inferior (0,41). Esses resultados sugerem que as variáveis utilizadas possuem capacidade limitada para explicar o comportamento das vendas, sendo recomendável incluir novos atributos para melhorar o desempenho preditivo.


<img width="691" height="545" alt="image" src="https://github.com/user-attachments/assets/3d0c579d-e09a-4c69-813d-2cc2acd7f17d" />




QUANTIDADE VENDIDA

Utilizamos a mesma base de dados de vendas da plataforma Amazon, com transações no período de 01/2022 à 12/2023, citada acima.

Na análise descritiva conhecemos as variáveis categóricas e numéricas, seus comportamentos ao longo dos dois anos. 

<img width="352" height="254" alt="image" src="https://github.com/user-attachments/assets/99a0ab06-1237-460f-8b17-50f0c72540f7" />

<img width="333" height="222" alt="image" src="https://github.com/user-attachments/assets/de94c1f2-6808-498e-bf60-4fa1bad169e9" />

<img width="298" height="223" alt="image" src="https://github.com/user-attachments/assets/34e5f83a-fc83-481d-91c0-8892f0fb5747" />

<img width="640" height="354" alt="image" src="https://github.com/user-attachments/assets/888c8204-856b-4d0a-9f7c-a324224a9d70" />

Plotamos histogramas das variáveis numéricas ao longo do tempo para observarmos o comportamento de cada uma delas ao longo do período:

<img width="769" height="298" alt="image" src="https://github.com/user-attachments/assets/aed85904-5b46-4c6d-89b4-b4f77f5cfe98" />

<img width="767" height="294" alt="image" src="https://github.com/user-attachments/assets/0e5b4e3b-4000-4de7-acde-52779f89b9ae" />

Os gráficos abaixo demonstram a evolução das vendas e as sazonalidades ocorridas nos anos de 2022 e 2023:

<img width="819" height="384" alt="image" src="https://github.com/user-attachments/assets/def952bd-610c-4adf-8365-c17d27162edc" />

<img width="793" height="443" alt="image" src="https://github.com/user-attachments/assets/3f9d23af-429e-4a6a-b9ba-974107b9f18a" />

Modelos de Aprendizado

Árvore de Decisão
O modelo de árvore de decisão está classificando  a variável quantity_sold (quantidade vendida).


<img width="958" height="655" alt="image" src="https://github.com/user-attachments/assets/f342f5d6-4554-4cf7-8b9c-63467746bbbf" />

MAE (Mean Absolute Error): 1.10  
R^2 (R-squared): 0.14

Observando o topo da árvore, as features que aparecem primeiro (profit e discounted_price) são as mais importantes para a previsão de quantity_sold neste modelo. Isso significa que a quantidade vendida é primeiramente segmentada com base no lucro e no preço com desconto.

A árvore mostra que as variáveis “profit” e “discounted_price” são divisores importantes para o target “quantity_sold”. No entanto, com um max_depth=3 e um R² baixo, este modelo é bastante simples e não captura a maior parte da variabilidade na quantidade vendida. 

Random Forest

Como o Random Forest geralmente é um modelo mais robusto que a Árvore de Decisão individual, rodamos o modelo buscando um desempenho melhor, aumentando o poder preditivo. O que não ocorreu, afinal o R^2 da árvore de decisão ficou em 0.14, enquanto o do Random Forest ficou em 0.13:

<img width="694" height="272" alt="image" src="https://github.com/user-attachments/assets/2499aa0d-70bf-44cc-9acd-56701df00b6a" />

MAE (Mean Absolute Error): 1.11.
R² (R-squared): 0.13

XGBoost

<img width="711" height="272" alt="image" src="https://github.com/user-attachments/assets/13060787-479e-4bf5-b63f-f8b455f07d81" />

MAE (Mean Absolute Error): 1.13.
R² (R-squared): 0.09

Comparando o XGBoost com a Árvore de Decisão e o Random Forest:

•	Árvore de Decisão (max_depth=3): MAE de 1.10,  R² de 0.14.
•	Random Forest: MAE de 1.11,  R² de 0.13.
•	XGBoost: MAE de 1.13,  R² de 0.09.
o XGBoost obteve o pior desempenho entre os três modelos em termos de R². Um R² de 0.09 é bastante baixo, indicando que o modelo tem uma capacidade muito limitada de explicar a variação na “quantity_sold”.

Para demonstrar as diferenças encontradas plotamos um gráfico de comparação das previsões versos o real:

<img width="930" height="484" alt="image" src="https://github.com/user-attachments/assets/100698c0-2a20-48df-bb08-b54c45a798fc" />


Possíveis razões para os baixos desempenhos:

•	As nossas features não são suficientemente preditivas para prever a "quantity_sold".

•	A relação entre as features e o target (quantity_sold) é muito complexa ou não linear para ser capturada eficazmente por esses modelos, ou existem outros fatores não incluídos nos dados.

•	O modelo está subajustado (underfitting), ou seja, o modelo não aprendeu bem os padrões dos dados de treinamento e, portanto, não generaliza bem para novos dados.










