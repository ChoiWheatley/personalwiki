---
{"dg-publish":true,"permalink":"/docs/TSP - 외판원 순회/","title":"TSP - 외판원 순회"}
---


# TSP - 외판원 순회

상태: 정리완료  
태그: dp, graph

모든 도시를 한번씩만 들르고 $v_1$으로 돌아오는 가장 저렴한 비용을 계산하라.

# 브루트포스

$O(N!)$의 시간복잡도를 가진다. 

# DP

결론: $O(N!)$를 $O(N2^N)$의 시간 복잡도를 가지며, 다항시간안에 문제를 풀이하는 알고리즘은 아직까지 밝혀지지 않았다. (NP-hard)

`D[vi][A]` = 집합 A에 속한 정점을 정확히 한 번만 거쳐 vi 에서 v1로 가는 최단경로의 길이

가장 큰 문제 : `D[v1][V-{v1}]` V = 전체 정점들의 집합. 

가장 작은 문제 : `D[vi][{}] = W[i][1]` vi에서 v1로 직빵으로 가는 경로의 길이

$$
\begin{alignat*}{}
&D[v_1][ø]=W[1][1]&& =0\\
&D[v_1][\{v_2\}]&& =\min(W[1][2]+D[v_2][ø])\\
&D[v_1][\{v_2,v_3\}]&& =\min_{v_j \in \{v_2, v_3\}}(W[1][j]+D[v_j][\{v2,v_3\}-\{v_j\}])\\
&\dots\\
&D[v_1][S] && =\min_{v_j\in S}(W[1][j]+D[v_j][S-\{v_j\}])
\end{alignat*}
$$

```python
for k in 1..<n :
	for all A subset of V - {v1} containing k vertices :
		for i such that i != 1 and vi is not in A :
			for j in A :
				vj = V[j]
				D[i][A] <- min( W[i][j] + D[vj][A - {vj}] )
```

## 시간복잡도

1. 첫번째 for문에서 n-1
2. 두번째 for문에서 C(n-1, k)
3. 세번째 for문에서 n - k - 1 : 아직 방문하지 않은 도시의 개수
4. 네번째 for문에서 k

$$
\sum_{k=1}^{n-1}{{n-1}\choose{k}}(n-k-1)k \in \Theta(n^22^n)
$$
