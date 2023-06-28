<h1 align="center">Análise de Dados com Phyton - Cancelamentos Cartão de Crédito </h1>

<h2 align="left"> 🎯Desafio </h2> 

Análise de Dados em Phyton.  

Objetivo: Você trabalha em uma grande empresa de Cartão de Crédito e o diretor da empresa percebeu que o número de clientes que cancelam seus cartões tem aumentado significativamente, causando prejuízos enormes para a empresa
O que fazer para evitar isso? Como saber as pessoas que têm maior tendência a cancelar o cartão?

Informações: Temos 1 base de dados com informações dos clientes, tanto clientes atuais quanto clientes que cancelaram o cartão

Download da Base de Dados: Botão na página

Referência: https://www.kaggle.com/sakshigoyal7/credit-card-customers

Empresa:  Cartão de Crédito 

<h2 align="left"> 🗂️ Organizando o Desafio </h2> 

► Passo 1 - Importar a base de dados

► Passo 2 - Visualizar e tratar essa base de dados

► Passo 3 - Observar a base de dados para ter um panorama geral para resolver o desafio, alguma informação que nos ajude.


<h2 align="left"> 1 - Importar a base de dados </h2> 
  Eu utilizei para esse projeto o Google Colaboratory, e utilizei o seguinte código

 import pandas as pd
  tabela = pd.read_csv("/content/drive/MyDrive/PHYTON/#Treinamento - Analises de dados/ClientesBanco.csv", encoding="latin1")
  tabela = tabela.drop("CLIENTNUM",axis=1)
  display (tabela)

  ![image](![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/e6127850-3280-439f-862f-a68941610c80)


  <h2 align="left"> Passo 2 - Visualizar e tratar essa base de dados </h2> 
    
  Precisamos sempre verificar se os dados estão todos preenchidos e no formato correto, para isso utilizo o seguinte código
  
  tabela = tabela.dropna()
  display(tabela.info ())
  
  ![image](![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/b80ea593-ddff-45c1-a313-43ab8cc80b6a)

  
<h2 align="left"> Passo 3 - Visão Geral | Análise dos dados </h2> 

  Utilizei o .describe para gerar estátisticas descritivas e entender mais sobre os clientes e como os valores estão distribuidos para irmos para o próximo passo com algumas ideias. 


  ![image](![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/40b9f942-1f12-4941-8fa2-8c651058047d)

  Vamos analisar como está a divisão entre cientes e cancelamento
    Obeservações: .value_counts() para contar quantos clientes e quanto canceledos temos e guardo isso em uma variavel. +normalize=true para me trazer o quando daquilo representa em porcentagem do total.

  qtde_categoria = tabela ["Categoria"].value_counts()
  display(qtde_categoria)

  qtde_categoria_perc = tabela ["Categoria"].value_counts(normalize=True)
  display(qtde_categoria_perc)
  ![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/1b71ad61-986e-485e-b3a6-344bf3ca1efa)

Temos que 16% dos clientes no total cancelaram, vamos olhar mais afundo agrupando de formas diferentes para descobrir motivos semelhantes entre eles e assim descobir as 3 principais causas.

Algumas formas para descobrir o motivo de cancelamento:
Podemos olhar a comparação entre Clientes e Cancelados em cada uma das colunas para ver se traz algum tipo de insight novo


Vamos amos utilizar a bliblioteca plotly, além dela ser facil ela é muito boa para usar os gráficos

 import plotly.express as px
 for coluna in tabela:
  grafico = px.histogram(tabela, x= coluna, color= "Categoria")
  grafico.show()

  ![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/a3120ba3-8188-4e42-b293-3524628f4778)

  ![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/cb9eed4d-6ca9-4ed9-9ad3-49944a76bbcf)
  ![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/711f8cdd-da7f-4655-93d2-46252ebf0db6)
  ![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/da6d1448-e859-4c65-811e-0c0147e09d7f)
  ![image](https://github.com/Isabella-Bueno/PYTHON_ANALISE_DE_DADOS/assets/112008347/254207f3-5b9f-4e32-b54f-0b91486ee765)


  # ANÁLISE DOS GRÁFICOS
  
  ► Quanto mais produtos ele tem menor a chance dele cancelar 
  
  ► Quanto Mais Transações menor a chance dele cancelar.
  
  ► Quato maior o contato maior a chance dele cancelar.





    
