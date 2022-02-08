# Belief-desire-intention software model
From Wikipedia 번역

&nbsp;BDI(Belief-desire-intention) 소프트웨어 모델은 지능형 에이전트로 프로그래밍을 위해 개발 된 합리적인 소프트웨어 에이전트이다.
에이전트의 믿음 상태(beliefs), 목적(desires), 의도(intention)의 구현이 특징이다.

&nbsp;BDI 모델은 현재 활성화된 계획의 실행과 계획 라이브러리 혹은 외부 계획자 응용프로그램(planner application)으로 부터 계획을 선택하는 것을 분리를 위한 방법론을 제공한다.

&nbsp;BDI의 특징은 계획 선택을 고려하고, 계획을 실행하는데 소요되는 시간의 균형을 맞춘 것이 특징이다. 계획 모델은 시스템 설계자 및 프로그래머에 의해 수동적으로 작성된다.

### Overview

&nbsp;계획 선택의 고려와 실행의 분리를 달성하기 위해 BDI 모델은 Michael Bratman의 믿음, 목적, 의도의 개념을 구현한다. 믿음과 목적은 행동과 관련된 태도이지만 의도는 행위를 통제하는 태도이다. Bratman은 목적은 계획들에서의 일시적인 지속성, 의도는 이미 수행되고 있는 계획에 기초하여 추가 계획을 수립한다고 정의 하였다. 

&nbsp;BDI 모델에서 일시적인 지속성은 시간에 대한 명시적 참조의 의미에서 탐구 되지 않는다. 계획은 계층적 구조로 이루어져 있으며 일부 게획은 다른 계획을 호출 할 수 있다. 계획의 하위 계획이 실행 되는 동안 상위 계획은 유효하므로, 이것은 일시적 지속성을 의미 한다.

### Architecture
* Beliefs : Beliefs(신념)은 에이전트의 상태를 정보적으로 표현한다. 즉 에이전트가 작동되고 있는 상태에 믿고 있는 신념이다. 신념은 추론 규칙을 포함할 수 있고, 새로운 믿음 상태를 이끌 수 있도록 추론 엔진을 사용하여 추론할 순방향 추론(forward chaining)을 할 수 있다. 지식(knowledge)보다 신념(Beliefs)이라는 용어를 사용하는 것은 에이전트가 믿는 것은 반드시 사실 일 필요는 없으며, 시간이 지나면 믿고 있는 신념이 변할 수 있기 때문이다.

* Desires : 욕망은 에이전트가 동기적으로 달성하고 싶은 상태, 에이전트가 달성하거나 달성하려는 목표 또는 상황을 나타낸다. 
> ex) 파티에 가거나 부자가 되어라.

* Goals : 목적은 에이전트가 적극적으로 달성하고자 하는 욕망이다. 목표라는 용어를 사용하게 되면 제한이 추가 된다.

> ex) 파티에 가고 집에 머문다. 라는 동시 목표를 가져서는 안된다.

* Intention : 의도는 에이전트가 욕망을 달성하기 위해 선택한 선택한 것(의도, 계획)을 나타낸다.

* Plans : 계획은 에이전트가 하나 이상의 의도를 달성하기 위해 수행 할 수 있는 일련의 동작이다. 계획에는 다른 계획이 포함 될 수 있다.

* Events : 이벤트는 Beliefs를 업데이트하거나 계획을 바꾸거나 목표를 수정 할 수 있따. 이벤트는 외부에서 생성되어 센서 또는 통합 시스템에 의해 수신 될 수 있따. 또한 분리된 업데이트 또는 활동 계획을 트리거 하기 위해 내부적으로 이벤트가 수행 될 수 있다.

### BDI Interpreter

```
Initialize-state
while(true){
   options = option_generator(event_queue)
   selected-options = deliberate(options)
   update-intentions(selected-options)
   execute()
   get-new-external_events()
   drop-unsuccessful-attitudes()
   drop-impossible-attitudes()
}
```

### Limitations and criticisms

BDI 소프트웨어 모델은 단일 에이전트에 대한 추론 아키텍쳐이다. BDI 모델에 대한 제약 사항은 다음과 같다.

* Learning(학습) : BDI 에이전트는 아키텍처 내에서 과거의 행동으로부터 배우고 새로운 상황에 적응 할 수 있는 특정 매커니즘이 존재 하지 않는다.
* Three attitudes : 고전적인 의사 결정 이론가들과 계획 연구자들은 (Belief, Desire, Intention)을 모두 가지 필요가 있는지에 대한 의문과 distributed AI 연구자들은 (Belief, Desire, Intention)이 충분한지에 대해 의문을 제기한다.
* Logics : BDI는 공리화와 효율적으로 계산할 수 없으므로 BDI의 기초가 된다고 주장하는 multi-modal logics(다중 모달 로직)과는 관계가 없다.
* Multiple agents : BDI 모델은 다른 에이전트와의 상호 작용 및 멀티 에이전트 시스템에 통합하기 위한 메커니즘을 명시적으로 설명하지 않는다.

