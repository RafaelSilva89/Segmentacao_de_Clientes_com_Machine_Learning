# Segmentação de clientes com Machine Learning
Este repositório contém script para fazer uma segmentação de clientes para definir a estratégia de marketing

<div align="center">
<img src="Imagens/Capa.PNG" width="500px">
</div>
</br>


# _Objetivo do projeto_

<img src="Imagens/Capa2.PNG" width="220px" align='right'>

<p align = 'left'>

Desenvolver uma segmentação de clientes com base no comportamento de compras.
<p>

<br>

# _1. Problema de Negócio_

Hoje sabemos que é de fundamental importância segmentar os nossos clientes para saber qual o padrão de consumo de cada um, e saber quais clientes estão mais propensos a comprar determinados tipos e marcas de produtos.
Um dos pontos cruciais de marketing é conhecer os clientes e identificar suas necessidades e entendendo os consumidores podemos enviar campanhas específicas para necessidades específicas e se dados sobre os clientes estão disponíveis, podemos aplicar Ciência de Dados para segmentar o mercado.

Fonte: https://www.kaggle.com/arjunbhasin2013/ccdata

<br>

# _2. Justificativa_

- **Por quê:** Dificuldade em segmentar os clientes para enviar campanhas
específicas.
- **Como:** Com a método CRISP-DM.
- **O quê:** Usando o algoritmo K-Means que trabalha com Clustering que é um conjunto de técnicas usadas para particionar dados em grupos ou clusters.

<br>

# _3. Premissas_

O conjunto de dados de amostra resume o comportamento de uso de cerca de 9.000 portadores de cartão de crédito ativos durante os últimos 6 meses.

As variáveis originais do conjuto de dados são:<br>

Variável | Definição
------------ | -------------
CUSTID | Identificação do cliente|
BALANCE | Saldo para fazer compras (saldo na conta corrente)|
BALANCE_FREQUENCY | Frequência que o saldo é atualizado (1 = frequente, 0 = não frequente) |
PURCHASES | Quantidade de compras realizadas|
ONEOFFPURCHASES | Quantidade de compras feitas “de uma só vez”|
INSTALLMENTS_PURCHASES | Quantidade de compras parceladas|
CASH_ADVANCE | Dinheiro adiantado, indica se o cliente saca do cartão de crédito|
PURCHASES_FREQUENCY | Frequência das compras (entre 1 e 0)|
ONEOFF_PURCHASES_FREQUENCY | Frequência de compras à vista (entre 1 e 0)|
PURCHASES_INSTALLMENTS_FREQUENCY | Frequência de compras parceladas (entre 1 e 0)|
CASH_ADVANCE_FREQUENCY | Frequência de saques de dinheiro adiantado|
CASH_ADVANCE_TRX | Número de transações feitas|
PURCHASES_TRX | Número de compras|
CREDIT_LIMIT | Limite do cartão de crédito|
PAYMENTS | Valor pago|
MINIMUM_PAYMENTS | Valor mínimo pago|
PRC_FULL_PAYMENT | Percentual de pagamentos da fatura “completa”|
TENURE | Posse do titular do cartão|

<br>

# _4. Planejamento da solução_

1. Entendimento do negócio:
    - Foi realizado a descrição do negócio.
2. Coleta dos dados:
    - Foi feito o downloand do arquivo da plataforma do Kangle.
3. Limpeza dos dados:
    - Foi realizado a Análise Descritiva dos Dados, passo importante para verificar o quanto, o projeto é desafiador, ou seja verificar a qualidade dos dados e o entendimento dos dados.
    - Também foi realizado a filtragem das variáveis relacionado nas restrições do negócio, fazendo a média para preencher os valores nulos.
4. Análise exploratória dos dados:
    - Nesta etapa foi realizado a Exploração de Dados, que serve para medir o impacto das variáveis em relação as variáveis respostas e muitas vezes quantificar este impacto, nesta etapa começa gerar valor para o entendimento do negócio.
5. Preparação dos dados:
    - Agora entramos na Modelagem dos dados, onde vamos preparar os dados para ensinar os Algoritmo de Machine learning, passo importante, porque o aprendizado da maioria dos algoritmos de ML é facilitado com dados numéricos e na mesma escala.
    - Vamos usar o Algoritmo K-Means, então devemos definir do número de clusters de acordo com a base de dados e foi usado Elbow Method, que é chamado do método do cotovelo.
6. Treinamento algoritmos de machine learning:
    - Nesta etapa vamos implementar os Algoritmos de Machine Learning, e escolher o que tem mais performance e seguir com ele para a produção.
7. Avaliação do algoritmo:
    - Nesta etapa é a oportunidade de responder: Qual seria o impacto deste resultado no negócio?
    - Dependendo da resposta podemos colocar em produção e deixar o time de negócio usar ou voltar e melhorar alguns pontos.
    - E para avaliar foi feito a aplicação de PCA (principal component analysis) é utilizado para redução de dimensionalidade, uma técnica que pode ser usada para ajudar na visualização do agrupamento.
8. Implementar o modelo para produção:
    - É a etapa em colocar em produção ou fazer uma simulação do modelo, para deixar acessível para qualquer consumidor.

<br>

# _5. Insights_

*Resumo dos insights durante análise exploratória de dados (EDA):*

- Separar um grupo de cliente que possuem uma tendência maior a sacar dinheiro do limite do cartão de crédito, pois assim o banco poderia aumentar o limite e os clientes poderia sacar mais dinheiro e o banco passaria a ganhar mais.
- Poderiamos separar grupos, pessoas que faz compra a vista e pessoas que faz compras a prazo, para que o banco possa enviar campanha de marketing diferentes.
- No atributo Purchases_frequency, podemos identificar dois grupos, um grupo de que usa muito o cartão de crédito e outro que praticamente não usa cartão de crédito, desta forma o banco pode análisar e mandar campanha diferente para cada perfil de cliente.

<br>

# _6. Modelos de Machine Learning_

1. K-Means.
2. PCA (principal component analysis)

<br>

# _7. Performance do Modelo de Machine Learning_

Analisando o resultado do algoritmo K-Means podemos fazer a definição do perfil dos clientes em grupos:

- Grupo 0:
  - TENURE: Clientes mais novos (7.23)
  - BALANCE: E que mantém pouco dinheiro na conta corrente (865).


- Grupo 3:  
  - BALANCE: É um dos grupo que mais deixam dinheiro na conta corrente (5567).
  - CREDIT_LIMIT : O limite do cartão alto a média é de 15570.
  - PRC_FULL_PAYMENT: É o grupo com o mais alto percentual de pagamento da fatura completa (0.47).

Este grupo pode ser considerados os clientes mais importantes para o banco (VIP/Prime). Podemos dizer que o banco sempre vai ganhar dinheiro com estes clientes, porque eles usam o cartão e pagam a fatura em dias. Uma estratégia que o banco pode fazer é aumentar o limite do cartão e incentivar o hábito de compras através de uma campanha de marketing.


- Grupo 4:
  - CASH_ADVANCE: Sacam muito dinheiro do cartão de crédito (5207).
  - PURCHASES_FREQUENCY: Compram pouco (0.29).
  - CASH_ADVANCE_FREQUENCY: E usam bastante o limite do cartão para saques (0.51).
  - PRC_FULL_PAYMENT: Pagam muito pouco a fatura completa (0.03).

Este pode ser considerado um grupo que o banco acaba ganhando bastante dinheiro, porque no uso do CASH_ADVANCE têm um juros muito alto, porém apresenta o maior risco para o banco, porque se eles não pagam a fatura completa a tendência é que estes clientes vão endividar cada vez mais rápido e pode chegar em uma situação que eles não vão ter o dinheiro para pagar todos os estes juros para o banco.


- Grupo 7:
  - São clientes que pagam poucos juros para o banco e são cuidadosos com seu dinheiro.
  - BALANCE: Possui menos dinheiro na conta corrente (105).
  - CASH_ADVANCE: Não sacam muito dinheiro do limite do cartão (303).
  - PRC_FULL_PAYMENT: 23% dos clientes deste grupo pagam a fatura completa.

Uma hipótese é que eles deixam pouco dinheiro na conta corrente, para fazer aplicações financeiras, porque se deixar dinheiro na conta corrente não vai render nada.

Fazemos a redução de dimensionalidade, justamente para conseguir visualizar no gráfico como os grupos estão dispostos. Este gráfico é mais para conseguir visualizar melhor os dados e desta forma fica melhor a visualização, porque podemos observar os grupos de maneira gráfica.


<div align="center">
<img src="Imagens/PCA.PNG" width="500px">
</div>
</br>


# _8. Conclusão_

O objetivo do projeto era fazer uma análise das vendas e do comportamento dos clientes. Com as features existentes no dataset foi possível segmentar os clientes, para o departamento de Marketing e agora se torna possível enviar campanhas específicas para necessidades específicas dependendo do tipo de cliente.

<br>

# _9. Próximos passos_
Aplicação de autoencoders que são um tipo de redes neurais artificiais para codificar dados, uma forma alternativa para a aplicação do PCA.
