백준 링크 : https://www.acmicpc.net/problem/2217

![image](https://user-images.githubusercontent.com/62640768/221408557-bb1a12c9-e2ee-4c85-a48e-0426249fd3ba.png)


문제풀이 힌트

밧줄 허용 중량 오름차순으로 정렬한다.
i번째 밧줄보다 크거나 같은 중량을 견딜 수 있는 밧줄은 N-i개이다.
그 N-i개의 밧줄 중에서 허용 중량이 가장 작은 것은 i번째 밧줄이다.
그 N-i개의 밧줄을 을 모두 사용하면, (i번째밧줄허용중량 * N-i개) 중량을 견딜 수 있다. 


```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) throws NumberFormatException, IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(reader.readLine());
        int[] A = new int[N];
        for (int i = 0; i < N; ++i)
            A[i] = Integer.parseInt(reader.readLine());
        Arrays.sort(A); // 허용 중량 배열을 오름차순으로 정렬한다.
        int max = 0; // 구해야할 최대값
        for (int i = 0; i < N; ++i)
          // i번째 배열보다 더 큰 중량을 견딜 수 있는 밧줄은 N-i개이다.
          // 그 N-i개 밧줄이 견딜 수 있는 중량은 A[i] * (N - i) 이다.
            max = Math.max(max, A[i] * (N - i));
        System.out.println(max);
    }
}

```
