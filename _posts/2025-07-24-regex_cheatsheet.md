---
title: "파이썬 정규표현식 완전 정리"
date: 2025-07-25
categories: [Python]
tags: [Regex, re, 정규표현식, Python, 문자열 처리]
---

# 🧩 파이썬 정규표현식 완전 정리

정규표현식(Regular Expression)은 문자열에서 특정 패턴을 찾거나 치환할 때 사용하는 **패턴 언어**입니다.  
파이썬에서는 `re` 모듈을 사용합니다.

---

## 🔧 기본 사용법

```python
import re

# 패턴 검색
re.search(pattern, string)

# 패턴 전체 일치 여부
re.fullmatch(pattern, string)

# 패턴 찾기 (첫 번째만)
re.match(pattern, string)

# 패턴 모두 찾기
re.findall(pattern, string)

# 패턴으로 문자열 나누기
re.split(pattern, string)

# 패턴으로 치환하기
re.sub(pattern, repl, string)
```

---

## 📘 자주 쓰는 메타 문자

| 메타 문자 | 의미                         | 예시              |
|-----------|------------------------------|-------------------|
| `.`       | 임의의 한 문자               | `a.b` → aab, acb  |
| `^`       | 문자열 시작                  | `^a` → abc 가능   |
| `$`       | 문자열 끝                    | `z$` → buzz 가능  |
| `*`       | 0개 이상의 반복              | `ab*` → a, ab, abb|
| `+`       | 1개 이상의 반복              | `ab+` → ab, abb   |
| `?`       | 0개 또는 1개                 | `ab?` → a, ab     |
| `{m}`     | 정확히 m번 반복              | `a{2}` → aa       |
| `{m,n}`   | m~n회 반복                   | `a{1,3}` → a, aa, aaa |
| `[]`      | 문자 집합                    | `[a-z]`, `[0-9]`  |
| `|`       | OR 조건                      | `cat|dog`         |
| `()`      | 그룹핑                       | `(ab)+` → ab, abab|

---

## 🔤 문자 클래스

| 표현 | 의미                      |
|------|---------------------------|
| `\d` | 숫자 (`[0-9]`)            |
| `\D` | 숫자가 아닌 문자         |
| `\w` | 문자 + 숫자 (`[a-zA-Z0-9_]`) |
| `\W` | 문자 + 숫자가 아닌 문자  |
| `\s` | 공백 문자 (`	`, `
` 등)|
| `\S` | 공백이 아닌 문자         |

---

## 🎯 예시 모음

### 이메일 형식 체크

```python
import re

pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
email = "test@example.com"
print(bool(re.match(pattern, email)))  # True
```

### 전화번호 찾기

```python
text = "내 번호는 010-1234-5678입니다."
pattern = r'\d{3}-\d{4}-\d{4}'
print(re.findall(pattern, text))  # ['010-1234-5678']
```

---

## 📌 그룹과 메서드

```python
m = re.search(r"(\d+)-(\d+)", "123-456")
print(m.group())     # 전체 일치: '123-456'
print(m.group(1))    # 첫 번째 그룹: '123'
print(m.group(2))    # 두 번째 그룹: '456'
print(m.start(), m.end())  # 일치하는 구간 인덱스
```

---

## 🧪 정규표현식 옵션

| 옵션     | 의미                            |
|----------|---------------------------------|
| `re.IGNORECASE` (`re.I`) | 대소문자 무시       |
| `re.MULTILINE` (`re.M`)  | 여러 줄에서 `^`, `$` 작동 |
| `re.DOTALL` (`re.S`)     | `.`이 줄바꿈 포함     |

```python
re.search(r"hello", "HELLO", re.I)
```

---

## ✅ 마무리

정규표현식은 복잡해보이지만, 자주 쓰는 패턴만 익혀도 충분히 실무에 활용 가능합니다.  
**많이 써보면서 익히는 게 가장 좋은 학습 방법입니다!**

---

✍️ 작성자: 지돌멩이  
📎 GitHub: [@yourgithub](https://github.com/yourgithub)
