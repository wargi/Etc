# 가로 세로 채우기

## 1. 문제

```
1. 아래의 2차원 배열(4x4)를 빈 배열을 하드코딩 해주세요.
0 0 0 0
0 0 0 0
0 0 0 0
0 0 0 0

2. 만약 G 2를 입력 받으면, 아래와 같이 채워줍니다.
0 0 0 0
0 0 0 0
1 1 1 1
0 0 0 0

3. 만약 S 0를 입력 받으면, 아래와 같이 채워줍니다.
1 0 0 0
1 0 0 0
1 1 1 1
1 0 0 0

4. 만약 S 3를 입력 받으면, 아래와 같이 채워줍니다.
1 0 0 1
1 0 0 1
1 1 1 1
1 0 0 1

5. 채운 배열을 출력해주세요.
```

## 2. 입력
- 채울 내용을 세 줄 입력 받습니다.

## 3. 출력

- 위의 문제 설명처럼 배열을 채우고 출력해주세요.


## 4. 예제 입력
```
G 0
S 1
G 2
```

## 5. 예제 출력
```
1 1 1 1
0 1 0 0
1 1 1 1
0 1 0 0
```

## 6. 예제 입력

```
S 3
G 0
S 1
```

## 7. 예제 출력

```
1 1 1 1
0 1 0 1
0 1 0 1
0 1 0 1
```

## 8. 코드

```c++
#include <iostream>
using namespace std;
int map[4][4] = { 0 };

void drawG(int n) {
    for (int i = 0; i < 4; i++) map[n][i] = 1;
}

void drawS(int n) {
    for (int i = 0; i < 4; i++) map[i][n] = 1;
}

int main()
{
    for (int i = 0; i < 3; i++) {
        char ch;
        int n;

        cin >> ch >> n;

        if (ch == 'G') drawG(n);
        else drawS(n);
    }

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << map[i][j] << " ";
        }
        cout << "\n";
    }
}
```