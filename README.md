# [쥬피터 노트북 해설](problem_solving.ipynb)

# 문제 1

이 문제를 해결하기 위해서는 배열에서 가장 작은 수를 찾아 제거하고, 그 결과를 반환하는 과정을 구현해야 합니다. 만약 배열의 길이가 1인 경우에는 바로 `[-1]`을 반환하면 됩니다. 배열에서 가장 작은 수를 찾는 것은 Python의 `min()` 함수를 사용하여 쉽게 구현할 수 있습니다.

아래는 파이썬으로 작성한 해결 코드입니다:

```python
def solution(arr):
    # 배열의 길이가 1인 경우 [-1]을 리턴
    if len(arr) == 1:
        return [-1]
    
    # 배열에서 가장 작은 값 찾기
    min_value = min(arr)
    
    # 가장 작은 값을 제거한 배열 리턴
    arr.remove(min_value)
    
    return arr
```

### 설명:
1. **배열의 길이가 1인 경우**: 배열이 한 개의 요소만 가지면, 그 요소를 제거하면 배열이 비게 되므로 `[-1]`을 반환합니다.
2. **가장 작은 값을 찾기**: `min(arr)` 함수를 사용해 배열에서 가장 작은 값을 찾습니다.
3. **가장 작은 값 제거**: `remove()` 함수를 사용해 배열에서 가장 작은 값을 제거합니다.
4. **결과 반환**: 제거된 배열을 반환합니다.

### 예시 실행:

```python
print(solution([4, 3, 2, 1]))  # 출력: [4, 3, 2]
print(solution([10]))          # 출력: [-1]
```

이 방식으로 문제를 해결할 수 있습니다!



---
---

# 문제 2

### 풀이 1

이 문제는 문자열을 내림차순으로 정렬하는 문제입니다. 중요한 점은 영문 대소문자가 섞여 있을 때, **대문자는 소문자보다 작은 것으로 간주**된다는 조건입니다. 즉, 내림차순으로 정렬할 때, 소문자가 먼저 오고 그다음 대문자가 와야 합니다.

Python에서는 `sorted()` 함수와 `join()`을 사용하여 문자열을 쉽게 정렬하고 새로운 문자열로 만들 수 있습니다. 정렬 시, 소문자가 대문자보다 큰 것으로 간주된다는 점을 활용하면 문제를 해결할 수 있습니다.

### 해결 코드:

```python
def solution(s):
    # sorted 함수로 문자열을 내림차순으로 정렬하고, join으로 다시 문자열로 변환
    return ''.join(sorted(s, reverse=True))
```

### 설명:
1. **`sorted()` 함수**: 문자열 `s`를 정렬하는데, `reverse=True` 옵션을 사용하면 내림차순으로 정렬됩니다.
   - 기본적으로 소문자가 대문자보다 크다고 간주되기 때문에 정렬하면 소문자가 먼저 오고, 대문자가 그다음에 옵니다.
2. **`join()` 함수**: 정렬된 리스트를 다시 하나의 문자열로 합칩니다.

### 예시 실행:

```python
print(solution("Zbcdefg"))  # 출력: "gfedcbZ"
```

이 방식으로 문자열을 내림차순으로 정렬할 수 있습니다!


### 풀이 2

 Python의 `ord()` 함수로 문자를 해당 ASCII 값(숫자)으로 변환한 뒤, 이를 정렬한 다음 `chr()` 함수를 이용해 다시 문자를 얻는 방식으로 구현할 수 있습니다.

아래는 해당 방법을 이용한 코드입니다:

### 해결 코드:

```python
def solution(s):
    # 각 문자를 ASCII 값으로 변환하여 리스트로 저장
    ascii_values = [ord(char) for char in s]
    
    # ASCII 값들을 내림차순으로 정렬
    ascii_values.sort(reverse=True)
    
    # 정렬된 ASCII 값을 다시 문자로 변환하여 문자열로 합치기
    return ''.join(chr(value) for value in ascii_values)
```

### 설명:
1. **`ord()` 함수**: 문자열 `s`의 각 문자를 해당 ASCII 값으로 변환합니다. 예를 들어, `ord('a')`는 97이고, `ord('A')`는 65입니다.
2. **정렬**: 변환된 ASCII 값들을 `sort(reverse=True)`로 내림차순으로 정렬합니다.
3. **`chr()` 함수**: 정렬된 숫자 값을 다시 문자로 변환하여 원래의 문자열로 만듭니다.
4. **`join()` 함수**: 다시 문자를 결합하여 하나의 문자열로 만듭니다.

### 예시 실행:

```python
print(solution("Zbcdefg"))  # 출력: "gfedcbZ"
```

### 작동 원리:
1. `"Zbcdefg"`의 각 문자를 `ord()`를 통해 ASCII 값으로 변환하면 `[90, 98, 99, 100, 101, 102, 103]`이 됩니다.
2. 이 값을 내림차순으로 정렬하면 `[103, 102, 101, 100, 99, 98, 90]`이 됩니다.
3. 다시 `chr()`로 변환하면 `"gfedcbZ"`라는 문자열이 만들어집니다.

이 방법을 통해 문자들을 숫자로 변환한 후, 내림차순으로 정렬하는 과정을 거쳐 문자열을 처리할 수 있습니다!