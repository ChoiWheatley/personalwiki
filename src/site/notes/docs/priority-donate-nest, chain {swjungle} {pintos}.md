---
{"dg-publish":true,"permalink":"/docs/priority-donate-nest, chain {swjungle} {pintos}/","title":"priority-donate-nest, chain {swjungle} {pintos}"}
---

- <https://github.com/ChoiWheatley/swjungle-week07-09/pull/23>
- [[docs/week07-10 {swjungle} {pintos}\|week07-10 {swjungle} {pintos}]]
___

## donate-nest / donate-chain

priority-donate-chain 예제를 기준으로 설명합니다. 지면이 부족하므로 `NESTING_DEPTH == 3`으로 놓고 진행합니다.

[[docs/assets/priority-donate-chain.excalidraw\|priority-donate-chain.excalidraw]]  
![Pasted image 20230929220928.png](/img/user/docs/assets/Pasted%20image%2020230929220928.png)

`main` 스레드는 0번 lock을 소유합니다. 이를 'h' 달린 화살표료 표기합니다. T1 스레드는 1번 lock을 소유하고 0번 lock을 기다립니다. 이를 w 달린 화살표로 표기합니다. 다시 main에 의해 T2가 실행됩니다. T2 스레드는 2번 lock을 소유하고 1번 lock을 기다립니다. T3 스레드는 3번 lock을 소유하고 2번 lock을 기다립니다. 

`lock_acquire`에서 lock 획득에 실패할 경우, lock holder에게 자신의 priority를 기부할지 안할지를 결정합니다. lock 하나 당 하나의 waiter만이 lock holder에게 우선순위를 기부할 수 있습니다. 따라서 이미 같은 lock에 대하여 기부자가 있는 경우 이를 대체할 지 여부도 결정하여야 합니다.

예제에서 모든 자식 스레드를 만든 경우, 위의 도식과 같은 모양이 됩니다. 청록색 곡선은 스레드에 걸려있는 donation list의 원소를 나타냅니다. 예를 들어 T2 스레드의 donation list는 T3입니다. 따라서 `get_priority(T2)`의 결과는 `max(T2.donation_list) = T2.original_priority = 9`가 됩니다.

`get_priority` 함수는 재귀적으로 작동해야 합니다. 연쇄적으로 서로의 lock을 물고 있는 경우가 대표적입니다. 가장 높은 우선순위를 가진 T3가 빠르게 실행되기 위해선 2번 lock을 해제해야 하고, 그러기 위해선 T2가 빠르게 실행되어야 하고, 그러기 위해선 1번 lock을 해제해야 합니다. 그러기 위해선 T1이 빠르게 실행되어야 하고, 그러기 위해선 0번 lock을 해제해야 합니다. 결국 main이 T1, T2, T3 모두의 donation list 중 최고 priority로 힘입어 동작하게 되며, 결과적으로 main 스레드는 마치 T3의 우선순위를 기부받은 것처럼 동작하게 될 것입니다.

하지만 명시적으로 main 스레드가 받은 donation은 T1으로부터 받은것에 불과하므로 `get_priority`를 재귀적으로 호출하여 donate list가 없는 스레드가 나올 때까지, 즉 기부받은 스레드가 없을 때까지 반복적으로 `get_priority`를 호출하게 됩니다.

```python
def get_priority(thread):
	if list_empty(thread.donation_list):
		return target.priority
	# not empty list
	max_donor = max(thread.donation_list, key=priority)
	return get_priority(max_donor)
```
