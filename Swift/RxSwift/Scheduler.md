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

## 내장 스케줄러(Builtin schedulers)

### CurrentThreadScheduler (Serial scheduler)

* 현재 스레드에 있는 작업의 단위들을 스케쥴해줍니다 
* `CurrentThreadScheduler`는 요소를 생성하는 연산자의 기본 스케줄러입니다
* 만약 `CurrentThreadScheduler.instance.schedule(state) { }가` 어떤 스레드에서 처음으로 호출 된 경우, <br> 예약 된 작업이 즉시 실행되고 재귀 적으로 예약 된 모든 작업이 잉시적으로 대기하는 숨겨진 큐가 생성됩니다
* 만약 콜 스택의 몇몇 부모 프레임이 이미 `CurrentThreadScheduler.instance.schedule(state)  { }`를 <br> 실행중이라면, 예약 된 작업은 현재 실행중인 작업과 이전에 대기열에 추가 된 모든 작업이 왼료되어 대기열에 추가되고 실행됩니다

<hr>

### MainScheduler (Serial scheduler)

* `MainThread`에서 실행되어야 하는 추상적인 작업에서 사용합니다 `schedule`메서드가 메인 스레드에서 호출된 경우에, 스케줄링 없이 작업을 실행합니다
* 이 스케줄러는 보통 UI 작업에서 쓰입니다

### SerialDispatchQueueScheduler (Serial scheduler)

* 특정 `dispatch_queue_t`에서 실행되어야 하는 추상적인 작업에서 사용합니다. 컨커런트 디스패치 큐에 전달된 경우에도 시리얼 디스패치 큐로 변환됩니다
* 시리얼 스케줄러는 `observeOn`를 위한 특정 최적화를 가능하게 해줍니다
* 메인 스케줄러는 `SerialDispatchQueueScheduler`의 인스턴스입니다

### ConcurrentDispatchQueueScheduler (Concurrent scheduler)

* 특정 `dispatch_queue_t`에서 실행되어야 하는 추상적인 작업에서 사용합니다. 시리얼 디스패치 큐에도 보낼 수 있으며 아무런 문제가 발생하지 않습니다
* 이 스케줄러는 백그라운드에서 작업이 실행되어야 할 때 적합합니다

### OperationQueueScheduler (Concurrent scheduler)

* 특정 `NSOperationQueue`에서 실행되어야 하는 추상적인 작업에서 사용합니다
* 이 스케줄러는 백그라운드에서 수행해야하는 큰 작업이 있고 `maxConcurrentOperationCount`를 이용해서 컨커런트 처리 과정을 미세 조정하려는 경우에 적합합니다
* 이 스케줄러는 백그라운드에서 수행해야하는 더 큰 작업 청크가 있고 `maxConcurrentOperationCount`를 사용하여 동시 처리를 미세 조정하려는 경우에 적합합니다


참고 : https://kyungmosung.github.io/2020/02/06/rxswift-scheduler/
