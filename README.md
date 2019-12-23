# Ugly Number II

Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. 

```
Example:

Input: n = 10
Output: 12
Explanation: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.
```

```
Note:  1 is typically treated as an ugly number.
```

### Implementation

```java
public static int nthUglyNumber(int n) {
		if (n <= 0)
			return 0;

		ArrayList<Integer> list = new ArrayList<Integer>();
		list.add(1);

		int i = 0;
		int j = 0;
		int k = 0;

		while (list.size() < n) {
			int m2 = list.get(i) * 2;
			int m3 = list.get(j) * 3;
			int m5 = list.get(k) * 5;

			int min = Math.min(m2, Math.min(m3, m5));
			list.add(min);
			if (min == m2)
				i++;

			if (min == m3)
				j++;

			if (min == m5)
				k++;
		}

		return list.get(list.size() - 1);
}
```

### Code execution :
```
initialize
   list =  [ 1 ]
   i =  j = k = 0;

First iteration
   list[1] = Min(list[i]*2, list[j]*3, list[k]*5)
           = Min(2, 3, 5)
           = 2
   list    = [ 1 , 2 ]
   i = 1,  j = k = 0  (i got incremented ) 

Second iteration
   list[2] = Min(list[i]*2, list[j]*3, list[k]*5)
           = Min(4, 3, 5)
           = 3
   list    = [ 1 , 2 , 3 ]
   i = 1,  j =  1, k = 0  (j got incremented ) 

Third iteration
   list[3] = Min(list[i]*2, list[j]*3, list[k]*5)
           = Min(4, 6, 5)
           = 4
   list    = [ 1 , 2 , 3 ,  4 ]
   i = 2,  j =  1, k = 0  (i got incremented )

Fourth iteration
    list[4] = Min(list[i]*2, list[j]*3, list[k]*5)
            = Min(6, 6, 5)
            = 5
    list    = [ 1 , 2 , 3 ,  4 , 5 ]
    i = 2,  j =  1, k = 1  (k got incremented )

Fifth iteration
    list[5] = Min(list[i]*2, list[j]*3, list[k]*5)
            = Min(6, 6, 10)
            = 6
    list    = [ 1 , 2 , 3 ,  4 , 5 , 6 ]
    i = 3,  j =  2, k = 1  (i and j got incremented )

```
