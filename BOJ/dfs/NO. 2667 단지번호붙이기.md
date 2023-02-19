백준 링크 : https://www.acmicpc.net/problem/2667

![image](https://user-images.githubusercontent.com/62640768/219946247-aae69fee-9f18-4ca2-95c4-af78af18b205.png)


필요 알고리즘 개념 : DFS, 연결그래프

지도의 각 칸들을 반복문으로 순회하면서
'1' 칸을 만나면, 그 칸과 인접한 칸들을 탐색하는 DFS 탐색을 시작한다.

DFS 탐색하면서 만나는 '1' 칸들의 값을 단지번호로 바꾼다. ('2', '3', '4',...)
칸들의 값을 단지번호로 바꾸는 이유는, 그 칸들이 다시 DFS 탐색 대상이 되지 않기 위함이다.

DFS 메소드는, 값을 바꾼 칸들의 수를 리턴한다.

리턴된 칸들의 수를 ArrayList에 저장하고, 정렬하여 출력한다.

```
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

public class Main {

    static char[][] map;

    static int DFS(int r, int c, char no) {
        if (r < 0 || r >= map.length) return 0;
        if (c < 0 || c >= map[0].length) return 0;
        if (map[r][c] != '1') return 0; // 이미 방문한 칸이면 무시
        map[r][c] = no;
        int count = 1; // 현재 칸의 수 1부터 시작
        count += DFS(r - 1, c, no); // 방문한 칸들의 수를 누적한다
        count += DFS(r + 1, c, no);
        count += DFS(r, c - 1, no);
        count += DFS(r, c + 1, no);
        return count; // 방문한 칸들의 수 리턴
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int N = scanner.nextInt();
        map = new char[N][];
        for (int r = 0; r < N; ++r)
            map[r] = scanner.next().toCharArray();
        ArrayList<Integer> result = new ArrayList<>();
        char no = '2';
        for (int r = 0; r < N; ++r)
            for (int c = 0; c < N; ++c)
                if (map[r][c] == '1')
                    result.add(DFS(r, c, no++));
        Collections.sort(result);
        System.out.println(result.size());
        for (int i : result)
            System.out.println(i);
        scanner.close();
    }
}
```
