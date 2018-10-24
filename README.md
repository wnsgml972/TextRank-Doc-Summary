## TextRank-Doc-Summary


## 분석 동기

블로그를 운영하는 블로거로서 만약 블로그를 자동으로 요약해서 글 제일 위에 나타낼 수 있다면
읽으러 오는 사람에게 얼마나 좋을까? 생각에 문서를 요약하는 프로그램을 생각하게 되었습니다.

<br/><br/>

## Step 1. 필요한 패키지 설치

* ```pip install newspaper3k``` # url 크롤링 패키지
* ```pip install jpype1```
* ```pip install konlpy``` # 한글 형태소 분석기
* ```pip install scikit-learn``` # TF-IDF를 위한 머신러닝 패키지

<br/>

## Step 2. 데이터 수집

![2](/img/1.png)

1. url을 이용해 문장을 추출하거나, text를 직접 입력해 문장을 추출합니다.

2. TF-IDF 모델을 만들기 위한 전처리 과정을 합니다.

불용어를 추가하여 twitter를 이용해 문장으로 분리 한 뒤 문장을 형태소 단위로 나눈 후 품사 태
깅을 통해 명사들만 추출합니다.

<br/>

## Step 3. 머신러닝을 이용하여 문장의 가중치 그래프 만들기

1. TF-IDF 모델 생성

문서에서 단어의 중요성을 계산하여 단어를 추출하는 TF-IDF를 이용합니다. <br/><br/>

![3](/img/2.png)

TF-IDF를 계산하기 위해 머신러닝 패키지인 scikit-learn을 이용합니다

2. 그래프 생성

TextRank를 적용시키기 위해 생성된 문장의 가중치 그래프를 만듭니다.

![3](/img/3.png)

<br/>

## Step 4. TextRank를 이용한 텍스트 요약

![4](/img/4.png)

1. 위의 공식을 이용한 알고리즘 적용

![4](/img/5.png)

2. 문서를 요약해주는 함수 생성 (default = 3줄)

![4](/img/6.png)

3. 문서의 키워드를 리턴 해주는 함수 생성 (default = 10단어)

![4](/img/7.png)

<br/>

## Step 5. 검증

1. 파이선 GUI tkinter를 이용하여 문서요약시스템을 보다 쉽게 사용할 수 있도록 구현하였
습니다.
2. 문서요약은 8줄로 되도록 만들었으며 단어는 default인 10개의 단어가 나오도록 하였습니
다.
3. mqtt 프로토콜을 분석하여 정리한 제 블로그 주소입니다.<br/>
url : https://wnsgml972.github.io/wnsgml972.github.io/mqtt/mqtt.html

![4](/img/8.png)
