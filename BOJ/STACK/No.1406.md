백준 1406번 : https://www.acmicpc.net/problem/1406

![image](https://user-images.githubusercontent.com/62640768/212547004-d67862b1-2364-4f08-85ba-9c28b418ee89.png)

![image](https://user-images.githubusercontent.com/62640768/212547030-421a8eff-61cc-4858-9bb0-48f74c5a9e12.png)

```
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Stack;

public class Main {
// 두 가지 스택을 선언하고, 커서를 기준으로 letf , right 스택을 사용하여 입력된 명령을 수행한다.
    public static void main(String[] args) throws Exception {
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        // 입력 문자열
        String str = bf.readLine();
        // 명령 행 개수
        int n = Integer.parseInt(bf.readLine());
        // 스택 선언
        Stack<Character> left = new Stack<>();
        Stack<Character> right = new Stack<>();
        for (int i = 0; i < str.length(); i++) {
            // 명령어가 수행되기 전에 커서는 문장의 맨 뒤에 위치해 있으므로
            left.push(str.charAt(i));
        }
        while (n > 0) {
            n--;
            String[] line = bf.readLine().split(" ");
            // 커서 왼쪽 한칸 이동
            if (line[0].equals("L")) {
                if(!left.empty()){
                    right.push(left.pop());
                }
            }
            // 커서 오른쪽 한칸 이동
            else if (line[0].equals("D")) {
                if(!right.empty()){
                    left.push(right.pop());
                }
            }
            // 커서 왼쪽 문자 삭제
            else if (line[0].equals("B")) {
                if(!left.empty()){
                    left.pop();
                }
            }
            // P 다음 문자 왼쪽 추가
            else if (line[0].equals("P")) {
                left.push(line[1].charAt(0));
            }
        }

        StringBuilder sb = new StringBuilder();
        while(!left.isEmpty()){
            right.push(left.pop());
        }
        while(!right.isEmpty()){
            sb.append(right.pop());
        }
        System.out.println(sb);
    }
}

```
