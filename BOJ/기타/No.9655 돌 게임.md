백준 링크 : https://www.acmicpc.net/problem/9655

![image](https://user-images.githubusercontent.com/62640768/212548718-5cfd2bcb-5d35-452f-87fd-86cdc6b09515.png)

```
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int count = sc.nextInt();
        int arr [] = {1,3};
        int num;
        String turn ="";
        while(count >0){
            Random random = new Random();
            if(count <3){
                num=arr[0];
            }else num=arr[random.nextInt(2)];
            turn = "SK";
            count= count - num;

            if(count ==0) break;

            if(count <3){
                num=arr[0];
            }else num=arr[random.nextInt(2)];
            turn ="CY";
            count= count - num;

            if(count ==0) break;
        }
        System.out.println(turn);

    }
}
```
