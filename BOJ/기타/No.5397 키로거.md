백준 링크 : https://www.acmicpc.net/problem/5397

![image](https://user-images.githubusercontent.com/62640768/221408811-64d05192-a5fa-4216-8a68-b96852264cdf.png)

필요 알고리즘 개념 : LinkedList, ListIterator

```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.ListIterator;

public class Main {
    public static void main(String[] args) throws NumberFormatException, IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        int T = Integer.parseInt(reader.readLine());
        for (int i = 0; i < T; ++i) {
            String s = reader.readLine();
            LinkedList<Character> list = new LinkedList<>();
            ListIterator<Character> iterator = list.listIterator();
            for (char c : s.toCharArray()) {
                switch (c) {
                case '<': if (iterator.hasPrevious()) iterator.previous(); break;
                case '>': if (iterator.hasNext()) iterator.next(); break;
                case '-':
                    if (iterator.hasPrevious()) {
                        iterator.previous();
                        iterator.remove();
                    }
                    break;
                default:
                    iterator.add(c);
                }
            }
            StringBuilder builder = new StringBuilder();
            for (char c : list)
                builder.append(c);
            System.out.println(builder.toString());
        }
    }
}

```
