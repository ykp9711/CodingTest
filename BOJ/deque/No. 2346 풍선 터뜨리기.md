백준 링크: https://www.acmicpc.net/problem/2346

![image](https://user-images.githubusercontent.com/62640768/221408309-d02f56c8-2da4-4ef0-ab67-b954e94d0caa.png)

필요 알고리즘 개념 : deque

```
import java.io.IOException;
import java.util.ArrayDeque;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) throws NumberFormatException, IOException {
        var scanner = new Scanner(System.in);
        int N = scanner.nextInt();
        var deque = new ArrayDeque<int[]>(); // deque(양방향 큐)를 이용하여 회전을 구현함
        for (int i = 0; i < N; ++i) {
            int value = scanner.nextInt();
            int no = i + 1;
            deque.addLast(new int[] { no, value }); // 풍선 번호와 값을 큐에 등록
        }
        while (true) {
            // 큐의 선두 풍선을 터뜨림 (제거함)
            int[] a = deque.remove();
            int no = a[0], value = a[1];
            // 큐의 선두 항목을 제거하자 마자, 그 다음 항목이 한 칸 앞으로 와서 선두 항목이 되기 때문에
            // 양수 방향 이동은 1 적게 이동하면 된다
            if (value > 0) --value;
            System.out.print(no + (deque.size() > 0 ? " " : "\n"));    // 방금 꺼낸 풍선 번호를 출력함
            if (deque.size() == 0) break;    // 풍선을 다 꺼냈으면 종료
            for (int i = 0; i < Math.abs(value); ++i) // 이동 횟수 만큼 큐를 회전함
                if (value > 0)
                    deque.addLast(deque.removeFirst()); // 오른쪽 이동이면, 왼쪽으로 회전
                else
                    deque.addFirst(deque.removeLast());  // 왼쪽 이동이면, 오른쪽으로 회전
        }
    }

}
```

