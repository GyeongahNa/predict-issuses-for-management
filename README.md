### predict-issues-for-management

본 프로젝트는 경희대학교 `데이터사이언스 및 시각화`를 수강하며 진행하였습니다.<br><br>

### 1. financialPlot

#### 기획의도

재무제표 분석이란, 이해관계에 있는 기업의 재무적 안정성 및 수익성을 시각화 하고 분석하여 예측하는 것이다. 그러나 Dart 공시에서 제공하는 재무제표는 테이블과 텍스트로만 이루어져 있고, 주요 평가 지표가 계산되어있지 않다. 따라서 분석가는 주요 지표를 일일이 계산하고 이를 다시 시각화하여 분석을 진행해야 한다. 
재무제표 시각화의 효율성을 제고하기 위하여 재무제표 시각화에 특화된 라이브러리 `financialPlot`을 개발, 배포하였다. 해당 라이브러리는 재무제표의 안정성, 수익성, 부실가능성 분석에 자주 사용 되는 15개의 차트를 제공한다.  사용자는 plotly에 대한 특별한 학습 없이 동적 차트를 구현할 수 있고, 재무적 지표를 자동으로 계산하도록 하여 시각화 할 수 있다.

#### 설치

```
Pip install financialPlot
From financialPlot import financialPlot
```

#### 사용 예시
```
financialPlot.막대(
“유동비율 분석”, corp_list, “유동비율 (%)”, 
ratio_list, color_list, legend_colors, px.colors.sequential.Reds_r[1])
```
<br><br>

### 2. 관리종목 및 비관리종목의 분류 예측

financialPlot 및 회계 도메인 지식을 이용하여 실제 기업 데이터를 분석하고 도산 가능성이 높은 기업을 예측하였다. 일반적으로 재무제표 데이터를 분석하는 과정에서 기업이 가지고 있는 이미지와 편견이 반영된다. 기업에 대한 이미지를 제거한 합리적인 의사결정을 위해 분류 모델을 구현하여 관리종목을 예측하였다.<br>

#### 데이터 수집 및 전처리
- 국내 기업의 2015 ~ 2019 재무제표 데이터
- DART OPEN API를 통해 수집
- JSON 형태의 데이터를 dataframe으로 변환
- 결측치는 DART 공시 사이트를 참고하여 실제 값으로 대체
- 화폐 단위 통일(KRW)

#### 모델 구성 및 학습
- 사용 모델: SVM
- Accuracy: 97%

#### 분류 결과 및 대안 제시
분류 모델이 테스트 데이터의 관리종목지정여부를 정확히 분류하는 것은 중요하다. 그러나 분류 모델이 정확히 예측하지 못한 테스트 데이터를 자세히 살펴볼 필요성도 있다. 실제로는 관리종목이 아니지만 분류모델이 관리종목으로 예측한 경우 이는 기업의 재무 데이터가 관리종목으로 예측될 만큼 위험하다는 것을 나타낼 수 있다. 따라서 해당 데이터 분석의 결과로 재무적 수익성과 안정성의 재검토가 필요한 기업을 선정하였다.


#### Details
> [최종 보고서](https://github.com/GyeongahNa/predict-issuses-for-management/blob/main/report.pdf)<br>
> [financailPlot 코드](https://github.com/GyeongahNa/predict-issuses-for-management/tree/main/financialPlot)<br>
> [데이터 분석 코드](https://github.com/GyeongahNa/predict-issuses-for-management/blob/main/codes.ipynb)<br>





