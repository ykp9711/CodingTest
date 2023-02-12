링크 : https://www.acmicpc.net/problem/17484 

![image](https://user-images.githubusercontent.com/62640768/218301282-ddaf6b26-4afc-4c74-9f44-214a07f67a86.png)
![image](https://user-images.githubusercontent.com/62640768/218301287-1ee917f2-1864-4716-abf4-a059b3916883.png)

필요 알고리즘 개념
dfs 함수를 구현하여 해결하는 문제이다.
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {
	
	public static void main(String[] args) throws IOException {
		// 입력
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int n = Integer.parseInt(st.nextToken());
		int m = Integer.parseInt(st.nextToken());
		int[][][] dp = new int[n+1][m][3];
		int[][] graph = new int[n][m];
		final int INF = (int)1e9;
		
		for(int i=0;i<n;i++) {
			st = new StringTokenizer(br.readLine());
			for(int j=0;j<m;j++) {
				graph[i][j] = Integer.parseInt(st.nextToken());
			}
		}
		for(int i=1;i<=n;i++) {
			for(int j=0;j<m;j++) {
				Arrays.fill(dp[i][j], INF);
			}
		}
		
		// 3차 dp
		for(int i=1;i<=n;i++) {	
			for(int j=0;j<m;j++) {
				if(j < m-1) {
					dp[i][j][0] = Math.min(dp[i-1][j+1][1], dp[i-1][j+1][2]) + graph[i-1][j]; 
				} 
				if(j > 0) {
					dp[i][j][2] = Math.min(dp[i-1][j-1][0], dp[i-1][j-1][1]) + graph[i-1][j]; 
				}
				dp[i][j][1] = Math.min(dp[i-1][j][0], dp[i-1][j][2]) + graph[i-1][j];
			}
		}
		
		// 최솟값 출력
		int ans = Integer.MAX_VALUE;
		for(int i=0;i<m;i++) {
			for(int j=0;j<3;j++) {
				ans = Math.min(ans, dp[n][i][j]);
			}
		}
		System.out.println(ans);
		br.close();
	}
}
```
