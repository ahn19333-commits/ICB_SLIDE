# 펭귄 데이터셋 분석 프레젠테이션

## 타이틀 슬라이드

**펭귄 데이터셋 분석 보고서**

- 발표자: AI 어시스턴트
- 날짜: 2025년 12월 23일

::: notes
이 프레젠테이션은 Palmer Penguins 데이터셋을 분석한 결과를 요약합니다. 데이터 로드, 시각화, 인사이트를 포함합니다.
:::

## 소개

Palmer Penguins 데이터셋 소개

- 세 종의 펭귄: Adelie, Chinstrap, Gentoo
- 변수: 부리 길이/깊이, 날개 길이, 체중, 성별, 섬
- 분석 목표: 종별 차이, 생태적 의미 이해

::: notes
데이터셋은 남극 펭귄 연구에서 유명하며, 기계 학습 예제로 자주 사용됩니다.
:::

## 데이터 개요

### 데이터셋 정보

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 344 entries, 0 to 343
Data columns (total 7 columns):
 #   Column             Non-Null Count  Dtype
---  ------             --------------  -----
 0   species            344 non-null    object
 1   island             344 non-null    object
 2   bill_length_mm     342 non-null    float64
 3   bill_depth_mm      342 non-null    float64
 4   flipper_length_mm  342 non-null    float64
 5   body_mass_g        342 non-null    float64
 6   sex                333 non-null    object
dtypes: float64(4), object(3)
memory usage: 18.9+ KB
```

::: notes
344개의 행, 7개의 열. 결측치가 일부 존재합니다.
:::

## 데이터 개요 (계속)

### 데이터셋 설명

```
       bill_length_mm  bill_depth_mm  flipper_length_mm  body_mass_g
count      342.000000     342.000000         342.000000   342.000000
mean        43.921930      17.151170         200.915205  4201.754386
std          5.459584       1.974793          14.061714   801.954536
min         32.100000      13.100000         172.000000  2700.000000
25%         39.225000      15.600000         190.000000  3550.000000
50%         44.450000      17.300000         197.000000  4050.000000
75%         48.500000      18.700000         213.000000  4750.000000
max         59.600000      21.500000         231.000000  6300.000000
```

### 결측치

```
species               0
island                0
bill_length_mm        2
bill_depth_mm         2
flipper_length_mm     2
body_mass_g           2
sex                  11
dtype: int64
```

::: notes
평균 값과 결측치를 요약. 성별에 결측치가 많습니다.
:::

## 시각화 1: 부리 길이 히스토그램

![부리 길이 히스토그램](bill_length_hist.png)

**인사이트:** 부리 길이 분포는 정규에 가까우나 종별 차이 존재. 평균 44mm, Gentoo가 길고 Adelie가 짧음. 생태적 적응 반영.

::: notes
이 그래프는 펭귄 종의 다양성을 보여줍니다. 긴 부리는 물고기 잡기에 유리.
:::

## 시각화 2: 부리 깊이 히스토그램

![부리 깊이 히스토그램](bill_depth_hist.png)

**인사이트:** 깊이 분포는 bimodal 경향. Gentoo가 깊고, Adelie 얕음. 먹이 처리 방식 차이.

::: notes
부리 깊이는 먹이 종류와 관련. 깊은 부리는 큰 먹이 처리.
:::

## 시각화 3: 날개 길이 히스토그램

![날개 길이 히스토그램](flipper_length_hist.png)

**인사이트:** 평균 201mm, Gentoo가 가장 길어 수영 효율 높음. 서식지 적응.

::: notes
날개 길이는 수영 능력 지표. 긴 날개는 깊은 바다 탐험 가능.
:::

## 시각화 4: 체중 히스토그램

![체중 히스토그램](body_mass_hist.png)

**인사이트:** 평균 4202g, Gentoo 무거움. 지방 저장으로 겨울 견딜 수 있음.

::: notes
체중은 건강과 생존 관련. 환경 변화 모니터링 중요.
:::

## 시각화 5: 종별 부리 길이 박스플롯

![종별 부리 길이 박스플롯](bill_length_box.png)

**인사이트:** Gentoo 중앙값 높음. 진화적 분화, 먹이 경쟁 피함.

::: notes
종별 구분 뚜렷. 분류 모델 유용.
:::

## 시각화 6: 종별 체중 박스플롯

![종별 체중 박스플롯](body_mass_box.png)

**인사이트:** Gentoo 무거움. 서식지 자원 영향.

::: notes
생존 전략 차이. 기후 변화 영향.
:::

## 시각화 7: 부리 길이 vs 깊이 산점도

![부리 길이 vs 부리 깊이 산점도](bill_scatter.png)

**인사이트:** 클러스터링 뚜렷. 약한 상관관계. 종별 특화.

::: notes
다변량 분석 기초. 이상치 주의.
:::

## 시각화 8: 날개 길이 vs 체중 산점도

![날개 길이 vs 체중 산점도](flipper_body_scatter.png)

**인사이트:** 강한 양 상관. 척추동물 패턴. 수영 효율.

::: notes
종 구분 가능. 생태적 niche 이해.
:::

## 시각화 9: 종별 개수 막대 그래프

![종별 개수 막대 그래프](species_bar.png)

**인사이트:** Adelie 우세. 넓은 서식지. 기후 취약성.

::: notes
샘플링 편향 고려. 다양성 반영.
:::

## 교차표: 종 vs 섬

```
island     Biscoe  Dream  Torgersen
species
Adelie         44     56         52
Chinstrap       0     68          0
Gentoo         124     0          0
```

**인사이트:** 섬별 분포. 경쟁 피함. 보존 우선순위.

::: notes
섬 환경이 종 선택 결정.
:::

## 피봇테이블: 종 및 성별 평균 체중

```
sex        Female     Male
species
Adelie   3368.836   4043.493
Chinstrap 3527.206  3938.971
Gentoo   4679.741  5484.836
```

**인사이트:** 수컷 무거움. 성적 이형성. 번식 생물학.

::: notes
건강 평가에 유용.
:::

## 시각화 10: 섬별 개수 막대 그래프

![섬별 개수 막대 그래프](island_bar.png)

**인사이트:** Biscoe 많음. 면적과 먹이 영향.

::: notes
연구 샘플링 반영.
:::

## 교차표: 섬 vs 종

```
species  Adelie  Chinstrap  Gentoo
island
Biscoe       44          0     124
Dream        56         68       0
Torgersen    52          0       0
```

**인사이트:** 역 분포. 환경 적응.

::: notes
보존 전략 수립.
:::

## 피봇테이블: 섬 및 종별 평균 부리 길이

```
species    Adelie  Chinstrap   Gentoo
island
Biscoe    38.975   0.000000  45.584
Dream     44.167  48.833333  0.000
Torgersen 39.038   0.000000  0.000
```

**인사이트:** 유전적 요인. 환경 영향 적음.

::: notes
진화 연구 기여.
:::

## 시각화 11: 종별 체중 바이올린 플롯

![종별 체중 바이올린 플롯](body_mass_violin.png)

**인사이트:** 분포 밀도. Gentoo 넓음. 변동성.

::: notes
세부 패턴 이해. 이상치 외.
:::

## 시각화 12: 페어 플롯

![페어 플롯](pair_plot.png)

**인사이트:** 모든 변수 관계. 클러스터링. 다변량.

::: notes
종 분류 모델 구축.
:::

## 시각화 13: 상관관계 히트맵

![상관관계 히트맵](correlation_heatmap.png)

**인사이트:** 날개-체중 강 상관. 모델 변수 선택.

::: notes
선형 관계 요약.
:::

## 시각화 14: 종별 성별 카운트 플롯

![종별 성별 카운트 플롯](sex_count.png)

**인사이트:** 균형적. 성비 왜곡 시 스트레스.

::: notes
생식 건강 모니터링.
:::

## 시각화 15: 종별 평균 부리 길이 라인 플롯

![종별 평균 부리 길이 라인 플롯](mean_bill_line.png)

**인사이트:** 평균 차이. 형태적 차이.

::: notes
트렌드 강조.
:::

## 결론

- 펭귄 종별 차이 명확.
- 시각화로 패턴 이해.
- 생태적 의미: 적응, 경쟁, 보존.

::: notes
이 분석은 펭귄 연구에 기여. 추가 연구 권장.
:::

## 감사합니다

질문 있으신가요?

::: notes
프레젠테이션 종료. 추가 논의 환영.
:::