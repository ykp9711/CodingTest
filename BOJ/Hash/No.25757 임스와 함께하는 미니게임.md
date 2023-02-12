링크 : https://www.acmicpc.net/problem/25757


![image](https://user-images.githubusercontent.com/62640768/218301071-2dd1112a-6f05-4992-946f-0d807e4b864e.png)

필요 알고리즘 개념
- 해시를 사용한 집합과 맵, 문자열
- 문자열을 사용해 해싱하는 문제이다.

```
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.HashSet;
import java.util.StringTokenizer;
 
public class Main{
    
    private int getPlayerCnt(char c){
        switch(c){
            case 'Y': return 1;
            case 'F': return 2;
            case 'O': return 3;
        }
        return -1;
    }
    
    public void solution() throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
       
        StringTokenizer st = new StringTokenizer(br.readLine());
        int n = Integer.parseInt(st.nextToken());
        int p = getPlayerCnt(st.nextToken().charAt(0));
        HashSet<String> hs = new HashSet<>();
        int cnt = 0;
        while(n-->0){
            String cur = br.readLine();
            cnt += hs.contains(cur)?0:1;
            hs.add(cur);
        }
        System.out.println(cnt/p);
    }
    
    public static void main(String[] args) throws Exception{
        new Main().solution();
    }
}
```
