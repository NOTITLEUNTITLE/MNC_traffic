
# 35개 도로의 시간별 교통량 예측
MNC에서 주관한 교통 물류 통행량 시계열 예측 모델 대회입니다.

## 대회 개요
- **대회 기간** : 2022년 02월 16일 12:00 PM ~ 2022년 02월 22일 12:00 PM
- **문제 정의** : 35개 도로의 시간별 물류 통행량 데이터를 학습, 이를 기반으로 기준시점 이후 물류 통행량을 예측하는 과제
- **추진 배경**
	- 도시화, 밀집화에 따른 교통 혼잡도 예측의 중요성 증대
	- 자율 주행 고도화 및 효율화를 위한 전제 조건


- **평가 지표** 
	- **RMSE(Root Mean Square Error)**
	<br/>
![image](https://github.com/NOTITLEUNTITLE/MNC_traffic/blob/main/image4.PNG?raw=true)<br/>
RMSE 관련 [참고 사이트](https://www.statisticshowto.com/probability-and-statistics/regression-analysis/rmse-root-mean-square-error/)


----------
## 문제 접근방법
이 문제를 풀면서 데이터에 대한 많은 고민을 하게 됩니다.
- 교통량에 직접적인 영향을 끼칠만한 이슈들에 대한 데이터가 아닌, 단순히 교통량의 통계 데이터만을 가지고 있었기에, 예측의 어려움이 있습니다.(함축적인 데이터라고 생각했습니다.)<br/>
저는 무수히 많은 삽질을 해본결과, 문제를 간단하게 만들어야 한다고 생각했습니다.
~~(어떻게 보면 당연한 말이지만, 논리적이고, 설득력이 있어야겠지요..)~~

주어진 데이터는 3447 x 35의 shape이였지만,
최종적으로 11 x 1의 형태로 만들어 내었습니다.

이렇게 만들어진 이유는, 제가 최종적으로 예측해야하는 값들은 1주일(월화수목금토일)의 24시간 동안 35개의 도로에 대해서 예측해야했습니다.

따라서, 각 요일별(7) 그리고 도로별(35개), 마지막으로는 시간(24)별로 묶으면 
11(주의 갯수)*1의 형태의가 나오게 되고, 저희는 12번째의 데이터를 예측하면 됩니다!!!

```python
Monday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
Tuesday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
Wednesday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
Thursday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
Friday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
Saturday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
Sunday = { '10': {0: [...], 1: [...], ..., 23: [...]}, '100': {0: [...], 1: [...], ..., 23: [...]}, ..., '6000': {0: [...], 1: [...], ..., 23: [...]}}
```

말로만 들으니깐 조금 이해가 안되실수있습니다.(설명을 못하는 제가 답답하네요...)
**자세한 내용은 .ipynb 파일을 확인부탁드립니다. 설명을 상세히 써놨습니다.**


## 학습결과
![image](https://github.com/NOTITLEUNTITLE/MNC_traffic/blob/main/image1.PNG?raw=true)
public socre 3620점을 기록하고, private는 3623점을 기록했습니다.
참고로 1등했습니다.@@@@


## Trend Image
<img src="https://github.com/NOTITLEUNTITLE/MNC_traffic/blob/main/image2.PNG?raw=true">



<br/><br/>
## 마무리
여지가 많이 남아 아쉬움이 큰 대회였습니다.
기본적으로 1주일대회여서 EDA하고 데이터 보는데만 2~3일 보면서 의미를 곱씹어보는 저에게는 아쉬운 대회 일정이였습니다.
- 첫번째로 아쉬운점은,linear regression으로 예측모델을 작성해보는것도 해볼만 했습니다.
- 두번재로 아쉬운점은, 각 도로별로 11-12개의 데이터들의 증가세와 감소세를 코딩으로 확인해 보려했으나, 대회종료 3분전임을 알았으며, 시도하지 못했습니다..<br/>
  - 11-12개 정도되는 데이터를 시간순서대로 증가했는지, 감소했는지 확인한후,<br/>과반이상이 증가했다면 가중치를 더해주고,<br/>과반이상이 감소했다면 빼주는 방법을 생각했습니다.<br/> 도로별로 교통량이 상이하기에 volume도 고려해야합니다.(단순히 증가했다, 감소했다가 아니라 증가량,감소량이 중요합니다.)<br/>
아니면, 끝에 데이터 2-3개만 해보는것도 정확할 것 같습니다.


	

	
-------
### traffic.ipynb : 최종 제출파일
