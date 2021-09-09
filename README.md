# NLP Studies   
   
## NLP의 어려운 점 3가지 - 언어의 유동성 / 언어의 모호성 / 언어의 의존성   
    -언어의 유동성 : 빨갛다, 시뻘겋다, 불거스름하다 - Red
    -언어의 모호성 : 눈이 보인다
    -여기서 눈은 eye? snow?
    -언어의 의존성 : 나는 아침에 일어난다. (시간) / 나는 아침을 먹는다. (밥)
  
## NLP 핵심 과제 : 소규모의 데이터로 의미를 잘 이해하는 것!   
   
## 좋은 언어모델 만들기   자료 수집 -> 전처리(데이터 가공) -> 프리 트레이닝(Embedding) -> 파인 튜닝(모델 학습)   
   
# NLP trend   
1. Word encoding   
    -One hot encoding : 문장의 단어들을 숫자로 만들어 행렬로 표현한다. 예를 들어 '나는 회사에 매일 늦는다, 나는 회사에 간다' 를 0:나는 1:회사에 2:간다 3:매일 4:늦는다 로 만들면   '나는 회사에 간다' 는 [[1,0,0,0,0],[0,1,0,0,0],[0,0,1,0,0]] 로 표현할 수 있다. 허나 0이 많이 생기므로 효율적이라 할 수 없다.   
    - Bag of words : 이번에는 단어의 빈도 수로 표현한다. '나는 회사에 간다, 나는 회사에 매일 늦는다' 가 있다면, 나는:2 회사에:2 간다:1 매일:1 늦는다:1   덜 sparse 하지만 단어의 순서가 없어진다는 단점이 있다.   
2. Word embedding : 단어를 의미 있는 벡터로 만드는데 집중. 문장을 몰라도 주변 단어를 보고 유추할 수 있다.   
    - Word 2 vec  여기서 핵심은 BOW 와 Skip-gram 이다.
    - BOW : outer word를 보고 center word를 예측한다.
    - Skip-gram : center word를 보고 outer word를 예측한다.   
   
- GloVe - Word 2 vec이 통계적 자료를 잘 활용하지 못 한다 판단되어 고안해냄   
- FastText - Word 2 vec 에서 sub-word를 이용하여 오타, 유의어 모두 의미를 잡아냈다.   
ex) <wh,whe,he,her,ere> -> where   
-Transfer learning(전이 학습)  : pre training 한 단어의 의미적 문법적 관계 정보 등을 활용해 다양한 task에 활용   
    = Language model  : 문장의 확률을 예측하거나, 이전 단어를 기반으로 다음 단어가 나올 확률을 예측   
3. Sentence embedding : 단어의 의미는 문맥에 따라 달라지므로 단순히 단어를 벡터로 표현하는 것은 의미를 표현하기 불충분하므로 문맥을 고려한 embedding을 고안해냈다.   
- ELMO
- GPT
- BERT
- MLM (Machine Language Model) : 15%를 [Mask]로 구성   
    - 발 없는 말이 [Mask] 간다.  80%
    - 발 없는 말이 천리 간다.
    - 발 없는 말이 냉장고 간다.  10%
    - 발 없는 말이 천리 간다.    10%   
- NSP (Next Sentence Prediction)
