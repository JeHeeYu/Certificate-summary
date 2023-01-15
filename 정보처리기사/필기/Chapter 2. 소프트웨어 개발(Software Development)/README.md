# 소프트웨어 개발 과목 정리 내용


## 자료 구조

### 자료 구조의 분류
* 선형 구조(Linear Structure)
  * 배열(Array)
  * 스택(Stack)
  * 큐(Queue)
  * 디큐(덱)
  * 선형 리스트(Linear List)
    * 연속 리스트(Contiguous List)
    * 연결 리스트(Linked List)
    

* 비 선형구조(Non-Linear Structure)
  * 트리(Tree)
  * 그래프(Graph)
  
### 선형 리스트(Linear List)

#### 연속 리스트(Contiguous List)
* <b>연속 리스트는 배열과 같이 연속되는 기억장소에 저장</b>되는 자료구조
* 기억장소를 <b>연속적으로 배정받기 때문에 이용 효율은 밀도가 1로서 가장 좋음</b>
* 중간에 데이터를 삽입하기 위해서는 연속된 빈 공간이 있어야 하며 <b>삽입 및 삭제 시 자료의 이동이 필요</b>

#### 연결 리스트(Linked List)
* <b>자료들을 연속적으로 배열시키지 않고</b> 임의의 기억공간에 기억, 자료 순서에 따라 노드의 포인터 부분을 이용하여 서로 연결시킨 자료 구조
* 노드의 <b>삽입 및 삭제 작업</b>이 용이
* 자료가 연속적으로 놓여 있지 않아도 저장 가능
* 연결 리스트 연결을 위한 링크(포인터) 부분이 필요
* 연결을 위한 포인터를 찾는 시간이 필요하므로 접근 속도가 느림
* 중간 노드 연결이 끊어지면 그 다음 노드를 찾기가 힘듦

### 스택(Stack)
스택은 리스트의 한쪽 끝으로만 자료의 삽입 및 삭제 작업이 이루어지는 자료 구조
<br>
스택은 가장 나중에 삽입된 자료가 가장 먼저 삭제되는 후입선출(LIFO, Last In First Out) 방식으로 자료를 처리
* 스택의 모든 공간이 가득 찬 상태에서 삽입 시 오버플로(Overflow) 발생
* 더이상 삭제할 데이터가 없는 경우에서 데이터 삭제 시 언더플로(Underflow) 발생

#### 스택의 응용 분야
* 함수 호출의 순서 제어
* 인터럽트의 처리
* 수식 계산 및 수식 표기법
* 컴파일러를 이용한 언어 번역
* 부 프로그램 호출 시 복귀주소 저장
* 서브루틴 호출 및 복귀 주소 저장

#### A, B, C, D로 정해진 입력 자료를 스택에 입력 후 B, C, D, A 순서로 출력하는 과정

![image](https://user-images.githubusercontent.com/87363461/212522358-0c211166-8de2-470c-a714-aec89ca74e78.png)
<br>

### 큐(Queue)
큐는 리스트의 한쪽에서 삽입 작업이 이루어지고 다른 한쪽에서는 삭제 작업이 이루어지는 자료 구조
* 큐는 가장 먼저 삽입된 자료가 가장 먼저 삭제되는 선입선출(FIFO, First In Last Out) 방식으로 처리
* 큐는 시작과 끝을 표시하는 두 개의 포인터가 있음

### 그래프(Graph)
* 방향 그래프
  * 정점을 연결하는 선에 <b>방향이 있는 그래프</b>
  * n개의 정점으로 구성된 <b>방향 그래프의 최대 간선 수 = n(n - 1)
* 무방향 그래프
  * 정점을 연결하는 선에 <b>방향이 없는 그래프</b>
  * n게의 정점을 구성하는 <b>무방향 그래프의 최대 간선 수 = n(n - 1) / 2</b>
  
### 트리(Tree)
트리는 정점(Node, 노드)과 선분(Branch, 가지)을 이용하여 사이클을 이루지 않도록 구성한 그래프의 특수한 형태
<br>
![image](https://user-images.githubusercontent.com/87363461/212522469-ac385ed2-a6eb-4d34-9e5f-b54c0492b23e.png)
<br>
* 노드(Node) : 트리의 기본 요소로서 자료 항목과 다른 항목에 대한 가지를 합친 것
  * Ex) A, B, C, D, E, F, G, H, I, J, K, L, M
* 근 노드(Root Node) : 트리의 맨 위에 있는 노드
  * Ex) A
* 디그리(Degree, 차수) : 각 노드에서 뻗어 나온 가지의 수
  * Ex) A = 3, B = 2, C = 1, D = 3
* 단말 노드(Terminal Node) = 잎 노드(Leaf Node) : 자식이 하나도 없는 노드, 즉 디그리가 0인 노드
  * Ex) K, L, F, G, M, I, J
* 자식 노드(Son Node) : 어떤 노드에 연결된 다음 레벨의 노드들
  * Ex) D늬 자식 노드 : H, I, J
* 부모 노드(Parent Node) : 어떤 노드에 연결된 이전 레벨의 노드들
  * Ex) E, F의 부모 노드 : B
* 형제 노드(Brother Node, Sibling) : 동일한 부모를 갖는 노드들
  * H의 형제 노드 : I, J
* 트리의 디그리 : 노드들의 디그리 중에서 가장 많은 수
  * Ex) 노드 A나 D가 3개의 디그리를 가지므로 잎 트리의 디그리는 3


### 트리의 운행법
* 전위(Preorder) 운행 : Root -> Left -> Right 순서와 같이 뿌리를 먼저 방문
  * A -> B -> C
* 중위(Inorder) 운행 : Left -> Root -> Right 순서와 같이 왼쪽 하위 트리를 먼저 방문
  * B -> A -> C
* 후위(Postorder) 운행 : Left -> Right -> Root 순서와 같이 하위 트리를 모두 방문 후 뿌리 방문
  * B -> C -> A
<br>

![image](https://user-images.githubusercontent.com/87363461/212522612-5460a944-ce3b-40ba-a755-b74494197a23.png)


<br>

### 트리 수식의 표기법
* 전위 표기법(PreFix) : 연산자 -> Left -> Right = +AB
* 중위 표기법(InFix) : Left -> 연산자 -> Right = A+B
* 후위 표기법(PostFix) : Left -> Right -> 연산자 = AB+
<br>

![image](https://user-images.githubusercontent.com/87363461/212522612-5460a944-ce3b-40ba-a755-b74494197a23.png)


<br>

---

## 정렬(Sort)

### 삽입 정렬(Insertion Sort) 
* 선택한 요소를 그보다 더 앞쪽의 알맞은 위치에 삽입하는 작업을 반복하는 정렬 알고리즘
* 정렬되지 않은 데이터가 있을 때 정렬되지 않은 첫 번째 요소를 정렬된 부분의 알맞은 위치에 삽입
* 정렬이 많이 이루어진 경우 효율적으로 사용 가능
* 정렬에 안정적이고 단순해서 구현이 쉬우나 시간 복잡도가 비효율적임

#### 삽입 정렬 예제
> 8, 5, 6, 2, 4를 삽입 정렬을 이용해 정렬

1. 초기 상태
<br>

![image](https://user-images.githubusercontent.com/87363461/212522709-ca7b1b84-e5c2-4936-b60a-fa02865d5af1.png)

<br>

2. 두 번째 값과 첫 번째 값을 비교
* 5를 첫 번째 자리에 삽입하고 8을 한 칸 뒤로 이동
<br>

![image](https://user-images.githubusercontent.com/87363461/212522725-48013a5d-ef48-422c-8e7a-df3d33e598a7.png)

<br>

3. 세 번째 값을 첫 번째, 두 번째 값과 비교
* 6을 8자리에 삽입 후 8을 한 칸 뒤로 이동
<br>

![image](https://user-images.githubusercontent.com/87363461/212522739-77b67527-544b-4c92-8278-99e45a5f1097.png)
<br>

4. 네 번째 값을 첫 번째부터 세 번째 까지의 값과 비교
* 2를 처음부터 비교, 가장 작으므로 맨 처음에 삽입하고 나머지를 한 칸씩 뒤로 이동

<br>

![image](https://user-images.githubusercontent.com/87363461/212522762-4964a452-6bac-42fd-975a-bf9cc88fc3dd.png)

<br>

5. 다섯 번째 값을 처음 부터 비교
* 4를 처음 자리부터 비교, 두 번째인 5자리에 삽입하고 나머지를 한 칸씩 뒤로 이동

<br>

![image](https://user-images.githubusercontent.com/87363461/212522775-741edda7-3722-48f9-83d9-9d0359052a68.png)

<br>


### 선택 정렬
* 가장 작은 요소부터 선택해 알맞은 위치로 옮겨서 순서대로 정렬하는 정렬 알고리즘
* 배열의 가장 작은 값을 찾아 맨 처음 요소와 위치를 변경하는 작업을 반복하여 정렬을 수행
* 같은 값이 있을 경우 상대적인 위치가 변경될 수 있어 안전하지 않음
* 배열의 크기를 알고 있기 때문에 이동 횟수를 미리 알 수 있다는 장점이 있음

1. 초기 상태
<br>

![image](https://user-images.githubusercontent.com/87363461/212522840-551ea73a-3c0f-4ed5-a8db-b128a9bc0031.png)

<br>

2. 가장 작은 값을 찾아 첫 번째와 변경
* 가장 작은 값인 2를 찾아 첫 번째 값 5와 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212522859-2dafc4b8-0b5e-4dd9-a4d8-244fb3d1f5d0.png)

<br>

3. 두 번째로 작은 값을 찾아 두 번째와 변경
* 두 번째로 작은 값은 4이므로 4를 찾아 두 번째 값인 6과 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212522923-0811ce49-7303-4627-9351-5fac1b2208e6.png)

<br>

4. 세 번째로 작은 값을 찾아 세 번째 값과 변경
* 세 번째로 작은 값은 5이므로 5를 찾아 세번째 값인 6과 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212522942-7440e7ca-923b-40d0-a636-0f475821beb2.png)

<br>

5. 마지막 값과 4번 째 값을 비교
* 마지막 값인 6이 8보다 작으므로 서로 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212522952-e7676e3e-8615-4720-bcdc-e5a7a860d055.png)

<br>

### 버블 정렬(Bubble Sort)
* 인접한 두 요소의 대소 관계를 비교하여 반복 교환
* 시간 복잡도가 느리지만, 코드가 단순하여 구현이 쉬워 자주 사용
* 요소의 개수가 n개인 배열에서 n - 1회 비교, 교환을 하고 나면 가장 작은 요소가 맨 처음 또는 끝으로 이동

1. 초기 상태

<br>

![image](https://user-images.githubusercontent.com/87363461/212523010-5ee89c07-4321-4b15-ba90-2b80e98d8174.png)

<br>

2. 첫 번째 부터 끝까지 값을 비교하여 서로 변경
* 5와 8 비교시 5가 더 작으므로 유지
* 8과 6 비교 시 6이 더 작으므로 변경
* 8과 2 비교 시 2가 더 작으므로 변경
* 8과 4 비교 시 4가 더 작으므로 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212523200-eda23091-1efe-4f6e-864b-ed317836c35b.png)

<br>

3. 첫 번째 부터 마지막 - 1 값 까지 비교하여 서로 변경
* 5와 6 비교 시 5가 더 작으므로 유지
* 6과 2 비교 시 2가 더 작으므로 변경
* 6과 4 비교 시 4가 더 작으므로 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212523250-49b21989-9de8-47f6-a905-63da5e9424f2.png)

<br>

4. 첫 번째 부터 마지막 - 2 값 까지 비교하여 서로 변경
* 5와 2 비교 시 2가 더 작으므로 변경
* 5와 4 비교 시 4가 더 작으므로 변경

<br>

![image](https://user-images.githubusercontent.com/87363461/212523282-8725d066-83f2-4bc2-b93e-becf9b9a83e9.png)

<br>

5. 첫 번째 값과 마지막 - 3 값 서로 비교
* 2가 더 작으므로 유지

<br>

![image](https://user-images.githubusercontent.com/87363461/212523302-5b2426c6-2f5c-48ba-a1c6-55c37a05e11f.png)

<br>
