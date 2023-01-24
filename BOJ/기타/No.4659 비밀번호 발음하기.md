백준 링크 : https://www.acmicpc.net/problem/4659

![image](https://user-images.githubusercontent.com/62640768/214246533-27b2f58c-8a33-4671-bb09-feaffcc75c34.png)

```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

/*
* 모음(a,e,i,o,u) 하나를 반드시 포함하여야 한다.
모음이 3개 혹은 자음이 3개 연속으로 오면 안 된다.
같은 글자가 연속적으로 두번 오면 안되나, ee 와 oo는 허용한다.
* */
public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;



        while(true) {
            st = new StringTokenizer(br.readLine());
            String pw = st.nextToken();
            if (pw.equals("end")) break;
            else {
                String vowels[] = {"a", "e", "i", "o", "u"};
                String consonant[] = {"b", "c", "d", "f", "g", "h", "j", "k", "l", "m", "n", "p", "q", "r", "s", "t", "v", "w", "x", "y", "z"};
                String arr[] = pw.split(""); // 비밀번호를 배열로 저장
                String checkTwo = "";
                boolean result = true;
                boolean checkMoum = false;

                for (String check : arr) {

                    if (!checkMoum) {
                        // 입력한 pw에 모음이 존재 할 경우 mo를 true로 변경
                        for (String mo : vowels) {
                            // 입력한 pw에 모음이 존재한다면 break;
                            if (check.equals(mo)) {
                                checkMoum = true;
                                result = true;
                                break;
                            } else {
                                // 존재하지 않는다면 false
                                result = false;
                            }
                        }
                    }

                    String regex = "[aeiou]{3,}|[^aeiou]{3,}";
                    Pattern pattern = Pattern.compile(regex);
                    Matcher matcher;
                    matcher = pattern.matcher(pw);
                    if(matcher.find()){
                        result = false;
                    }

                    // 같은 글자가 2번 나온다면
                    if (check.equals(checkTwo)) {
                        // 들어온 문자가 e나 o가 아니면 부적절한 pw
                        if (!check.equals("e") && !checkTwo.equals("e") && !check.equals("o") && !checkTwo.equals("o") ) {
                            result = false;
                        }
                    }
                    checkTwo = check;
                }
                if (result) {
                    System.out.println("<" + pw + ">" + " is acceptable.");
                } else {
                    System.out.println("<" + pw + ">" + " is not acceptable.");
                }
            }
        }
    }
}

```
