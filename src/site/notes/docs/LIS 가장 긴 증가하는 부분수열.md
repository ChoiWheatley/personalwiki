---
{"dg-publish":true,"permalink":"/docs/LIS 가장 긴 증가하는 부분수열/","title":"LIS 가장 긴 증가하는 부분수열","tags":["algo/dp"]}
---


# LIS 가장 긴 증가하는 부분수열

상태: 정리완료  
태그: dp

LIS(Longest Increasing Subsequence)의 길이를 구하는 문제. 길이만 구하는 데에는 완전탐색에 dp를 사용하면 시간복잡도 O(N^2)에 풀 수 있고, 탐색을 영리하게 수행하여 O(N lgN) 시간에 문제를 푸는 방식이 있다. 더 나아가 LIS 수열 자체를 찾는 알고리즘도 구하고 싶었다.

# 브루트포스

처음에는 테스트 케이스를 따지지 않고 모든 경우의 수를 찾아보자는 마인드로 시작. 수열을 읽어가며 우리는 두가지 옵션이 있다. i번째 원소를 부분수열에 **포함한다, 포함하지 않는다.** 다음 코드는 위의 아이디어를 구현한다.

```cpp
int bruteforce
(const vector<int>& sequence, vector<int>::iterator it, int max_val=-1)
{
    if (it == sequence.end())
        return 0;

    int ret = 0;

    // 부분수열에 넣는다.
    if (max_val < *it)
        ret = max( ret, 1 + bruteforce(sequence, it+1, *it) );

    // 지나친다.
    ret = max( ret, bruteforce(sequence, it+1, max_val) );

    return ret;
}
```

증가하는 부분수열을 만들어야 하기 때문에 부분수열을 넣기 전, 지금까지 넣은 수열의 max_val보다 큰지 비교하는 점을 유의하자. 

시간복잡도는 매 인덱스마다 두번의 재귀호출이 일어나므로 O(2^N)이다. N≤500 이므로 대략 346자리의 어마어마하게 큰 수가 나오게 된다. 이래서야 시간 내에 문제를 제대로 풀 수 없을 것이다. 

# 메모이제이션

부분문제를 여러번 평가하는 브루트포스의 문제를 해결하기 위해 단순히 인덱스 j로 끝나는 부분 수열들 중 가장 큰 길이를 저장해두는 방법을 고안할 수 있다.  코드는 교재를 참고했다.

```cpp
int using_dp_iter
(const vector<int>& sequence, vector<int>::iterator it, int max_val)
{
    if (it == sequence.end())
        return 0;
    if (max_val == UNDEFINED)
        max_val = *it;
    size_t index = it - sequence.begin();
    int& ret = cache[index];

    if (ret != UNDEFINED) // 여기서 subproblems들이 걸러진다.
        return ret;
    
    // 항상 1+a개를 구하기 때문에 1부터 시작.
    ret=1;
    // max_val 보다 뒤에 있고 큰 수들 중 하나를 결정한 뒤
    // 여기서 시작하는 부분증가수열의 최대치를 구해 비교한다.
    while(++it != sequence.end())
    {
        // 부분수열에 넣는다.
        if (max_val < *it)
            ret = max( ret, 1 + using_dp_iter(sequence, it, *it) );
    }

    return ret;
}
```

```cpp
int using_dp(vector<int>& sequence)
{
    int ret = 0;
    for (vector<int>::iterator i = sequence.begin(); i != sequence.end(); i++)
    {
        memset(cache, UNDEFINED, sizeof(cache));
        ret = max( ret, using_dp_iter(sequence, i) );
    }
    return ret;
}
```

`using_dp_iter` 함수의 인자로 들어가는 반복자 `it` 을 포함하는 부분수열 중 가장 긴 증가부분수열의 길이를 ret에 저장하게 된다. 이로인해 초기 `it` 을 결정하는 코드를 N 번 수행하여야 하고 (using_dp), 하나의 이터레이션마다 최대 N번 재귀를 반복하기 때문에 이 코드의 시간복잡도는 O(N^N)가 된다. 하지만 우리에겐 중복되는 문제의 해답을 이미 가지고 있으므로 time taken per iteration = N 즉, `O(N*N)` 이 된다. 물론 N의 최대치인 500에 비교하면 해당 테스트 케이스 안에 정복이 가능하다.

> 💡 [Time Complexity is **the number of unique problems / subproblems * time taken per iteration**](https://www.freecodecamp.org/news/demystifying-dynamic-programming-24fbdb831d3a/)

시간복잡도는 고유문제의 수 ➗ 부분문제의 수 ✖️ 이터레이션을 지배하는 시간복잡도

# 최적화 방법론 (not dp)

위의 방법을 활용하면 매 이터레이션마다 접근하게 되는 부분문제의 수가 N개가 된다. 만약 이를 줄일 수 있다면? 우리는 고정된 길이 i에서의 LIS의 길이를 가지고는 있으나, 그것 말고는 저장하고 있는 정보가 없다. 따라서 조금 더 영리하게 문제를 풀기 위해선 dp의 정의였던 **부분문제의 유일성** 을 포기 하고서라도 캐시를 말 그대로 동적으로 활용해야 한다. 

[가장 긴 증가하는 부분 수열 (Longest Increasing Subsequence)](https://seungkwan.tistory.com/8)

> 💡 cache[i] = i 길이 증가수열의 마지막 원소 중 가장 작은 값을 가리키는 인덱스

```cpp
int efficient_lis(const vector<int>& seq)
{
    int L = 0, newL;
    memset(cache, 0, sizeof(cache));

    // cache[0]은 사용하지 않는다는 것을 염두하세요.
    for(size_t i = 0; i < seq.size(); i++)
    {
        // seq[i] > seq[m[j]]를 만족하는 가장 큰 j를 찾는다.
        int lo=1, hi=L;
        while (lo<=hi)
        {
            int mid = (lo+hi) / 2;
            if (seq[i] > seq[cache[mid]])
                lo = mid+1;
            else
                hi = mid-1;
        }
        newL = lo;
        cache[newL] = i;
        if (newL > L)
            L = newL;
    }

    return L;
}
```

위키피디아의 코드와 seungkwan 님의 코드를 적당히 섞어서 코드를 작성해 보았다. 위키피디아의 경우 cache 배열에 seq의 인덱스를 가리키게 만들어서 해석하기 매우 어려웠다. 하지만 lower bound를 찾는 과정이 드러나있어서 도움이 되었다. 

결국 코드의 목표는 seq[cache] 배열을 계속 정렬된 상태로 만드는 것이다. 매 i마다 seq[cache] 배열의 seq[i]에 대한 lower bound를 이진탐색으로 찾아 다음 두 가지 행동 중 하나를 수행하게 된다.

1. cache 원소와 교체한다.
2. cache 맨 뒤에 i를 추가한다.

i 순회가 완료되고나면 현재 seq 배열의 마지막 값을 가리키고 있는 L이 곧 LIS의 길이가 된다. 

아래는 임의의 seq : [2,10,6,14,1,9,15,13]에 대한 cache가 가지는 값의 변화에 대한 기록이다.

| i | seq | seq[cache[1..N]] | L |
| --- | --- | --- | --- |
| 0 | 2 | 2 | 1 |
| 1 | 10 | 2, 10 | 2 |
| 2 | 6 | 2, 6 | 2 |
| 3 | 14 | 2, 6, 14 | 3 |
| 4 | 1 | 1, 6, 14 | 0 |
| 5 | 9 | 1, 6, 9 | 3 |
| 6 | 15 | 1, 6, 9, 15 | 4 |
| 7 | 13 | 1, 6, 9, 13 | 4 |

# Pseudocode with python

C++에 `std::lower_bound`가 있다면 Python에는 [`bisect.bisect_left`](https://docs.python.org/3/library/bisect.html#bisect.bisect_left)가 있다.

자세한 알고리즘 설명은 노션에 있으니까 여기는 원래 목적 그대로 치트시트 수준으로만 작성하자.

```python
from bisect import bisect_left


def length_of_lis(nums: list):
    """lower bound를 활용한 효율적인 캐시 검색"""
    cache = []

    for num in nums:
        newL = bisect_left(cache, num)
        if len(cache) == newL:
            cache.append(num)
        else:
            cache[newL] = num

    return len(cache)


assert 5 == length_of_lis([1, 2, 3, 4, 5])
assert 1 == length_of_lis([5, 4, 3, 2, 1])
assert 4 == length_of_lis([10, 9, 2, 5, 3, 7, 101, 18])
assert 2 == length_of_lis([4, 5, 2, 3, 1, 2])
assert 4 == length_of_lis([2, 10, 6, 14, 1, 9, 15, 13])
```

# LIS의 리스트까지 구하고 싶다

```cpp
// X[i] : 입력으로 주어진 수열
// M[k] : 수열 X의 길이 k인 부분수열 중에서 마지막 인덱스의
// 값이 가장 작은 값을 저장.
// P[i] : X[i]가 바라보고 있는 M 배열의 인덱스
vector<int> efficient_list_re(const vector<int>& X)
{
    int M[MAXCACHE+1], P[MAXCACHE];
    int L = 0, newL;

    memset(M, 0, sizeof(M));
    memset(P, 0, sizeof(P));
    for (size_t i = 0; i < X.size(); ++i)
    {
        int lo = 1, hi = L, mid;
        // find lower bound using binary search
        while( lo<=hi )
        {
            mid = (lo+hi) / 2;
            if (M[mid] < X[i])
                lo = mid+1;
            else
                hi = mid-1;
        }
        // after binary search, lo gets 1 greater
        // than L

        // M replace (or append) new value X[i]
        // and P keeps tracking on M's index
        newL = lo;
        M[newL] = X[i];
        P[i] = newL;

        // when append we have to set hi value
        if (newL > L)
            L = newL;
    }

    // backtracking to get LIS
    // we only care when M gets appended!
    vector<int> ret(L);
    int r = L-1;
    for (int i = (int)X.size()-1; i >= 0; --i)
    {
        if (L == P[i])
        {
            ret[r--] = X[i];
            L--;
        }
    }

    return ret;
}
```

P 배열을 추가로 사용하여 i마다 배열 M이 가리키는 위치를 저장해 두었다. 순회가 끝난 뒤 M이 새 값을 추가할 때 1씩 커진 L의 값을 추적하여 LIS의 인덱스 리스트를 생성할 수 있다. 

| i | seq | M | L | P |
| --- | --- | --- | --- | --- |
| 0 | 2 | 2 | 1 | 1 |
| 1 | 10 | 2, 10 | 2 | 2 |
| 2 | 6 | 2, 6 | 2 | 2 |
| 3 | 14 | 2, 6, 14 | 3 | 3 |
| 4 | 1 | 1, 6, 14 | 0 | 1 |
| 5 | 9 | 1, 6, 9 | 3 | 3 |
| 6 | 15 | 1, 6, 9, 15 | 4 | 4 |
| 7 | 13 | 1, 6, 9, 13 | 4 | 4 |

이전의 예제를 들어 설명하자면, L의 값을 배열 P에 계속 보관하고 있다가 L이 가장 큰 값으로 바뀌었을 때만을 뽑아내면 리스트를 완성하게 된다.
