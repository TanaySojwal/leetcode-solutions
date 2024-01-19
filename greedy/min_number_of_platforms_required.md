```java
public class Solution {
    public static int calculateMinPatforms(int at[], int dt[], int n) {
        // first solution to find the overlapping schedules
        int max = 1;
        for (int i = 0; i < n; i++) {
            int count = 1;
            for (int j = i + 1; j < n; j++) {
                if ((at[j] >= at[i] && at[j] <= dt[i]) || (dt[j] >= at[i] && dt[j] <= dt[i])) {
                    count++;
                }
            }
            if (count > max)
                max = count;
        }
        return max;
    }
}
```
