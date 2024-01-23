머신러닝 활용 현금흐름 중심 기업수명주기를 고려한 부실예측모형 연구
====================
(상장 중소기업과 비상장 외감중소기업 비교 중심)
-----------------------------

# 서론
## 기획배경
중소기업은 현금유동성이 중요하다
## 선행연구
## 차별점
상장중소기업과 비상장외감중소기업의 부실예측비교 연구
## 부실정의
- 조건 1 : 3년 연속 이자보상배율 1미만
- 조건 2 : 3년 연속 영업현금흐름 음수
- 조건 3 : 감사의견 거절 혹은 부적정ㄴㄴ
## 기업수명주기 (현금흐름관련) 정의
- 도입기 : 영업현금흐름 (-), 투자현금흐름 (-), 재무현금흐름 (+)
- 성장기 : 영업현금흐름 (+), 투자현금흐름 (-), 재무현금흐름 (+)
- 성숙기 : 영업현금흐름 (+), 투자현금흐름 (-), 재무현금흐름 (-)
- 쇠퇴기 : 영업현금흐름 (-), 투자현금흐름 (+), 재무현금흐름 (±)  
## 연구대상은 상장 중소기업과 비상장 외갑 중소기업
- 한국상장협의회 참조

# 본론 Workflow
## 1_데이터 수집 및 전처리
- 3년 연속 재무데이터 보유
- 회계월이 12월
### 1_1. 부실판단
1. 3년 연속 이자보생배율 1미만
2. 3년 연속 영업현금흐름 음수
3. 감사의견 거절 혹은 부적절
위의 조건중 하나라도 해당되면 부실(1) 
### 1_2. 현금흐름 기업수명주기판단
- 영업현금흐름 (-), 투자현금흐름 (-), 재무현금흐름 (+) = 도입기
- 영업현금흐름 (+), 투자현금흐름 (-), 재무현금흐름 (+) = 성장기
- 영업현금흐름 (+), 투자현금흐름 (-), 재무현금흐름 (-) = 성숙기
- 영업현금흐름 (-), 투자현금흐름 (+), 재무현금흐름 (±) = 쇠퇴기
쇄신기는 제외. 제외이유는 발표자료 참고
### 1_3. 파생변수 생성
### 1_4. train_test_split
1 : np.exp(1)
탐색적 데이터 분석(EDA; Exploratory Data Analysis)은 수시로 한다.
### 1_5. 결측치 처리
1. inf는 max로 대체, -inf는 min으로 대체   
2. 정규성 검사   
    - 정규성 -> fillna(mean 평균)    
    - 정규성X -> fillna(median 중앙값)
### 1_6. 이상치 처리 -> Winaorizing
기업수명주기별 부실별 Q-Qplot   
일괄 양쪽 1%
### 1_7. Resampling;  (∵ 데이터 불균형)
- Undersampling(쌍대표본방식) 기업수명주기별 정상과 부실의 표본 수 일치   
- Oversmapling(SMOTE) 기업수명주기별 정상과 부실의 표본 수 일치   

## 2_Feature Selection
### 2_1. filter : t-test(p-value 0.05)
### 2_2. scaling : minmax, standard
### 2_3. wrapper : backward
### 2_4. embedded : LASSO(데이터셋 별 a 값 상이)

## 3_Modeling
Logistic regression, RandomForest, Boosting, Bagging, LightGBM, XGboost, adaboost, Suport Vector Machine_linear & rbf
## 4_Robustic 강건성평가
winsorizing과 Resampling 되기 전 원본데이터
# 결론 Insight
발표자료 참고
![image](https://github.com/jyoooonh/Project2/assets/87022534/5c4678b5-570b-46b6-a55d-7a7c207809e9)
![image](https://github.com/jyoooonh/Project2/assets/87022534/8f907bfb-2856-4c76-9047-307511587011)
![image](https://github.com/jyoooonh/Project2/assets/87022534/8aa4e188-654f-43a6-b5ef-d5a0d7d0cebc)
![image](https://github.com/jyoooonh/Project2/assets/87022534/4f30c692-92ec-47a5-a545-a842f7d2828e)
![image](https://github.com/jyoooonh/Project2/assets/87022534/61bbbfd2-087d-4280-95e7-84fbd15fcfbd)
![image](https://github.com/jyoooonh/Project2/assets/87022534/2ce9b646-28b2-40a4-8d77-0e275fa1fc23)
![image](https://github.com/jyoooonh/Project2/assets/87022534/c99fdd05-6ecf-4281-b350-a8d5dd03cfd7)
![image](https://github.com/jyoooonh/Project2/assets/87022534/569dc94e-f766-463f-b907-b7d5753f3e7c)
![image](https://github.com/jyoooonh/Project2/assets/87022534/cbaf6eb4-52cf-4b4f-aebe-b80f5e47066f)
![image](https://github.com/jyoooonh/Project2/assets/87022534/e5d3cfa6-4f28-4b0d-aac3-00408863b7b4)
![image](https://github.com/jyoooonh/Project2/assets/87022534/ef58f7b5-1714-44ae-9062-bf7486459f7d)
![image](https://github.com/jyoooonh/Project2/assets/87022534/d049e852-4a84-419a-81e9-3e6ee47f1b80)
![image](https://github.com/jyoooonh/Project2/assets/87022534/07a9f8fc-bf87-4bb7-b4bf-5dbeb1d6ff62)
![image](https://github.com/jyoooonh/Project2/assets/87022534/7e8843f8-0926-49bc-b487-9f04d85f48ed)
![image](https://github.com/jyoooonh/Project2/assets/87022534/e03909e9-489f-4782-8993-e64aa71c696b)
![image](https://github.com/jyoooonh/Project2/assets/87022534/d185e9ff-eec9-45fb-9937-e9d0562e0855)
![image](https://github.com/jyoooonh/Project2/assets/87022534/3a234e81-e2dc-47e7-8d72-6c34f7a7fa97)
![image](https://github.com/jyoooonh/Project2/assets/87022534/e1a6019a-5751-4b0c-9d32-48441f4bd3a2)
![image](https://github.com/jyoooonh/Project2/assets/87022534/d037bb5f-80ad-4408-818e-55b4eaf202d2)
![image](https://github.com/jyoooonh/Project2/assets/87022534/b50e2d09-9a35-4558-84cd-96d412bc5241)
![image](https://github.com/jyoooonh/Project2/assets/87022534/b0b70fa1-6c4f-4b20-8c45-461b66676f97)
![image](https://github.com/jyoooonh/Project2/assets/87022534/cd9fd579-8a46-4735-83e9-003b6e8eaef5)
![image](https://github.com/jyoooonh/Project2/assets/87022534/9493444c-cb25-4c83-97c6-f76353ce8976)
![image](https://github.com/jyoooonh/Project2/assets/87022534/622ca7f6-f5b1-40cf-983a-de02d5997e2f)
![image](https://github.com/jyoooonh/Project2/assets/87022534/12c3d516-ad05-41c7-94da-aba56976c7da)
![image](https://github.com/jyoooonh/Project2/assets/87022534/8c3c9a1b-0726-4cba-a5c1-759b9eba36a9)
![image](https://github.com/jyoooonh/Project2/assets/87022534/f1153c98-0345-4fef-8660-56e1bfd4ef3b)
![image](https://github.com/jyoooonh/Project2/assets/87022534/ca0f571d-4d4e-4180-8181-4d2c743bb4b9)
![image](https://github.com/jyoooonh/Project2/assets/87022534/e696ac4d-2e37-4ed5-bf26-0df17338f11d)
![image](https://github.com/jyoooonh/Project2/assets/87022534/e2b70bf2-3ea4-4e1a-9144-197e1bf50255)
![image](https://github.com/jyoooonh/Project2/assets/87022534/1d601c9d-5e07-4b06-a630-dd2d8d7463e7)
![image](https://github.com/jyoooonh/Project2/assets/87022534/6bc5faf8-92f6-408e-a886-5cff976858f9)
![image](https://github.com/jyoooonh/Project2/assets/87022534/ce9f15a5-5fe3-4d87-85cb-3863328acfd4)
![image](https://github.com/jyoooonh/Project2/assets/87022534/c6ea082d-0582-4cb4-8c5a-bced4bc45688)
![image](https://github.com/jyoooonh/Project2/assets/87022534/abf80ce4-d17b-41e3-b163-b16447bacb46)
![image](https://github.com/jyoooonh/Project2/assets/87022534/35c6a8f6-0167-4b4f-9e80-b1430e3d61a8)
![image](https://github.com/jyoooonh/Project2/assets/87022534/331f2366-a5d1-4bec-b309-0da8b68ac45b)
![image](https://github.com/jyoooonh/Project2/assets/87022534/97aed128-0b4a-49ad-9e75-b43c3530740a)
![image](https://github.com/jyoooonh/Project2/assets/87022534/956656f2-7194-48ab-9eaf-c59ad070819c)
![image](https://github.com/jyoooonh/Project2/assets/87022534/f8ceef2b-334b-400b-a554-4c09e2392d05)
![image](https://github.com/jyoooonh/Project2/assets/87022534/c742a387-60ac-44a8-9ed3-21498fd0512f)
![image](https://github.com/jyoooonh/Project2/assets/87022534/0101dc66-3a1f-4eba-b188-a214014a60f3)
![Uploading image.png…]()









