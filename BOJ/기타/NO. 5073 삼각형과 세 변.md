링크 : https://www.acmicpc.net/problem/5073

![image](https://user-images.githubusercontent.com/62640768/218301671-f11a8cfa-bec8-4887-92ca-eca03bb6696b.png)

```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;

		int a, b, c;
		
		while (true) {
			// input
			st = new StringTokenizer(br.readLine());
			a = Integer.parseInt(st.nextToken());
			b = Integer.parseInt(st.nextToken());
			c = Integer.parseInt(st.nextToken());

			// 0 0 0이 입력되면 종료한다.
			if (a == 0 && b == 0 && c == 0) break;
			
			if (a >= b + c || b >= c + a || c >= a + b) {
				// 삼각형의 조건 미충족
				System.out.println("Invalid");
			} else if (a == b && b == c && c == a) {
				// 세 변의 길이 모두 일치
				System.out.println("Equilateral");
			} else if (a == b || b == c || c == a) {
				// 두 변의 길이 일치
				System.out.println("Isosceles");
			} else if(a != b && b != c && c != a) {
				// 세 변의 길이 모두 불일치
				System.out.println("Scalene");
			}
		}
	}
	
}
```
