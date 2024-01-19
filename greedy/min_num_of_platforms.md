```java
import java.util.Arrays;

public class Solution {
    public static int calculateMinPatforms(int at[], int dt[], int n) {
        // Write your code here.

        Arrays.sort(at);
        Arrays.sort(dt);

        int platforms_needed = 1, result = 1;
        int i = 1, j = 0;

        while (i < n && j < n) {
            if (at[i] <= dt[j]) {
                platforms_needed++;     // ith train does not have a platform to stop on
                i++;                    // because i was overlapping and we've added a platform for it
            } else if (at[i] > dt[j]) {
                platforms_needed--;     // sufficient platforms are there
                j++;                    // because j isn't overlapping
            }

            if (platforms_needed > result)
                result = platforms_needed;
        }

        return result;

    }
}
```