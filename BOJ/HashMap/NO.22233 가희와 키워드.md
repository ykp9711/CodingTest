링크 : https://www.acmicpc.net/problem/22233

![image](https://user-images.githubusercontent.com/62640768/218301513-6b3ffbb5-cfbf-44aa-b22e-07b660442cdb.png)
![image](https://user-images.githubusercontent.com/62640768/218301518-15c959d1-ea1e-4678-a997-146f48195e8b.png)

필요 알고리즘 개념
해시맵을 이용해서 키워드가 있는지 없는지 알아내고 있다면 카운트를 하나씩 감소해주는 식으로 구현

```
    import java.io.*;
    import java.util.*;


    public class Main {
        static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        static BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));


        public static void main(String[] args) throws IOException {
            int n, m;
            StringTokenizer st = new StringTokenizer(br.readLine());
            n = Integer.parseInt(st.nextToken());
            m = Integer.parseInt(st.nextToken());
            Map<String, Boolean> map = new HashMap<>();
            for (int i = 0; i < n; i++) {
                map.put(br.readLine(), true);
            }
            int cnt = n;
            for (int i = 0; i < m; i++) {
                st = new StringTokenizer(br.readLine(), ",");

                while (st.hasMoreTokens()) {
                    String s = st.nextToken();
                    if (map.containsKey(s)) {
                        map.remove(s);
                        cnt--;
                    }
                }
                bw.write(cnt + "\n");
            }
            bw.flush();
        }
    }
```
