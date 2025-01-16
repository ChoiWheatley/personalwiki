---
{"dg-publish":true,"permalink":"/docs/lower bound with bisect_left (python)/","title":"lower bound with bisect_left (python)"}
---

[`bisect.bisect_left`](https://docs.python.org/3/library/bisect.html#bisect.bisect_left)

C++에 [[이분탐색을 활용한 lowerbound 구현법 {Algo}\|lower_bound]]가 있다면 파이썬에는 `bisect.bisect_left`가 있다. 그럼 `upper_bound`는? `bisect.bisect_right` 바보야 😲

이분탐색은 그 자체로 너무 많은 곳에 활용이 되고 있어서 실전 위주로 정리를 해보겠다. 흠흠

아래는 [[docs/LIS 가장 긴 증가하는 부분수열\|LIS 가장 긴 증가하는 부분수열]]를 파이썬으로 구현한 코드이다. 확실히 엄청나게 간결하다.


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/docs/20230518-estsoft-python-tree-lis-selection-sort-insertion-sort-merge-sort-quick-sort/#4ygbua" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



[[docs/LIS 가장 긴 증가하는 부분수열\|LIS 가장 긴 증가하는 부분수열]]  
<https://choiwheatley.notion.site/LIS-d61b26f5619a4ea1b0412155535ec812> 에 정리해두긴 했으나 수정할 사안이 존재하여 다시 불러왔다.  


</div></div>


아래는 삽입정렬을 `bisect_left`를 활용하여 푼 코드이다. 부분정렬리스트인데, 이분탐색을 안할 이유가 없잖아?


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/docs/20230518-estsoft-python-tree-lis-selection-sort-insertion-sort-merge-sort-quick-sort/#fyzoll" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



```python
from bisect import bisect_left


def insertion_sort(data):
    """insertion sort with binary search => O(N LOG(N))"""

    result = []

    for e in data:
        idx = bisect_left(result, e)
        if idx == len(result):
            result.append(e)
        else:
            result.insert(idx, e)

    return result


ls = [199, 22, 33, 12, 32, 64, 72, 222, 233]
assert sorted(ls) == insertion_sort(ls)
```

</div></div>

