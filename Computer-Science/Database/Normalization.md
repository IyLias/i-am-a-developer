
### What is Database Normalization?

![Untitled (19)](https://github.com/IyLias/i-am-a-developer/assets/48081162/24b2b30c-3814-49b6-af6d-13ba91ceb99b)


정규화 작업을 통해 관계형 데이터베이스를 정규형 normal forms 으로 바꾸고 이 과정에서 data redundancy 데이터 중복 문제와 data integrity 데이터 무결성을 향상시킨다. 


<br><br>

### 1NF : 제 1 정규형

![Untitled (20)](https://github.com/IyLias/i-am-a-developer/assets/48081162/7696eddb-740f-4657-a461-4e184c60415f)


간단하다. 각 어트리뷰트 값이 atomic 해야한다. 따라서 위의 사례는 제 1 정규형을 만족하지 않는다. 

![Untitled (21)](https://github.com/IyLias/i-am-a-developer/assets/48081162/d5fec5ff-715b-4030-a3b9-67a0a6d6d7df)


해결책으로는 별도의 릴레이션을 만들어주는 방법이 있겠다. 


<br><br>

### 2NF : 제 2 정규형

![Untitled (22)](https://github.com/IyLias/i-am-a-developer/assets/48081162/92520d8f-2790-46a4-ad58-499fabb1464c)


제 2 정규형을 만족하기 위한 두 가지 조건이 필요하다. 

- 우선 제 1 정규형을 만족해야한다.
- 릴레이션의 후보키의 진부분집합들에는 어떠한 함수적 종속성도 존재하지 않아야한다.

<br>
만약 테이블이 하나의 어트리뷰트로 구성된 primary key를 가진다면 자동적으로 2NF를 만족한다. 하지만 2개 이상의 composite key를 가진다면 위반의 가능성이 생긴다. 

그래서 제 2정규형을 만족시키기 위해 테이블을 분해하는 알고리즘을 정리하면 아래와 같다. 

<br>

좀 더 정확히 강의 자료를 참고하여 설명하면 

1) 부분 종속성을 만족하는 그러니까 non-prime 어트리뷰트를 기존 릴레이션에서 삭제한다. 그러면 일단 테이블이 하나 나온다. 

2) 그리고 삭제한 어트리뷰트와 함수적 종속성을 가졌던 그 어트리뷰트를 결합한 릴레이션을 하나 만들어 준다. 

<br>
이렇게 분해를 하면 제 2정규형을 만족하게 된다. 

<br>
1) 아래 사례를 통해 살펴보자.

![Untitled (23)](https://github.com/IyLias/i-am-a-developer/assets/48081162/9c2978ac-6487-42a9-b3f8-1e4a8f41808b)


우선 Manufacturer와 Model이 기본키이다. 

그리고 제1정규형을 만족한다. 그런데 후보키의 진부분집합인 Manufacturer를 통해서 Manufacturer country를 결정짓는다.  Manufacturer → Manufacturer Country 

이는 제 2정규형 두 번째 조건을 위반한다. 

<br>
2) 또 하나의 예시 

![Untitled (24)](https://github.com/IyLias/i-am-a-developer/assets/48081162/e915c062-d81f-4bdd-8dfe-ff0f2c284ba2)


이걸 보고 이해가 확 된 것 같다. 

후보키의 진부분 집합과 후보키에 전혀 속하지 않은 어떤 어트리뷰트 간에 종속성이 생기면 중복의 가능성이 생긴다. 그래서 이는 제 2정규형을 위반하고 이를 해결하기 위해 종속성이 생기는 부분을 테이블로 따로 하나 만들고 나머지 부분들을 또 나눈다. 

<br>
3) 마지막 사례 하나 더 

![Untitled (25)](https://github.com/IyLias/i-am-a-developer/assets/48081162/304632a5-7f1e-4885-9f0e-59e98b73e362)


해당 테이블에서 후보키는 Title 이랑 Format 이고 후보키의 진부분집합인 Title은 price를 제외하고 다른 모든 어트리뷰트들과 종속성을 이룬다. 이는 제 2정규형 위반이다. 

그래서 후보키와 price를 제외한 나머지 어트리뷰트들을 삭제하여 테이블을 하나 구성한다. 

그리고 삭제한 어트리뷰트들과 그와 종속성을 이룬 진부분집합인 Title을 합쳐서 테이블을 또 하나 구성한다. 

이렇게 분해하면 제 2정규형을 만족하게 된다. 


### References

깔끔한 한글 자료 

[[Database] 정규화(Normalization) 쉽게 이해하기](https://mangkyu.tistory.com/110)


<br><br>
### 3NF : 제 3 정규형

첫번 째 정의 (수업 때 다룬 정의) 
![Untitled (26)](https://github.com/IyLias/i-am-a-developer/assets/48081162/dcc3a313-dea4-49fe-8db8-69584325da66)


함수 종속성 F와 그의 폐포 $F^+$에 대해서 그에 속한 모든 종속성들에 대해서  

각각이 다음 3개의 조건 중 최소 하나를 만족하면 제 3 정규형을 만족한다고 한다. (즉 각각의 모든 종속성들이 다음 3 조건 중 최소 하나는 만족해야한다)

⇒ 다만 이 방식에 대한 나의 의문은 해당 스키마의 모든 함수 종속성에 대해서 검사를 해줘야하는데 이걸 어떻게 종속성을 다 찾을 것이며 그 각각의 종속성에 대해서 위 3개의 조건을 또 검사해줘야 하는데.. 좋은 방법이 맞는 건가?

물론 문제에서 모든 함수 종속성이 주어졌다면 위 방식대로 하면 더 수월하게 결론낼 수 있는 것은 분명하다. 

두 번 쨰 정의 

![Untitled (28)](https://github.com/IyLias/i-am-a-developer/assets/48081162/bdbdee1f-4873-42f0-ab9d-863484893512)



1) 아래 사례를 통해 살펴보자 

![Untitled (29)](https://github.com/IyLias/i-am-a-developer/assets/48081162/9e126087-69b0-4b7d-8543-de51f8821b92)


위 테이블이 제 3 정규형을 만족하는 지 알아내는 방법은 위처럼 2가지 방법이다. 

우선 첫 번째 강의 슬라이드 정의에 따르면 위 테이블에서 찾을 수 있는 함수 종속성 중 winner → winner’s date of birth를 보면 우선 nontrivial 하고, winner는 슈퍼키가 아니며 그리고 B-A 인 winner’s date of birth 는 후보키에 포함되지 않는다. 따라서 3 조건을 모두 만족하지 않으므로 제 3 정규형을 만족하지 않는다. 

두번 째 정의에 의해 검사하면 우선 제 2정규형은 만족한다.(진부분집합들이 어떤 종속성도 이루지 않는다) 다만 winner → winner’s date of birth라는 종속성이 primary key → Winner 를 통해 이행적 종속성을 이루게 된다. 

즉 제 3 정규형이 아닌 것이다. 

위키에 올라와있는 동일한 문제 

![Untitled (30)](https://github.com/IyLias/i-am-a-developer/assets/48081162/cf258cb4-16cf-4155-bf28-8a10d10f83da)


2) 강의 슬라이드 사례 

참고할 부분은 앞의 두 조건은 BCNF의 조건과 동일하다. 

![Untitled (31)](https://github.com/IyLias/i-am-a-developer/assets/48081162/21e4b530-b5bc-4b2c-aee3-4859de40ec2b)


예시를 통해 살펴보면 위 dept_advisor 스키마는 BCNF는 안되지만 제 3 정규형은 만족한다. 

문제에서 종속성이 전부 주어졌으므로 각 종속성에 대한 조건만 검사해주는 식으로 하면 된다.



### BCNF

![Untitled (32)](https://github.com/IyLias/i-am-a-developer/assets/48081162/d76a8ea0-fad3-45f9-91d4-57ff2d5b787f)


함수 종속성 F와 그의 폐포 $F^+$에 대해서 그에 속한 모든 종속성들에 대해서  

둘 중 최소 하나를 만족하면 BCNF를 만족한다. 

- $\alpha$ →$\beta$ 가 trivial 하다.
- $\alpha$ 는 $R$의 슈퍼키 superkey 이다.

사실 위 두 조건은 전부 다 자명하다. 

$\alpha$가 슈퍼키라면 $\beta$에 뭐가 오든 전부 다 결정할 수 있기 때문에 당연한 말이고 ㅇㅇ
