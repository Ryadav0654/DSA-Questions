# Minimum number of moves to seat everyone

> Question link:
> https://leetcode.com/problems/minimum-number-of-moves-to-seat-everyone/description/?envType=daily-question&envId=2024-06-13

### Approach:
1. **Sort both vectors**: The function sorts both the `seats` and `students` vectors in ascending order. Sorting ensures that the positions are arranged properly for comparison.

2. **Iterate over the elements**: The function iterates through the elements of both vectors simultaneously using a loop.

3. **Calculate the absolute difference**: For each corresponding seat and student position, it calculates the absolute difference between the student's position and the seat's position. This absolute difference represents the number of moves needed to seat the student at that particular seat.

4. **Accumulate the total sum**: It accumulates the absolute differences calculated in the previous step into a variable named `sum`.

5. **Return the total sum**: Finally, the function returns the total sum, which represents the minimum number of moves required to seat all students.

### Code:

```C++
 int minMovesToSeat(vector<int>& seats, vector<int>& students) {
        sort(seats.begin(), seats.end());
        sort(students.begin(), students.end());

        int sum = 0;
        for(int i = 0; i< seats.size(); i++){
            // sum += max(students[i], seats[i]) - min(students[i], seats[i]);
            sum += abs(students[i] - seats[i]);
        }

        return sum;
    }
```
**Time Complexity:**  `O(nlog(n))`, where `n` is the length of the `seats` and `students` vectors.

**Space Complexity:** `O(1)`.
