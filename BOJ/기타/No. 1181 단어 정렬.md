백준 링크 : https://www.acmicpc.net/problem/1181

![image](https://user-images.githubusercontent.com/62640768/219945960-b8d8a14b-f5a9-4e0a-9618-1f328f58e363.png)

태그 : Comparator, TreeSet

```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(reader.readLine());
        ArrayList<String> list = new ArrayList<>();
        for (int i = 0; i < N; ++i)
            list.add(reader.readLine());
        list.sort((s1, s2) -> {
            int r = s1.length() - s2.length();
            if (r != 0) return r;
            return s1.compareTo(s2);
        });
        String prev = "";
        for (String s : list) {
            if (prev.equals(s) == false)
                System.out.println(s);
            prev = s;
        }
    }
}
```



```
list.sort((s1, s2) -> {
     int r = s1.length() - s2.length();
     if (r != 0) return r;
     return s1.compareTo(s2);
});
```

ArrayList 클래스의 sort 매소드를 호출하여 정렬한다.
이 메소드의 파라미터는 Comparator<String> 객체이다.
이 객체의 compare 메소드는, 두 문자열을 비교하여, 첫째 파라미터 값의 정렬 순서가 앞이면 음수를 리턴하고,
둘째 파라미터 값이 정렬 순서가 앞이면 양수를 리턴하고, 두 파라미터 값이 같으면 0을 리턴해야 한다.

이 Comparator 객체를 lambda expression 문법으로 구현하였다. 
