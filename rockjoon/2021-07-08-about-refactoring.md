# 리팩토링의 경험

## 시작하며
개발자로서 레거시 리팩토링은 자주 겪게 되는 과제이지만, 꼭 유쾌하지만은 않다.  
특히 코드가 *dirty*한 경우에는 더욱 그렇다.

현재 회사에서 리팩토링을 진행 중인데, 복잡하고 이해하기 힘든 코드라서 쉽지 않은 프로젝트가 되고 있다.  
그래도 프로젝트를 진행하면서 개인적으로 느낀점과 들었던 생각들을 공유해보려 한다.

## 👉시작은 디버깅 모드부터
리팩토링을 한다는 것은 기본적으로 해당 도메인에 익숙한 경우가 많다.  
때문에 코드 레벨에서 바로 시작할 수 있다.

리팩토링을 한다면 코드 분석부터 시작할텐데, 나는 이때 `디버깅 모드`를 먼저 구동한다.  
간단한 코드의 경우에는 디버깅 모드가 필요 없지만, 간단한 코드란 존재하지 않는다.

레거시 코드에는 내가 모르는 함수, 변수, 객체들이 쏟아져 나오는데,  
**이들이 어떻게 변화하고 상호작용하는지 하나 하나 직접 확인** 할 수 있어서 
디버깅 모드로 분석하는 것을 선호하는 편이다.

보통 나같은 경우는 디버깅을 한 두번 돌려서 해당 코드를 완전히 이해하지 못하는 경우가 많다.  
그럴 때는 브레이크 포인트를 촘촘하게 걸어서 몇번이고 돌려 본다.

## 🔗스텝 바이 스텝
새롭게 시작하는 프로젝트라면 태초마을부터 만들어 가면 되지만, 리팩토링의 경우에는 기존 코드의 방대함에 압도될 수 있다.  
인간의 버퍼는 한계가 있어서 기능의 디테일한 부분들을 동시에 전부 신경쓸 수 없다.

이럴 때 `TDD`가 효과적이라고 생각한다. 하지만 개인적으로 테스트를 먼저 작성하는 TDD 사이클에는 익숙하지 않다.  
중요한 건 **동작하는 작은 단위를 완성 시키는 것**(그리고 테스트)이라고 생각한다.
작은 기능을 하나 하나 완성시키면 부담도 줄어들고 작업에도 가속도가 붙는다.

## 👽이러시는 이유가 있을거 아니에요...

레거시 코드를 보다 보면 존재의 이유를 알기 힘든 코드들을 가끔 만난다.  
이번에 프로젝트를 할 때, 어떠한 동작 전후로 똑같은 코드가 반복되는 경우가 있었다.  
코드에 문제가 있다고 생각하여 그 부분을 빼버렸는데, 그것이 앞뒤로 반복되는 게 아주 중요한 핵심 포인트였다.  
이유없이 존재하는 코드는 거의 없다. 그 코드를 짠 사람도 이를 원치 않았을 것이다. 항상 다시 체크해 보자.

## 🐷욕심이 과하면
리팩토링을 너무 거창하게 하려 하면 오히려 역효과가 날 수 있다.

*어떻게 하면 더 확장성 있고 더 변화에 유연하고 더 성능이 빠르고 그러면서 동시에 더 클린한 코드를 만들 수 있을까...*

라는 것에 매몰되면 코드를 한 줄도 작성하기 힘들다.  
그래서 나는 리팩토링의 목적에 맞게(ex 프레임워크 변경, 코드 리뉴얼, 기능 변경 ...) 개발하는 것이 일순위라고 생각한다.

## 🧐코드를 이해하는 능력

이해하기 힘든 코드들을 볼 때면 항상 *"나는 남들이 읽기 쉬운 코드를 짜자"* 라는 생각이 들었다.  
그런데 이번에는 나아가서, **코드를 잘 이해하는 능력**도 중요하다는 생각이 들었다.  

그 이유는 우리가 개발을 하면서 `항상 좋은 코드만 만나지는 않는다.` 결국 이를 해석하고 개선하는 것이 `나의 몫`이기 때문이다.  
또한 코드를 이해하는 것은 주관적이다. 내가 잘 짯다고 생각하는 코드도 누군가에게는 어려움이 될 수도 있다.

## 마치며
리팩토링은 고독한 싸움이다. 기존 코드가 엉망이었더라도 어쨋든 돌아가기 때문에 잘해도 본전이고 못하면 욕먹기 쉽다.  
하지만 나름의 성취감도 있다고 생각한다. 마치 어지러진 집안 곳곳을 청소하는것 같은 기분이다.  
무엇보다 해당 시스템의 리팩토링이 끝나면 어차피 유지 보수하는 사람이 나이기 때문에  
결국 나를 위한 작업이라 생각하고 싶다.