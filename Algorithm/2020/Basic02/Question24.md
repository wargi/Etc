# 배열 탐색하기

## 1. 문제

```
1. 2차원 배열(3x4)을 하드코딩 해주세요.
A B G K
T T A B
A C C D
```

- 2차원 배열(2x2)을 입력 받고, 해당 배열이 위의 하드 코딩 배열에 존재하는지 출력해주세요.
- 존재한다면, 몇개가 있는지 확인하고 "발견(1개)" 이런식으로 출력해주시고, 없다면 "미발견"이라고 출력해주세요.

## 2. 입력

- 2차원 배열(2x2)을 입력 받습니다.

## 3. 출력

- 입력 받은 배열이 존재한다면, 몇개가 있는지 확인하고 "발견(1개)" 이런식으로 출력해주시고, 없다면 "미발견"이라고 출력해주세요.


## 4. 예제 입력
```
AB
CD
```

## 5. 예제 출력
```
발견(1개)
```

## 6. 예제 입력

```
AS
DF
```

## 7. 예제 출력

```
미발견
```

## 8. 코드

```c++
#include <iostream>
using namespace std;

struct Sketchbook {
    char image[3][4];
};

int main()
{
    int dat[100] = { 0 };
    Sketchbook s1;

    for (int i = 0; i < 3; i++) {
        cin >> s1.image[i];
    }

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            dat[s1.image[i][j]]++;
        }
    }

    for (int i = 0; i < 100; i++) {
        if (dat[i] > 0) cout << char(i);
    }
}

```
