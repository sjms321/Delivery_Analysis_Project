

# 서울시 자치구별 월소득과 종류별 배달량의 상관관계 분석

##  프로젝트 목적

- 서울시 자치구별 월소득과 종류별 배달량의 상관관계 분석
- 배달량에 관한 새로운 데이터 추출
- 배달량과 상관관계가 존재하는 요소 파악





## 사용언어 및 주요 패키지

![image-20210706173623209](https://user-images.githubusercontent.com/67422547/124581801-68cd3a00-de8c-11eb-87f6-87e48e20062a.png)

## DATA



![image-20210706174254934](https://user-images.githubusercontent.com/67422547/124581974-8e5a4380-de8c-11eb-94f3-58afca3ae93d.png)



## 데이터전처리





![image-20210706180621265](https://user-images.githubusercontent.com/67422547/124582108-acc03f00-de8c-11eb-9c94-ef80c9c7b45c.png)

``` python
import pandas as pd
import numpy as np
missing_values = ["배달전문업체","심부름"]
df = pd.read_csv("seoul_delivery.csv",na_values = missing_values)
df = df.filter(['업종','시군구','통화건수'])
df_grouped=df.groupby(['업종','시군구'])
df_grouped['통화건수'].sum()
```



![image-20210706181003613](https://user-images.githubusercontent.com/67422547/124582140-b5b11080-de8c-11eb-9d55-d1d818167837.png)

``` py
GDP_seoul = pd.read_csv('report.txt',sep='\t')
GDP_seoul=GDP_seoul.filter(['자치구','인구수','월소득'])
```

![image-20210706180246580](https://user-images.githubusercontent.com/67422547/124582196-c2cdff80-de8c-11eb-9ae8-aeff7a93737a.png)



**<span style="color:red">다양한 데이터 정재를 통해 필요한 데이터를 분류별로 넣은 하나의 Data Frame 완성!</span>**







## Analysis



**<span style="color:red">전처리를 통해 얻은 Data frame를 각종 python 패키지들을 통해 데이터 시각화</span>**

![image-20210706180303246](https://user-images.githubusercontent.com/67422547/124582212-c95c7700-de8c-11eb-9506-fa0e5f181e4f.png)

```
첫 번째로 지역구별 월소득과 총배달량의 상관관계입니다.
대략적으로 상승선을 타지만 예외 지역들이 존재합니다.
```



![image-20210706180310196](https://user-images.githubusercontent.com/67422547/124582242-ceb9c180-de8c-11eb-8557-1d587d9217c4.png)

```
앞선 데이터를 음식의 종류별로 나누어서 시각화하면 이 역시 대략적인 상승세를 보이지만 
음식 종류에 따라 다른 상승세를 보이지 않습니다.
```



![image-20210706180333360](https://user-images.githubusercontent.com/67422547/124582255-d4170c00-de8c-11eb-9f47-b20dcdb6a098.png)

``` 
종류에 영향을 미치는 요소가 월소득말고 어떤것이 있을까 찾아보기위해 상관관계를 알 수 있는 heatmap을 그려 보았습니다.
heatmap을 통해 인구수가 종류별로 다른 상관관계를 나타낸다는 것을 알게 되었습니다.
```

![image-20210706180340535](https://user-images.githubusercontent.com/67422547/124582273-d9745680-de8c-11eb-9023-40d0d6ee39c1.png)

```
상관관계가 가장 차이나는 치킨과 중식을 비교하기 위해 시각화 하였습니다. 
치킨은 상승선을 그리는 반면, 중식은 평이한 선을 그리고 있습니다.
```



## 결과

![image-20210706190946680](https://user-images.githubusercontent.com/67422547/124583195-bf874380-de8d-11eb-9b47-d404ed81c2fb.png)

``` 
월소득 인구수 치킨 세가지 요소를 3차원 그래프로 그려 서울시내에 가장 치킨집에 적합한 세지역을 선별하였다
--> 강서 강남 송파
```



- **월소득과 배달량의 상관관계가 존재한다.**

- **배달 음식 종류별 차별점은 존재하지 않는다**

- **종류별 음식과 상관관계가 있는 변수 탐색**

- **탐색 변수(인구수) 와 종류별 음식의 상관관계 파악**



## 보완점

- **인구수와 치킨의 관계 원인 파악.**
- **비례에 따르지 않는 지역의 존재 원인.**
- **한정적인 지역 선별**