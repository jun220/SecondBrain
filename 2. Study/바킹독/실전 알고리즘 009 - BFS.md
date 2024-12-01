```vid
https://youtu.be/ftOmGdm95XI?si=9k5VsTIvox5ybxIw
```

학습일 : 2024-11-02 14:24 

---
### 학습내용
### BFS (Breadth First Serach)
다차원 배열에서 각 칸을 방문할 때 너비를 우선으로 방문하는 알고리즘

#### BFS 예시
![[Pasted image 20241103234803.png]]
(0,0)부터 시작하여 인접한 파란색 칸을 모두 찾아 칠하는 과정을 생각.

1. (0,0)을 큐에 추가
2. 큐에서 pop한 (0,0)의 상하좌우 칸인 (0,1)과 (1,0)을 방문처리하고 큐에 추가
3. pop->(0,1). 상하좌우 칸 중 파란색이고 방문하지 않은 것을 찾음. (0,2)를 방문처리하고 큐에 추가
4. pop->(1,0). (2,0)을 방문처리하고 큐에 추가.

이후에도 pop과 주변 탐색, 맞는 칸을 방문 처리하고 큐에 추가하는 과정을 반복. 큐가 완전히 빈 순간 종료

visited 처리로 모든 칸이 큐에 1번씩만 들어가므로, 시간 복잡도는 칸이 N개일 때 O(N).

```cpp title="BFS 예시 코드" fold
#include <iostream>
#include <queue>
using namespace std;


#define X first
#define Y second // pair에서 first, second를 줄여서 쓰기 위해서 사용

int board[502][502] =
{ {1,1,1,0,1,0,0,0,0,0},
 {1,0,0,0,1,0,0,0,0,0},
 {1,1,1,0,1,0,0,0,0,0},
 {1,1,0,0,1,0,0,0,0,0},
 {0,1,0,0,0,0,0,0,0,0},
 {0,0,0,0,0,0,0,0,0,0},
 {0,0,0,0,0,0,0,0,0,0} }; // 1이 파란 칸, 0이 빨간 칸에 대응

bool visited[502][502]; // 해당 칸을 방문했는지 여부를 저장
int n = 7, m = 10; // n = 행의 수, m = 열의 수

int dx[4] = { 1,0,-1,0 };
int dy[4] = { 0,1,0,-1 }; // 상하좌우 네 방향을 의미

int main(void) {
    ios::sync_with_stdio(0);
    cin.tie(0);

    queue<pair<int, int> > Q;
    visited[0][0] = 1; // (0, 0)을 방문했다고 명시

    Q.push({ 0,0 }); // 큐에 시작점인 (0, 0)을 삽입.

    while (!Q.empty()) {
        // Q가 비어있는지 확인했으므로, 첫번째 원소를 가져옴
        pair<int, int> cur = Q.front(); 
        Q.pop();

        cout << '(' << cur.X << ", " << cur.Y << ") -> ";

        for (int dir = 0; dir < 4; dir++) { // 상하좌우 칸을 살펴볼 것
            int nx = cur.X + dx[dir];
            int ny = cur.Y + dy[dir]; // nx, ny에 dir에서 정한 방향의 인접한 칸의 좌표가 들어감
            if (nx < 0 || nx >= n || ny < 0 || ny >= m) continue; // 범위 밖일 경우 넘어감
            if (visited[nx][ny] || board[nx][ny] != 1) continue; // 이미 방문한 칸이거나 파란 칸이 아닐 경우
            visited[nx][ny] = 1; // (nx, ny)를 방문했다고 명시
            Q.push({ nx,ny }); // 큐에 푸시
        }
    }
}

```

### 태그
#코딩테스트 #cpp #자료구조



