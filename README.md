# 목표설정이 학업성취에 미치는 영향 분석 (PISA 2018)

> 코딩 교육 현장에서 목격한 "목표를 구체적으로 세운 학생이 더 잘 성장한다"는 가설을,  
> OECD PISA 2018 국제 데이터로 검증하고 성취도 예측 모델을 구현한 프로젝트

---

## 프로젝트 배경

방과후 코딩 교육 강사로 일하면서 학생들을 관찰한 결과,  
**"오늘 이 문제를 풀겠다"는 구체적 목표를 세운 학생**과  
**"그냥 열심히 하겠다"는 막연한 학생** 사이에 뚜렷한 성취 차이가 있었습니다.

이 프로젝트는 OECD PISA 2018 데이터(약 60만 명)를 활용해 이 가설을 데이터로 검증합니다.

**핵심 질문:**
> 목표 지향 방식(숙달목표 vs 수행목표)과 실패 두려움 수준이 수학 성취도를 얼마나 예측하는가?

---

## 데이터셋

- **출처**: [OECD PISA 2018 Database](https://www.oecd.org/pisa/data/2018database/)
- **대상**: 79개국 약 60만 명 학생
- **주요 변수**:

| 변수명 | 설명 |
|--------|------|
| MASTGOAL | 숙달목표 지향성 (배움 자체가 목적) |
| GFOFAIL | 실패에 대한 두려움 |
| SWBP | 주관적 웰빙 |
| BELONG | 학교 소속감 |
| PV1MATH ~ PV10MATH | 수학 성취도 (10개 추정값) |

---

## 분석 내용

### 1. 목표 유형 군집 분석 (K-Means Clustering)
- 학생들을 목표 지향 패턴으로 군집화
- 각 군집의 성취도 차이 비교

### 2. 목표변수 → 성취도 상관관계
- 숙달목표 / 실패두려움 / 소속감 × 수학 점수

### 3. 성취도 예측 모델
| 모델 | 목표 |
|------|------|
| Logistic Regression | 기준선 |
| Random Forest | 비선형 관계 포착 |
| XGBoost | 최고 성능 |

### 4. 교육 현장 시사점
- 코딩 교육에서 목표설정 방식이 학습 효과에 미치는 영향
- 효과적인 목표 유형 제안

---

## 실행 방법

```bash
# 1. 패키지 설치
pip install -r requirements.txt

# 2. 데이터 다운로드 (아래 링크에서 CY07_MSU_STU_QQQ.sav 다운로드)
# https://www.oecd.org/pisa/data/2018database/ → Student questionnaire data

# 또는 간편 버전: Kaggle PISA 2018 subset 사용
# https://www.kaggle.com/datasets/tunguz/student-questionnaire-pisa-2018

# 3. data/ 폴더에 저장 후 실행
jupyter notebook notebooks/goal_setting_analysis.ipynb
```

---

## 기술 스택

`Python` `pandas` `scikit-learn` `XGBoost` `matplotlib` `seaborn`

---

## 향후 계획

- [ ] 한국 학생 데이터 단독 분석 (국가별 비교)
- [ ] 코딩 교육 수강생 목표설정 설문 → 실제 학습 로그 매칭
- [ ] 목표 유형별 맞춤 피드백 시스템 설계
