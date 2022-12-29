# PREVISÃO DE VENDAS DA REDE DE DROGARIAS ROSSMANN

<img src="https://github.com/jefferson-datascience/project_rossmann/blob/main/img/rossmann-logo.png" alt="logo" style="zoom:100%;" />

O projeto tem como objetivo realizar a previsão do volume de vendas das próximas 6 semanas de cada loja da Rede Rossmann. Para o projeto ser executado, os dados foram obtidos e coletados do desafio "Rossmann Store Sales" da plataforma Kaggle.

O contexto de negócio é fictício. Todavia, o planejamento, execução, desenvolvimento e implementação da solução seguem todos os passos de um projeto real.

## QUESTÃO DE NEGÓCIO

A Rossmann é uma rede de Drogarias Europeia em que o seu principal faturamento vem das vendas de comésticos e medicamentos. O CFO da Rossmann tem como objetivo montar um budget para a reforma das lojas. Assim, para tomar a melhor decisão na obtenção do budget, o CFO solicitou ao Cientista de Dados da empresa para realizar a previsão das vendas nas próximas 6 semanas das lojas da Rede.

## PLANEJAMENTO DA SOLUÇÃO
### Qual é a solução?
  A solução para esse problema de negócio é um aprendizado de máquina que faça a previsão de vendas das próximas 6 semanas.
  
### Como será o produto final?
  Será entregue um BOT no Telegram para que o CFO possa ter as informações das vendas das próximas 6 semanas das lojas. Com isso, o CFO pode ter acesso a esses dados de qualquer lugar no momento em que ele precise bastando apenas ter um dispositivo(smartphone, tablet ou notebook) em mãos. Além disso, como subproduto será entregue um relatório com os principais insights gerados.
  A API estará hospedada na plataforma HEROKU e está disponível no seguinte link: [<img alt="Telegram" src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white"/>](http://t.me/predict_sales_rossmann_bot)

  
  
## ESTRATÉGIA DE RESOLUÇÃO

**1º Passo. Descrição dos Dados:** Realização da limpeza dos dados e construção das métricas estatíticas com intuito de ter uma visão mais holística do modelo de negócio e tomar melhores decisões ao longo do projeto.
  
**2º Passo. Feature Engineering:** Aprofundar o conhecimento sobre os atributos do conjunto de dados fornecidos e derivar novas features para ajudar na construção do modelo. Como subproduto, obter uma lista de hipóteses com o propósito de gerar insights para o time de negócios.

**3º Passo. Filtragem:** Filtragem dos dados para a o aprendizado do modelo.
  
**4º Passo. Análise Exploratória de Dados:** Validação e desvalidação das hipóteses com o objetivo de gerar insights, compreensão da correlação das variáveis e qual o impacto delas no modelo, e, entendimento do comportamento da variável resposta sobre as outras variáveis.

**5º Passo. Preparação dos Dados:** Redimensionamento de variáveis numéricas e encoding de variáveis categóricas para que os modelos de aprendizado de máquina possam aprender o comportamento específico.
  
**6º Passo. Feature Selection:** Seleção das variáveis mais relevantes para o aprendizado do modelo.
  
**7º Passo. Machine Learning Models:** Treinamento dos modelos de Machine Learning, aplicação do cross-validation e escolha do melhor modelo.

**8º Passo. Hiperparâmetros Fine Tunning:** Escolha dos melhores parâmetros para refinamento do modelo escolhido na etapa anterior.

**9º Passo. Tradução e Interpretação do Erro:** Conversão do desempenho do modelo em resultados para o negócio.
  
**10º Passo. Deploy do Modelo para Produção:** Publicação do modelo em produção para que o CFO e o time de negócio possam usar o serviço de qualquer lugar. 

## PRINCIPAIS INSIGHTS

**HIPÓTESE 1** - Lojas com maior sortimento vendem mais.

**FALSA**: Lojas com maior sortimento não vendem mais. Na verdade, lojas com sortimentos 'basic' e 'extended' vendem muito mais que o 'extra'

**HIPÓTESE 2** - Lojas com competidores mais próximos deveriam vender menos.

**FALSA**: Lojas com competidores mais próximos vendem mais. As lojas que estão em um raio de até 4km de distância tem um dos maiores volumes de vendas.

**HIPÓTESE 3** - Lojas com competidores à mais tempo deveriam vender mais.

**FALSA**: Lojas com competidores à mais tempo vendem menos.

**HIPÓTESE 9** - Lojas deveriam vender mais no segundo semetre do ano.

**FALSA**: Lojas vendem menos no segundo semestre do ano.

# MODELOS DE MACHINE LEARNING UTILIZADOS

Para a escolha do melhor algoritmo de Machine Learning, nós usamos os seguintes modelos:

* Linear Regression Model
* Linear Regression Regularized Model - Lasso
* Random Forest Regressor
* XGBoost Regressor

## Real Performance - Cross Validation

|  MODEL NAME  |  MAE CV	|   MAPE CV	 |   RMSE CV  |
|--------------|----------|------------|------------|
|Random Forest Regressor|	 747.19+/-134.35 | 0.11+/-0.02 | 1126.12+/-203.85 |
|	  Linear Regression   | 2081.73+/-295.63 | 0.3+/-0.02	 | 2952.52+/-468.37 |
| 	       Lasso  	    | 2388.68+/-398.48 | 0.34+/-0.01 | 3369.37+/-567.55 |  
|	  XGBoost Regressor   |	6796.01+/-335.89 | 0.95+/-0.0	 | 7417.55+/-389.15 |

## Modelo Final
  No fim, o modelo que teve um melhor desempenho foi o Random Forest Regressor, logo, ele devia ser o modelo a ser escolhido para realizar as predições. Todavia, nós escolhemos o XGBoost para fins de estudo. Em um primeiro momento ele dá impressão de ser um péssima escolha, mas com os parâmetros que foram escolhidos na etapa "Hyperparameter Fine Tunning" veremos que conseguiremos uma performance boa.
  
## Hyperparameter Fine Tunning
  Após escolhido o XGBoost Regressor, nós realizamos o Fine Tunning do modelo no qual conseguimos o seguinte desempenho:
  |       MODEL NAME      |      MAE CV      |   MAPE CV	 |      RMSE CV     |
  |-----------------------|------------------|-------------|------------------|  
  |	  XGBoost Regressor   |	   767.092812    |  0.115328	 |    1105.894623   |
 		  
# CONVERSÃO DO DESEMPENHO DO MODELO EM RESULTADOS FINANCEIROS
 Dado o conjunto de teste, obtemos os seguintes resultados financeiros:
 
 |     Scenario	    |      Values      |
 |------------------|------------------|
 |   predictions	  | R$286,474,432.00 |
 |  worst_scenario  |	R$285,615,996.91 |
 |  best_scenario	  | R$287,332,828.43 |
 
 Ou seja, temos uma margem de erro de R$1.000,00 tanto para o melhor cenário quanto para o pior cenário. Logo, temos uma performance ótima, pois é uma margem de erro pequena se compara ao montante total que está na faixa dos R$ 290.000,00.

# CONCLUSÃO

  Por fim, nesse projeto, cumprimos o objetivo de realizar a previsão das próximas 6 semanas de vendas de cada loja da Rede Rossmann sendo que, no contexto geral, obtemos um ótima performance do nosso modelo no primeiro ciclo. 
  
 Além disso, compreendeendemos que em problemas que envolve regressão é relevante que apliquemos modelos de comportamento linear(Linear Regression e Lasso) e não-linear(Random Forest Regressor e XGBoost Regressor) para que possamos entender como é o comportamento dos nossos dados e, baseado nessas informações, escolher o melhor modelo para ser implementado para que possamos obter a melhor performance possível e, no momento de fine tunning, possamos fazer pequenos ajuste de parâmetros para melhorar a accurace, dessa forma, conseguindo melhores retornos financeiros para o negócio.

# PROJETOS FUTUROS

  Para projetos futuros, podemos iniciar um novo ciclo desse projeto buscando novas abordagens para trabalhar com os seguintes pontos:
  
  - **Implementação do modelo Random Forest Regessor**
  - **Seleção de novas features para melhorar a performance do modelo**
  - **Melhoramento de performance do modelo em lojas em que a accurace foi bem baixa**
  - **Validação das Hipóteses restantes**
 
 **Para acessar os códigos e os desenvolvimento dos projetos, basta clicar no link:** https://github.com/jefferson-datascience/project_rossmann/blob/main/store_sales_prediction.ipynb
  
