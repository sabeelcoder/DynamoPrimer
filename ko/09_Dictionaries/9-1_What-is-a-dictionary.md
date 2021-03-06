# 사전
Dynamo 2.0에서는 사전 데이터 유형을 리스트 데이터 유형과 분리하는 개념을 도입했습니다. 이러한 변경으로 인해 워크플로우에서 데이터를 작성하고 사용하는 방법도 크게 달라질 수 있습니다. 2.0 이전에는 사전과 리스트가 데이터 유형으로 결합되어 있었습니다. 간단히 말해, 리스트는 실제로 정수 키가 있는 사전이었습니다.

* #### 사전이란 무엇입니까?
사전은 각 키가 각 모음에서 고유한 키-값 쌍 집합으로 구성된 데이터 유형입니다. 사전에는 순서가 없으므로 기본적으로 리스트의 경우처럼 색인 값 대신, 키를 사용하여 "항목을 조회"할 수 있습니다. *Dynamo 2.0에서 문자열만 키가 될 수 있습니다.*

* #### 리스트란 무엇입니까?
리스트는 정렬된 값의 모음으로 구성된 데이터 유형입니다. Dynamo에서 리스트는 정수를 색인 값으로 사용합니다.

* #### 이렇게 변경된 이유와 주의해야 하는 이유는 무엇입니까?
리스트에서 사전을 분리하면서 사전이 일급 객체가 되었고, 사전을 사용하여 색인 값을 기억하거나 엄격한 리스트 구조를 유지할 필요없이 전체 워크플로우에서 빠르고 쉽게 값을 저장하고 조회할 수 있게 되었습니다. 사용자 테스트를 통해 ```GetItemAtIndex``` 노드 대신 사전을 활용할 때 그래프 크기가 크게 감소된 것을 확인할 수 있었습니다.

* #### 어떤 변화가 있습니까?
  * *구문*이 변경되었으며 이로 인해 코드 블록에서 사전 및 리스트를 초기화하고 사용하는 방법도 달라졌습니다.
    * 사전은 구문 ```{key:value}```를 사용합니다.
    * 리스트는 다음 구문 ```[value,value,value]```를 사용합니다.
  * 사전을 작성, 수정 및 조회할 수 있도록 *새 노드*가 라이브러리에 추가되었습니다.
  * 1.x 코드 블록에서 작성된 리스트는 스크립트를 로드할 때 중괄호 ```{ }``` 대신 대괄호 ```[ ]```를 사용하는 새 리스트 구문으로 자동으로 마이그레이션됩니다. ![IMAGE](images/9-1/DYN20_Dictionary.png)

* #### 주의해야 하는 이유는 무엇입니까? 리스트를 어디에 사용할 수 있습니까?
컴퓨터 과학에서 리스트와 같은 사전은 객체 모음을 의미합니다. 리스트는 특정 순서로 나열되지만, 사전은 *정렬되지 않은* 모음입니다. 순차적인 번호(색인)를 사용하지 않고 대신 *키*를 사용합니다.

아래 이미지는 사전의 잠재적인 사용 사례를 보여줍니다. 사전은 직접적인 상관 관계가 없을 수도 있는 두 가지 데이터 조각을 연관 짓는 데 사용되는 경우가 많습니다. 여기에서는 나중에 조회할 수 있도록 스페인어 버전 단어를 영어 버전에 연결합니다. ![IMAGE](images/9-1/9-1_dictionaryExample.png)

