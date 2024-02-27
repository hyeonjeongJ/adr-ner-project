
BERT+ 알고리즘 기반 약물 리뷰를 활용한 약물 이상 반응 탐지

약물의 시판 후 이상 반응을 모니터링하기 위해 약물 리뷰 데이터로부터 약물 이상 반응을 탐지할 수 있는 방법을 제시한다. 부정적인 약물 리뷰는 주로 약물 이상 반응을 언급하고 있다는 점을 고려하여 약물 리뷰들을 감성 분석하여 부정 리뷰를 추출했다. 약물 리뷰는 다른 소셜 미디어 데이터에 비해 그 내용이 긴 편이고, 각 문장마다 다른 극성을 가질 수 있기 때문에 BERT+ 알고리즘을 개발하여 문맥 기반 감성 분석을 실시하였다.
제안하는 BERT+ 알고리즘은 기존의 BERT 알고리즘으로 분류되기 어려운 중립에 가까운 리뷰나 약물 이상 반응 용어가 증상으로 사용된 경우 등도 효율적으로 판별할 수 있다.

제안하는 BERT+ 알고리즘으로 부정 리뷰를 판별한 다음, MedDRA 표준 의학 용어 사전을 활용해 이상 반응 단어를 찾고, 개체명 인식 기법을 사용하여 구로 표현된 이상 반응 표현을 탐지하였다. 실험을 위해 비스테로이드성 소염진통제 세 종류의 약물 리뷰를 약물 리뷰 사이트로부터 수집하여 테스트하였으며, 실험 결과는 약물 리뷰를 통한 약물 이상 반응 탐지가 현재의 약물 감시 체계의 한계점을 보완할 수 있음을 보여준다.

1116label.csv: BERT 알고리즘 훈련에 사용된 데이터. KUC Hackathon 데이터 중 평점이 1~2점인 데이터와 10점인 데이터의 일부를 사용

celecoxib.csv, naproxen.csv, ibuprofen.csv: drugs.com, everydayhealth.com, askapatient.com, iodine.com, webmd.com에서 수집한 약물 리뷰 데이터.

terms.txt: 사전기반 방식에서 사용된 MedDRA 용어

test.txt: 개체명 인식 모델의 훈련 데이터인 CADEC 데이터로 단어와 태그 형식으로 되어있음

BERT+.ipynb: 코드의 구성은 다음과 같다.
- BERT 모델 훈련
- BERT를 통한 celecoxib, naproxen, ibuprofen 감성 분석 (BERT+와의 비교를 위해)
- BERT+를 통한 celecoxib, naproxen, ibuprofen 감성 분석

dictionary_based_method.ipynb: 사전 기반 방식의 약물 부작용 탐지 코드

NER_based_method.ipynb: 코드의 구성은 다음과 같다.
- CADEC 데이터를 활용해 개체명 인식 기반의 약물 부작용 탐지 모델 구축
- 구축한 모델에 celecoxib, naproxen, ibuprofen의 리뷰를 적용해 약물 부작용 표현 
