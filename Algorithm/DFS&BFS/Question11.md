# 단지 번호 붙이기 #

## 1. 문제
- <그림 1>과 같이 정사각형 모양의 지도가 있다.
- 1은 집이 있는 곳을, 0은 집이 없는 곳을 나타낸다.
- 철수는 이 지도를 가지고 연결된 집들의 모임인 단지를 정의하고, 단지에 번호를 붙이려 한다.
- 여기서 연결되었다는 것은 어떤 집이 좌우, 혹은 아래위로 다른 집이 있는 경우를 말한다.
- 대각선상에 집이 있는 경우는 연결된 것이 아니다.
- <그림 2>는 <그림 1>을 단지별로 번호를 붙인 것이다.
- 지도를 입력하여 단지수를 출력하고, 각 단지에 속하는 집의 수를 오름차순으로 정렬하여 출력하는 프로그램을 작성하시오.

![단지](https://user-images.githubusercontent.com/35207245/71095718-6b0b6d00-21f0-11ea-9f52-95e7888e671e.png)

## 2. 입력

- 첫 번째 줄에는 지도의 크기 N(정사각형이므로 가로와 세로의 크기는 같으며 5≤N≤25)이 입력되고, 그 다음 N줄에는 각각 N개의 자료(0혹은 1)가 입력된다.

## 3. 출력
- 첫 번째 줄에는 총 단지수를 출력하시오.
- 그리고 각 단지내 집의 수를 오름차순으로 정렬하여 한 줄에 하나씩 출력하시오.

## 4. 예제 입력
```
7
0110100
0110101
1110101
0000111
0100000
0111110
0111000
```

## 5. 예제 출력
```
3
7
8
9
```

## 6. 코드

```c++
#include <stdio.h>
#include <algorithm>
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

const int MAX = 60;
bool visited[MAX][MAX];
int arr[MAX][MAX];
int dx[4] = {-1, 1, 0, 0};
int dy[4] = {0, 0, -1, 1};
vector<int> visitedArr;
queue<int> QueueX;
queue<int> QueueY;
int n, cnt = 0;

void BFS() {
  for(int i = 0; i < n; i++) {
    for(int j = 0; j < n; j++) {
      int current = arr[i][j];     

      if(current == 1 && !visited[i][j]) {
        QueueX.push(i);
        QueueY.push(j);
        visited[i][j] = true;
        
        while(!QueueX.empty()) {
          cnt++;
          
          int currentX = QueueX.front();
          int currentY = QueueY.front();
          QueueX.pop();
          QueueY.pop();
          
        for(int i=0; i<4; i++) {
          int nx, ny;
          nx = currentX + dx[i];
          ny = currentY + dy[i];
          
          if(nx < n && nx > -1 && ny < n && ny > -1) {
            if(arr[nx][ny] == 1 && !visited[nx][ny]) {
              QueueX.push(nx);
              QueueY.push(ny);
              visited[nx][ny] = true;
            }
            }
          }
        }
      }
      if(cnt > 0) {
        visitedArr.push_back(cnt);
        cnt = 0;
      }
    }
  }
}

int main() {
  scanf("%d", &n);
  for(int i = 0; i < n; i++) {
    for(int j = 0; j < n; j++) {
      scanf("%1d", &arr[i][j]);
    }
  }

  BFS();
  sort(visitedArr.begin(), visitedArr.end());
  printf("%d\n", visitedArr.size());
  
  for(int i = 0; i < visitedArr.size(); i++) {
    printf("%d\n", visitedArr[i]);
  }

  return 0;
}
```
