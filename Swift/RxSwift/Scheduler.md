# Scheduler

### Scheduler?

Scheduler는 특정코드가 실행되는 Context를 추상화한것

Context는 로우레벨 Thread가 될 수도 있고 Dispatch Queue, Operation Queue가 될 수도 있음

추상화된 Context이기 때문에 Thread와 1대1로 매칭되지 않습니다

> Cocoa -> GCD
> 
> RxSwift -> Scheduler

### subscribeOn

* 시퀸시가 시작될때 어느 Scheduler에서 실행될지 지정(최상위부터 적용)

### observeOn

* 다음에 오는 작업들이 어느 스케줄러에서 실행될지 지정(하위부터 적용)

![image](https://user-images.githubusercontent.com/81547954/149592935-85989f53-29ae-4b41-b941-bcd9ae12313d.png) <br>
출처 : https://reactivex.io/documentation/scheduler.html

참고 : https://kyungmosung.github.io/2020/02/06/rxswift-scheduler/
