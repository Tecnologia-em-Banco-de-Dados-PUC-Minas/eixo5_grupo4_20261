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
