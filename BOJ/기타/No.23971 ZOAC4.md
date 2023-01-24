백준링크 : https://www.acmicpc.net/problem/23971 
![image](https://user-images.githubusercontent.com/62640768/214250020-11ca7fa5-8cd1-47cb-a4f1-0afb3c34fe9b.png)

```
import java.io.*;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        String str = br.readLine();
        StringTokenizer st = new StringTokenizer(str);

        int H = Integer.parseInt(st.nextToken());
        int W = Integer.parseInt(st.nextToken());
        int N = Integer.parseInt(st.nextToken()); //세로줄크기
        int M = Integer.parseInt(st.nextToken()); //가로줄크기

        int A = (H-1)/(N+1)+1;
        int B = (W-1)/(M+1)+1;

        bw.write(A*B+"\n");
        bw.close();
    }
}
```
