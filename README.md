# Sales Forecasting Project - Rossmann Store Sales

![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/f297423b-0aac-42fa-b510-567dc47adf38)

# 1. Descrição

Este é um projeto end-to-end de previsão de vendas para as próximas 6 semanas de uma rede de farmácias (Rossmann). Para a construção da solução do problema de negócio, foi aplicado a metodologia CRISP-DM, a qual se baseia em 10 principais passos:
- Problema de negócio
- Entendimento do negócio
- Coleta de dados
- Limpeza dos dados
- Análise exploratória dos dados
- Modelagem dos dados
- Aplicação de algoritmos de Machine Learning (XGBoost, Random Forest)
- Avaliação do algoritmo
- Modelo em produção (API no telegram)

![Untitled](https://github.com/ChristianoDS/rossmann_project/assets/103225340/911e085f-209d-418a-ac93-1276cf15d16b)

# 2. Problema de Negócio
## 2.1 Rossamnn

A Rossmann é uma rede de drogarias com origem alemã. Com mais de 3.000 lojas em sete países europeus, ela é uma das maiores redes de drogarias na Europa. A empresa vende uma variedade de produtos, incluindo itens de cuidados pessoais, produtos de beleza, produtos para o lar, alimentos e bebidas, entre outros. A Rossmann é conhecida por oferecer uma ampla gama de produtos a preços acessíveis e por sua presença em muitas comunidades locais na Europa.

![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/5519912f-dc5e-4c65-a94f-d5363699a04a)

## 2.2 Questão de negócio
Atualmente, os gerentes das lojas da Rossmann têm a tarefa de prever suas vendas diárias com até seis semanas de antecedência. As vendas das lojas são influenciadas por muitos fatores, incluindo promoções, concorrência, feriados escolares e estaduais, sazonalidade e localização. Com milhares de gerentes individuais prevendo vendas com base em suas circunstâncias únicas, a precisão dos resultados pode variar bastante

# 3. Entendimento do Negócio
O CEO da Rossmann planeja realizar um investimento para reformas nas suas lojas e para isso, necessita de um orçamento prévio de quanto suas 1115 lojas irão faturar durante as 6 próximas semanas do ano. Caracterizando um problema de predição.

# 4. Coleta dos dados
Os dados de origem pública foram coletados através da plataforma Kaggle (https://www.kaggle.com/c/rossmann-store-sales/data).

Arquivos coletados:
- train.csv: dados históricos incluindo vendas.
- test.csv: dados históricos excluindo vendas.
- sample_submission.csv: um arquivo de submissão de exemplo no formato correto.
- store.csv: informações complementares sobre as lojas.

# 5. Limpeza dos dados
Nessa etapa, depois de coletados os dados e carregados na IDE VSCode, foi aplicada uma limpeza dos dados. Aqui as colunas foram renomeadas em snake case, também foram checados e preenchidos com base no negócio os valores nulos e ausentes, em adição foram convertidos os dados de formato date, e alguns dados para o formato de inteiros. Aqui nessa etapa ainda foram aplicadas estatística descritiva para os dados numéricos e categóricos.

# 6. Análise Exploratória dos Dados - EDA
A EDA tem como principais objetivos a criação ou derivação de novas varáveis, além da criação e validação de hipóteses de negócio e também ajuda a ter sensibilidade de quais variáveis impactam a variável resposta (vendas).

## 6.1 Feature engineering
Nessa etapa são derivadas novas variáveis a partir de variáveis temporais. Como semanas do ano, dia, mes e ano, etc.

### 6.1.1 Mapa mental de hipóteses
Nessa etapa é avaliado o fenômeno a ser modelado, os agentes que atuam sobre o fenômeno de interesse (vendas) e criadas as hipóteses. Para a criação das hipóteses de negócios, foi criado um mapa mental de hipóteses.

![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/e2ee3a51-1832-465e-b39c-816b2e78bf0e)

## 6.2 Análise Univariada
Nessa etapa, para melhor entendimento da distribuição das variáveis, foi aplicado a análise univariada.

![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/664cdbb8-c1ec-49a3-b337-c121e37cd26a)

## 6.3 Análise Bivariada - Validação das hipóteses
Nessa etapa, por meio da análise bivariada (variável explicativa x variável resposta) foram respondidas as hipóteses de negócios criadas com o mapa mental de hipóteses. Ainda nessa etapa foram gerados alguns dos principais insights de negócio.

### 6.3.1 Principais insights da análise bivariada
- Lojas com maior sortimentos, vendem MENOS
  ![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/0146b397-e4fc-47b4-82fb-f7efda5f7a30)
- Lojas com competidores mais próximos vendem MAIS
Essa observação muito provavelmente pode dizer respeito a localização dos estabelecimentos próximos a shoppings e galerias, onde os competidores estão mais próximos.
- Lojas com mais promoções consecutivas vendem menos
- Lojas abertas durante o feriado de natal vendem menos
- Lojas vendem mais depois do dia 10 de cada mes

## 6.4 Análise multivariada
Por meio da análise multivariada pode-se ter uma noção de quais variáveis são impactantes para a predição das vendas. Com ela também pode-se ver quais variáveis estão mais correlacionadas entre si (multicolinearidade).
![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/5731dc28-4792-4182-9978-d6f818a1df62)

# 7.0 Modelagem dos dados
Nessa etapa os dados são preparados para o modelo de Machine Learning, sendo transformados, seja por meio de encoding (transformação de variáveis categóricas em numéricas), por meio de rescaling (deixando algumas variáveis na mesma escala, eliminando desproporcionalidades para o modelo de Machine Learning) ou normalizados (desejável que a variável alvo tenha uma distribuição normal).

## 7.1 Seleção de features
Durante essa etapa do CRISP, são aplicados processos, como a divisão dos dados a serem analisados (não considerando as 6 últimas semanas), além da aplicação do selecionados de variáveis adotado nesse projeto (Boruta). O Boruta traz as variáveis mais relevantes para a previsão das vendas. Essas variáveis selecionadas irão para o Modelo de Machine Learning do XGBoost.
![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/93c255f9-ba57-4e71-8642-ba7fd57a2f14)

# 8.0 Aplicação de algoritmos de Machine Learning
Aqui são aplicados alguns modelos de Machine Learning (ML) adequados para problemas de predição, como Regressão Linear (normal e com regularizzação Ridge), Random Forest e XGBoost. Para eliminar algum viés dos dados, e garantir a maior generalização do modelo, a técnica de Validação cruzada também foi aplicado. 

## 8.1 Tunagem de hiperparâmetros
Para melhoramento do desempenho do modelo de ML foi aplicado a técnica de RandomSearch (mais rápida e despende um menor tempo de processamento) para tentar encontrar de acordo com uma lista de valores, quais os melhores parâmetros para o modelo.

# 9.0 Avaliação do algoritmo
As métricas de desempenho do modelo foram RMSE, MAE e MAPE. O modelo mais promissor foi o XGBoost.

## 9.1 Tradução do modelo para o resultado de negócio
Aplicando todo o primeiro ciclo do CRISP, chegou-se a conclusão de que para as próximas 6 semanas, as 1115 lojas da Rossmann irão faturar aproximadamente $290 milhões, com um erro de 12.4% aproximado.
Também foram projetados os melhores/piores cenários de faturamento

![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/951c10a5-4273-4c1c-a098-8074fb645bb8)


# 10.0 Modelo em produção
Para deixar o projeto acessível para qualquer pessoa, foram criadas API's para fazer o deploy num aplicativo de celular, como o Telegram. Procurando no telegram por rossmannproject_bot, você pode entrar na conversa com o bot criado para o deploy desse projeto, e solicitar informação da loja desejada para saber seu faturamento nas próximas 6 semanas.

Exemplo: Caso queria saber o faturamento nas 6 próximas semanas para a loja 21, é só digitar "/21", que a mágica acontece.

![image](https://github.com/ChristianoDS/rossmann_project/assets/103225340/af352d24-44b8-49ad-96da-d19c4de0f287)

# 11.0 Conclusão
Aplicando o método CRISP para esse projeto, chegou-se a conclusão de que para as próximas 6 semanas, as 1115 lojas da Rossmann irão faturar aproximadamente $290 milhões, com um erro de 12.4% aproximado.

# 12.0 Próximos passos
Para melhor compreensão do case, são sugeridos melhorias no mesmo:
- Realizar mais ciclos do método CRISP
- Criar/derivar novas variáveis durante a EDA
- Testar outros modelos de ML, como o RANSAC
- Melhorar a precisão do modelo

# 13.0 Ferramentas utilizadas
- ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
- ![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white)
- ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
- ![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
- ![Scikit-learn](https://img.shields.io/badge/Scikit%20Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
- ![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
- ![XGBoost](https://img.shields.io/badge/XGBoost-016B8E?style=for-the-badge&logo=xgboost&logoColor=white)
- ![Matplotlib](https://img.shields.io/badge/Matplotlib-3776AB?style=for-the-badge&logo=matplotlib&logoColor=white)
- ![requests](https://img.shields.io/badge/requests-FF6F00?style=for-the-badge&logo=requests&logoColor=white)





