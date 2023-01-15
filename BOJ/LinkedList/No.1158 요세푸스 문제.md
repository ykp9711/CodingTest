백준 링크 : https://www.acmicpc.net/problem/1158

![image](https://user-images.githubusercontent.com/62640768/212549290-a1b3ad86-548a-4f7a-8cb2-f42bf4a776e4.png)

```
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        LinkedList<Integer> List = new LinkedList<>();
        int N = sc.nextInt(); // 사람 수
        int K = sc.nextInt(); // 제거될 순서

        //링크드리스트에 사람 수만큼 입력
        for(int i=1;i<=N;i++) List.add(i);

        //출력
        System.out.print("<");

        //링크드리스트가 빌 때까지 반복
        while(!List.isEmpty()) {
            //제거될 순서만큼 반복
            for(int i=0;i<K;i++) {
                //K번이 되면 리스트에서 삭제하고,
                if(i==K-1) {
                    int a = List.remove();
                    //링크드리스트 크기가 0이라면 마지막엔 쉼표 없이 출력
                    if(List.size()==0) {
                        System.out.print(a);
                    }
                    else System.out.print(a + ", ");
                }
                //K번이 아니라면 삭제 후 다시 넣기
                else {
                    List.add(List.remove());
                }
            }
        }
        System.out.print(">");
    }
}
```
