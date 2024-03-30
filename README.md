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
Os dados de origem pública foram coletados atrás da plataforma Kaggle (https://www.kaggle.com/c/rossmann-store-sales/data).
Arquivos coletados:
- train.csv: dados históricos incluindo vendas.
- test.csv: dados históricos excluindo vendas.
- sample_submission.csv: um arquivo de submissão de exemplo no formato correto.
- store.csv: informações complementares sobre as lojas.


