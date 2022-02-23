
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
![image](data:image/png;base64,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)
RMSE 관련 [참고 사이트](https://www.statisticshowto.com/probability-and-statistics/regression-analysis/rmse-root-mean-square-error/)


----------
## 문제 접근방법
이 문제를 풀면서 데이터에 대한 많은 고민을 하게 됩니다.
- 교통량에 직접적인 영향을 끼칠만한 이슈들에 대한 데이터가 아닌, 단순히 교통량의 통계 데이터만을 가지고 있었기에, 예측의 어려움이 있습니다.(함축적인 데이터라고 생각했습니다.)<br/>
저는 무수히 많은 삽질을 해본결과, 문제를 간단하게 만들어야 한다고 생각했습니다.
~~(어떻게 보면 당연한 말이지만, 논리적이고, 설득력이 있어야겠지요..)~~

주어진 데이터는 3447*35의 shape이였지만,
최종적으로 11*1의 형태로 만들어 내었습니다.

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


### 학습결과
![image](https://github.com/NOTITLEUNTITLE/MNC_traffic/blob/main/image1.PNG?raw=true)
public socre 3620점을 기록하고, private는 3623점을 기록했습니다.
참고로 1등했습니다.@@@@







## 마무리
여지가 많이 남아 아쉬움이 큰 대회였습니다.
기본적으로 1주일대회여서 EDA하고 데이터 보는데만 2~3일 보면서 의미를 곱씹어보는 저에게는 아쉬운 대회 일정이였습니다.
- linear regression으로 예측모델을 작성해보는것도 해볼만 했습니다.
- 아니면 코딩으로 증가세나 감소세를 확인해보는것도 좋았을것 같았습니다.!!!

	

	
-------
### report_final.ipynb : 최종 제출파일
