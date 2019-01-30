# Forecast_Video_Game_Sales
Project 5 - ND Predictive Analysis for Business

## Passo 1: Planeje sua análise

1.	O conjunto de dados atende aos critérios de um conjunto de dados da série temporal? Certifique-se de explorar as quatro principais características de um dado de séries temporais.

Podemos falar que o conjunto de dados atende sim aos critérios da série temporal, afirmamos isso pois os dados estão em ordem, 2008-01 à 2013-09, de forma sequencial e em intervalos de tempo iguais, além de cada unidade de tempo ter no máximo um pondo de dados. 

2.	Quais registros devem ser usados como amostra de retenção?

O tamanho da amostra de retenção depende do tamanho da nossa série tempos e de quantos tempo temos como expectativa de prever. Neste problema de negócio, temos como objetivo prever os próximos 4 meses de vendas, com isso podemos dizer a amostra de retenção é dos últimos 4 períodos da nossa base, ou seja, se 2013-06 à 2013-09.

## Passo 2: Determine os componentes tendência, sazonalidade e erro

1.	Qual é a tendência, a sazonalidade e o erro da série temporal? Mostre como você conseguiu determinar os componentes usando gráficos de séries temporais. Inclua esses gráficos.

![01 - tendencia sazonalidade e erro](https://user-images.githubusercontent.com/34245933/52019464-f4308d00-24d4-11e9-959d-d680a3208615.PNG)  
*Figura 1: Tendência, Sazonalidade e Erro*
 
 ![02 - erro](https://user-images.githubusercontent.com/34245933/52019502-162a0f80-24d5-11e9-9aaa-5e1a9f9f6fd6.PNG)  
 *Figura 2: Error Plot*
 
Analisando os gráficos acima, podemos dizer que temos uma **Tendência Crescente**, pois como vemos o gráfico *Trend*, a nossa linha tem um padrão crescente.
Em relação à **Sazonalidade**, podemos ver claramente no gráfico *Seasonplot*, que temos uma queda de vendas entre Fev-Mai e um aumento de vendas entre Mai-Nov e isso ocorre em todos os anos analisados.
A variável **Erro** é demonstrado no gráfico *Remainder* e nele vemos claramente que temos uma variação ao longo do tempo. Quanto mais próximo de zero o Remainder estiver, o modelo interpretará os dados com maior acurácia.


## Passo 3: Construa seus modelos

1.	Quais são os termos modelo para o ETS? Explique por que você escolheu esses termos.

a.	Descreva os erros na amostra. Use pelo menos RMSE e MASE ao examinar os resultados.

Como vemos uma **sazonalidade** forte dentro dos anos, usamos o termo de modelo *multiplicativamente*. Vemos uma **tendência** de crescimento ano após ano, ou seja, uma tendência linear, então aplicamos o termo de modelo *aditivo*. Para a variável **erro**, por encontrarmos um erro que aumenta e diminui conforme o tempo, usamos o termo de modelo *multiplicativamente*. Por fim, executamos o modelo **ETS Dampened (amortecido)** e **Não Amortecido**, conforme resultados abaixo.

![03 - decomposition plot](https://user-images.githubusercontent.com/34245933/52019712-d3b50280-24d5-11e9-8d3c-659ad1475c1e.PNG)  
*Figura 3: Decomposition Plot – Method Dempened x Non-Dempened*

![03 - error summary](https://user-images.githubusercontent.com/34245933/52019734-ea5b5980-24d5-11e9-9d88-62bf14964c5a.PNG)  
*Figura 4: Error Summary – Method Dempened x Non-Dempened*

Podemos analisar os indicadores de ambos os métodos na comparação abaixo:

![05 - ets methods comparison](https://user-images.githubusercontent.com/34245933/52019767-03fca100-24d6-11e9-96e2-8017a5be86a8.PNG)  
*Figura 5: Comparação de Modelo ETS Amortecido e Não Amortecido*

Como o MASE e o AIC são menores no modelo ETS Dempened (Amortecido), podemos afirmar que este modelo é o que tem mais fit com os meus dados históricos, ou seja, esse método é o mais acurado para o nosso problema de negócio. Portanto, é ele que devemos uma para realizar nosso forecast. O MASE e o AIC podemos dizer que são algumas das principais métricas para análise de fit de modelo para séries temporais.

2.	Quais são os termos modelo para o ARIMA? Explique por que você escolheu esses termos. Crie um gráfico com a função de correlação automática (Auto-Correlation Function - ACF) e lotes de função de autocorrelação parcial (Partial Autocorrelation Function Plots - PACF) para as séries temporais e o componente sazonal e use esses gráficos para justificar a escolha dos termos do modelo.

a.	Descreva os erros na amostra. Use pelo menos RMSE e MASE ao examinar os resultados.
b.	Refaça os gráficos ACF e PACF tanto para a série temporal como para a diferença sazonal e inclua esses gráficos em sua resposta.

## Passo 4: Previsão
Compare as medidas de erro da amostra em ambos os modelos e compare as medidas de erro da amostra de retenção na sua previsão. Escolha o modelo de melhor ajuste e preveja os próximos quatro períodos (limite de 250 palavras).

Responda às seguintes perguntas:

1.	Qual modelo você escolheu? Justifique sua resposta mostrando: medições de erro na amostra e medidas de erro de previsão contra a amostra de retenção.

2.	Qual é a previsão para os próximos quatro períodos? Crie um gráfico com os resultados, usando intervalos de confiança de 95% e 80%.
