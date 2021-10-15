# ⚡[DACON](https://dacon.io/competitions/official/235740/overview/description)-Artificial-Intelligence-Bit-Trader-Competition-Season-3⚡

#Overview of the competition - Time Series Data Prediction Model
#
#1. Topic

#Please make the highest yield model by predicting the price of 10 kinds of cryptocurrency including Bitcoin!
#
#2. Background

#If you could predict the future correctly, what would you like to do first?

#There have been many developments in many areas to predict the price of stocks and cryptocurrency.

#Then is it possible to predict the price of cryptocurrency by looking at the price in minutes for a day?

#Wouldn't it be possible to predict the price of cryptocurrency by referring to the codes of many time series competitions currently held in Dacon?

#Join the contest through your own brilliant ideas and experiments!
#
#3. Explanation of the competition

#All participants have a total virtual capital of $10,000.

#The goal is to create a model that invests continuously and predicts the amount of final change in a total of 760 investment 
opportunities.
#
#4. Organized / supervised

#Host: [DACON](https://dacon.io/)

#Subject: [DACON](https://dacon.io/)

#

### ✔ INU_IME팀, PUBLIC 4위,Private31위 ($1351.64013)ARIMA

대회를 마무리하며 전체적인 코드를 공유합니다. 

Public 평가와 달리, Private 평가에서는 성능이 좋지 않았습니다. 

저희는 Arima 모델을 사용했는데요, 최대한 안정적으로 매매하는 것을 목표로 했습니다.

BB(볼린저 밴드)와 BBW를 이용하여 Price가 BB와 BBW의 상단터치, 하단터치시 매수 매도 등의 제약을 걸어봤으나, 유효한 결과를 얻지 못하여, 안정성 증가만을 목표로 하단 터치시 buy quantity = 0 이 되도록 설정했습니다.

RSI와 VWAP등 여러 지표도 사용했고, Price의 경우엔 꼬리가 긴 형태의 bar로 인한 변동성 증폭을 고려하여 다음과 같이 초기 Price를 설정했습니다.

((((df['high'] + df['low'])/2) +  df['open'] + df['close']) / 3)
#
### 결과적으로 Public 평가에서는 4위, Private 평가에서는 31위를 기록했습니다.

Private 평가에서 성능이 좋지 않았던 이유를 리뷰해 보겠습니다. (Private 평가에 사용된 data는 2021년 4월~5월의 데이터라는 것만 공개)

우선, 리더보드를 보면, Public 평가 상위권 팀들 대부분이 Private 평가에서 순위가 급락한 것을 확인 할 수 있었습니다.

저희 팀의 경우에도 Public 평가의 Score는 21,274.17065인 반면, Private 평가의 Score는 1351.64013로  10배 이상 하락했습니다.

또한, Private 상위권 팀의 점수를 보면, 거의 거래를 하지 않은(기준점수 10,000)에 근접한 팀들이 대다수인것을 확인했습니다.

해당팀들의 Public 평가 점수를 확인해 본 결과, Public 평가에서도 거래를 하지않고 Submission을 제출만 한 팀들이 대부분 이라는 것을 확인 했습니다.

이러한 근거를 바탕으로 거래를 하면 할 수록 손실이 발생했을 것이라는 가설을 세웠고, Private 평가용 데이터에 대해 좀더 탐색해 보았습니다.

Private 평가용 데이터의 기간동안 (2021년 4월~5월) Binance 기준으로 비트코인 차트를 보면, 큰 급락이 있었습니다.
#
![binance btc](https://user-images.githubusercontent.com/66030601/137497764-adcd1696-c47a-4a54-a0bc-3a5b625e9dac.PNG)

1D Bar 차트로 보면, 적정 매수 타점은 이와 같이 볼 수도 있습니다.

![binance btc1](https://user-images.githubusercontent.com/66030601/137498060-d6c6b5ac-d393-4d85-94b2-4943dbc8ca66.PNG)
#
하지만 거래량 Data를 함께 본다면, 매도 거래량이 매수 거래량을 압도하기 때문에, 매수타점은 사실상 존재하지 않는 것으로 보여집니다.
#
⚡ 실제로 제가 취미로 Upbit API를 이용해서 Larry Williams's Volatility Breakthrough Strategy Algorithm 을 적용한 프로그램매매를 진행하고 있는데, 해당 기간인 2021년 4월~5월에는 매수신호가 거의 없었던 경험이 있습니다.
#
Private 평가에서는, 데이터가 Secret Data라는 생각을 했는데, Private 평가에 이용되는 시계열 데이터의 대략적인 기간이 공지되어 있으므로, Private 평가에 사용되는 데이터에 해당되는 기간의 전체 추세를 안다는 것을 전제로 하여 전략을 구성했으면 좀더 현실적인 전략으로 접근할 수 있지 않았을까 하는 아쉬움이 남습니다.

좋은 팀원과 좋은 경험을 쌓게 해준 DACON팀에게 감사드립니다.

