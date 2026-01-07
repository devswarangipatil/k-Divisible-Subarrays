# k-Divisible-Subarrays

In a data analysis lab, a researcher is studying a long sequence of sensor readings collected over time.
Each reading is stored in an array nums of size n.
The researcher defines a special subarray as follows:
Consider any continuous segment of the array.
Count how many elements in that segment are divisible by a given integer k.
If this count itself is divisible by k, the segment is considered special.
Your task is to help the researcher determine how many special subarrays exist in the given sequence.

Input
The first line contains two integers 
n and k — the size of the array and the divisor.
The second line contains n integers — the elements of the array nums.

Output
Print a single integer — the total number of special subarrays.

Constraints
1≤n≤2×10 
1≤nums[i]≤10 
1≤k≤100
Example
Input
5 2
2 3 4 6 5

Output
7

Explanation
Here,
k=2. We look for subarrays where the number of elements divisible by 2 is itself divisible by 2.
Valid special subarrays are:
[2, 3, 4]
[3]
[3, 4, 6]
[3, 4, 6, 5]
[4, 6]
[4, 6, 5]
[5]
Since there are 7 such subarrays, the answer is 7.


n, k = map(int, input().split())
nums = list(map(int, input().split()))

freq = [0] * k
freq[0] = 1  # empty prefix

prefix = 0
ans = 0

for x in nums:
    if x % k == 0:
        prefix += 1

    mod = prefix % k
    ans += freq[mod]
    freq[mod] += 1

print(ans)
