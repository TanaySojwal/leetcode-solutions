```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Solution {

    static class Meeting {
        int start;
        int end;
        int pos;
        Meeting(int start, int end, int pos) {
            this.start = start;
            this.end = end;
            this.pos = pos;
        }
    }

    static class MeetingComparator implements Comparator<Meeting> {
        @Override
        public int compare(Meeting o1, Meeting o2) {
            if (o1.end < o2.end)
                return -1;
            else if (o1.end > o2.end)
                return 1;
            else if (o1.pos < o2.pos)
                return -1;
            else
                return 1;
        }
    }

    public static int maximumMeetings(int []start, int []end) {
        List<Meeting> meets = new ArrayList<>();
        for (int i = 0; i < start.length; i++)
            meets.add(new Meeting(start[i], end[i], i + 1));

        MeetingComparator mc = new MeetingComparator();
        Collections.sort(meets, mc);

        int maxMeets = 1;               // at least the first meet can be scheduled
        int limit = meets.get(0).end;   // first limit will be the first meet's end time

        for (int i = 1; i < meets.size(); i++) {
            if (meets.get(i).start > limit) {
                limit = meets.get(i).end;
                maxMeets++;
            }
        }
        return maxMeets;
    }
}

```
