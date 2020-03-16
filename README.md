# MULTI GPU환경에서 ETRI 한국어 BERT모델 활용한 감정 분류기 
문장이 주어졌을 떄 5가지의 감정(기쁘다, 놀라다/황당하다, 화나다, 슬프다, 수치스럽다)으로 분류하는 모델입니다.

각 형태소가 결과에 어떤 영향을 주는지 Heatmap을 이용하여 시각화하였습니다.  

학습데이터 사이즈는 **460K** 입니다. 

**Example)**

밥을 든든히 먹어서 매우 기분이 좋다.  :   기쁘다

오늘 여자 친구랑 싸웠어.   :   화나다

오늘은 월급날이다.   :   기쁘다

머리가 많이 아프다.   :   슬프다

친구들이랑 같이 놀러가기로 했다.   :   기쁘다

누가 갑자기 다가와 어깨를 쳤다.   :   놀라다/황당하다

아버지가 많이 아파서 병원에 갔다.   :   슬프다

오늘의 공연은 형편 없었다.    :   화나다 

나는 밥을 먹었다.   :    중립

저 동물의 이름은 늑대이다.   :   중립

## Requirements
Python3.6

tensorflow==1.14.0 

urllib3


## 실행방법 

**step 0. BERT classification dataset 형식처럼 "입력\t정답" 형태의 tsv 데이셋을 만들어주세요** 

**step 1. [Mecab 형태소분석기](https://github.com/Gyunstorys/nlp-api) API 설치합니다.**

**step 2. ETRI_pretrained directory 만들어서 ETRI pretrained model checkpoint 저장합니다.**

**step 3. shell script path 바꿔줍니다. (docker 사용하면 mount 시킬 volume의 source path 만 바꿔주세요.)**

BERT_BASE_DIR 를 clone 하신 path로 바꿔주세요 
    
**step 4. 실행합니다.**

    ./run_classifier_ETRI.sh

## Korquad Result (test set)

| model | eval_accuracy  |   eval_loss | 
| ------ | ------ | ------ | 
|ETRI+mecab| 65.05 | 1.303 |

## Hyperparameters 

batch size : 8*8

learning rate : 8.5e-5

epoch : 2.3

학습시간 : 120min

GPU : TITAN V  (12066MiB) * 8
