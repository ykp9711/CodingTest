백준 링크 : https://www.acmicpc.net/problem/1991

![image](https://user-images.githubusercontent.com/62640768/219945370-9aabc27b-8a6a-430d-b7b0-1f3dd0ee4eea.png)


필요 알고리즘 개념
DFS, inorder, preorder, postorder

```
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class Main {
    static final int PRE = 0, IN = 1, POST = 2, LEFT = 0, RIGHT = 1;
    static Map<String, String[]> map = new HashMap<>();

    static void traverse(String id, int order) {
        if (id.equals(".")) return;
        String[] child = map.get(id);
        if (order == PRE) System.out.print(id);
        traverse(child[LEFT], order);
        if (order == IN) System.out.print(id);
        traverse(child[RIGHT], order);
        if (order == POST) System.out.print(id);
    }

    public static void main(String[] args) {
        try (Scanner scanner = new Scanner(System.in)) {
            int N = scanner.nextInt();
            for (int i = 0; i < N; ++i) {
                String id = scanner.next();
                String left = scanner.next();
                String right = scanner.next();
                map.put(id, new String[] { left, right });
            }
            traverse("A", PRE); System.out.println();
            traverse("A", IN);  System.out.println();
            traverse("A", POST); System.out.println();
        }
    }
}
```
