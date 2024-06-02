### Trail of ones

**Easy**Accuracy: **55.03%**Submissions: **4K+**Points: **2**

[

In need of more Geekbits? Win from a pool of 3500+ Geekbits via DSA-based Coding Contest every sunday!

![banner](https://media.geeksforgeeks.org/img-practice/external-1657081738.svg)

](https://www.geeksforgeeks.org/events/rec/gfg-weekly-coding-contest)

Given a number **n**, find the number of binary strings of length **n** that contain consecutive 1's in them. Since the number can be very large, return the answer after modulo with 1e9+7.

**Example 1:**

**Input:**
n = 2
**Output:**
1
**Explanation:**
There are 4 strings of 
length 2, the strings 
are 00, 01, 10, and 
11. Only the string 11 
has consecutive 1's.

**Example 2:**

**Input:**
n = 5
**Output:**
19
**Explanation:**
There are 19 strings
having consecutive 1's. 

**Your Task:**

You don't need to read input or print anything. Your task is to complete the function numberOfConsecutiveOnes() which takes an integer n and returns the number of binary strings that contain consecutive 1's in them.

**Expected Time Complexity:** O(n)  
**Expected Auxiliary Space:** O(n)  
**  
Constraints**  
2 <= **n** <= 10<sup>5</sup>

Seen this question in a real interview before ?1/4

YesNo

**Company Tags**

[Amazon](https://www.geeksforgeeks.org/explore/?company[]=Amazon)

**Topic Tags**

[Bit Magic](https://www.geeksforgeeks.org/explore/?category[]=Bit%20Magic)[Data Structures](https://www.geeksforgeeks.org/explore/?category[]=Data%20Structures)

Discussions ( 55 Threads )[](https://discuss.geeksforgeeks.org/dashboard?utm-source=practice&utm-event=comment-thread)

Most Recent

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

Submit

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Shashi ranjan](https://auth.geeksforgeeks.org/user/shashi345jbd/practice/)37 minutes ago

class Solution {

public:  
    int numberOfConsecutiveOnes(int n) {  
          
        vector<int> dp(n+1, 0);  
          
        dp\[0\] = 0;  
        dp\[1\] = 0;  
        dp\[2\] = 1;  
          
        if (n < 3) {  
            return dp\[n\];  
        }  
          
        int a=0;  
        int b=1;  
          
        for (int i = 3; i <= n; i++) {  
              
            int c=(a+b)%1000000007;  
              
            dp\[i\] =(dp\[i - 1\] \* 2)%1000000007+(c)%1000000007;  
              
           
            dp\[i\]=dp\[i\]%1000000007;  
                 
            a=b;  
            b=c;  
        }  
        return dp\[n\];

    }  
};

concept;

n=1  0\*2+0=0

n=2   0\*2+1=1

n=3  1\*2+1  = 3

n=4   3\*2+2  = 8

n=5   8\*2+3 = 19

n=6  19\*2+5 = 43

n=7  43\*2+8 = 94

n=8  94\*2+13  = 201

........aso

0+1+1+2+3+5+8+13..... is fibonacci series

and rest is maths

curr\_ans=prev\_ans\*2+fib();

..... see less

1

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[smk](https://auth.geeksforgeeks.org/user/sudomoon/practice/)

(Edited)03/06/2024, 01:31

44 minutes ago

## ✅ Python

```
    def numberOfConsecutiveOnes (ob,n):
        mod = int(1e9+7)
        a, b, c = 0, 1, 0
        for i in range(2, n+1):
            # power of two can blow up fast so, keep running mod
            a, b, c = b, (a+b)%mod, ((c*2) % mod + b)%mod
        return c
```

..... see more

0

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Anshuman Gupta](https://auth.geeksforgeeks.org/user/guptanshuman7/practice/)67 minutes ago

## **using fabonacci two variable and basic observation**

class Solution {  
  public:  
    int numberOfConsecutiveOnes(int n) {  
        int ans=0;  
        int a=0;  
        int b=1;  
        for(int i=2;i<=n;i++){  
            ans=((ans\*2)%1000000007+b)%1000000007;  
            int temp=b;  
            b=(a+b)%1000000007;  
            a=temp;  
        }  
        return ans%1000000007;  
    }  
};

..... see more

0

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Sagar ray](https://auth.geeksforgeeks.org/user/roy_707/practice/)94 minutes ago

# All Possible Approaches || Recursion || Memoization || Tabulation || Space Optimized || ✅🚀

**Recursion (TLE)**

```
// Recursion - TLE
int mod=1e9+7;
class Solution {
    public:
    int help(int n,int flag)
    {
        //base case
        if(n==0)
        {
            if(flag>=2)
            return 1;
            else
            return 0;
        }
        
        //recursive calls
        //and small calculation
        
        int a=0;
        int b=0;
        
        if(flag==2)
        a=help(n-1,flag);
        else
        a=help(n-1,0);
        
        if(flag==0)
        b=help(n-1,1);
        else
        b=help(n-1,2);
        
        return (a+b)%mod;
    }
    int numberOfConsecutiveOnes(int n) {
        int fnCall=help(n,0);
        return fnCall;
    }
};
```

**Memoization**

```
// Memoization
int mod=1e9+7;
class Solution {
    public:
    int help(int n,int flag,vector<vector<int>>& memo)
    {
        //base case
        if(n==0)
        {
            if(flag>=2)
            return 1;
            else
            return 0;
        }
        
        //memo check
        if(memo[n][flag]!=-1)
        return memo[n][flag];
        
        //recursive calls
        //and small calculation
        
        int a=0;
        int b=0;
        
        if(flag==2)
        a=help(n-1,flag,memo);
        else
        a=help(n-1,0,memo);
        
        if(flag==0)
        b=help(n-1,1,memo);
        else
        b=help(n-1,2,memo);
        
        return memo[n][flag]=(a+b)%mod;
    }
    int numberOfConsecutiveOnes(int n) {
        vector<vector<int>> memo(n+1,vector<int>(3,-1));
        int fnCall=help(n,0,memo);
        return fnCall;
    }
};
```

**Tabulation**

```
// Tabulation
int mod=1e9+7;
class Solution {
    public:
    int numberOfConsecutiveOnes(int n) {
        vector<vector<int>> dp(n+1,vector<int>(3,0));
        dp[0][2]=1;
        
        for(int i=1;i<=n;i++)
        {
            for(int j=0;j<=2;j++)
            {
                int a=0;
                int b=0;
                
                if(j==2)
                a=dp[i-1][j];
                else
                a=dp[i-1][0];
                
                if(j==0)
                b=dp[i-1][1];
                else
                b=dp[i-1][2];
                
                dp[i][j]=(a+b)%mod;
            }
        }
        
        return dp[n][0];
    }
};
```

**Space Optimized**

```
// Space optimized
int mod=1e9+7;
class Solution {
    public:
    int numberOfConsecutiveOnes(int n) {
        vector<int> pre(3,0);
        pre[2]=1;
        
        for(int i=1;i<=n;i++)
        {
            vector<int> curr(3,0);
            for(int j=0;j<=2;j++)
            {
                int a=0;
                int b=0;
                
                if(j==2)
                a=pre[j];
                else
                a=pre[0];
                
                if(j==0)
                b=pre[1];
                else
                b=pre[2];
                
                curr[j]=(a+b)%mod;
            }
            pre=curr;
        }
        
        return pre[0];
    }
};
```

## **Connect With Me**

- _GITHUB_ -   _https://github.com/roy7077_
- _LINKEDIN_\- _https://www.linkedin.com/in/sagar-ray-3a6297225/_

# **If you found this helpful, kindly consider upvoting. Have a great time coding, my friend!**

..... see more

3

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Varad Jadhav](https://auth.geeksforgeeks.org/user/varadjadhav/practice/)119 minutes ago

**Easy c++ solution using DP**

```
int mod=1e9+7;
    long long power(long long a,long long b){
        long long ans=1;
        while(b){
            if(b%2)ans*=a;
            b>>=1;
            a*=a;
            a%=mod;
            ans%=mod;
        }
        return ans;
    }
    long long solve(int n,vector<int> &dp){
        if(n==2) return 1;
        if(n==3) return 3;
        if(dp[n]!=-1)return dp[n];
        return dp[n]=((solve(n-1,dp) + power(2,n-2))%mod+ solve(n-2,dp))%mod;
    }
    int numberOfConsecutiveOnes(int n) {
        vector<int> dp(n+1,-1);
        return solve(n,dp);
    }
```

..... see more

0

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[monika jha](https://auth.geeksforgeeks.org/user/divakarmohdjx/practice/)2 hours ago

**c++ easy solution**

int numberOfConsecutiveOnes(int n) { const int MOD = 1e9 + 7; if (n == 0) return 0; // dp\[i\] will store the number of binary strings of length i without consecutive 1's vector<int> dp(n + 1, 0); // Base cases dp\[0\] = 1; // An empty string has 1 way, trivially. dp\[1\] = 2; // "0" and "1" if (n >= 2) { dp\[2\] = 3; // "00", "01", "10" } // Fill dp array for (int i = 3; i <= n; ++i) { dp\[i\] = (dp\[i-1\] + dp\[i-2\]) % MOD; } // Total number of binary strings of length n is 2^n long long totalStrings = 1; for (int i = 0; i < n; ++i) { totalStrings = (totalStrings \* 2) % MOD; } // Number of strings without consecutive 1's is dp\[n\] int withoutConsecutiveOnes = dp\[n\]; // Number of strings with consecutive 1's is the difference int result = (totalStrings - withoutConsecutiveOnes + MOD) % MOD; return result; } };

..... see more

0

1

Reply

(Show 1 Replies)

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Harshit](https://auth.geeksforgeeks.org/user/harshitdhundale/practice/)2 hours ago

Python Code:  
  

#### `**_class Solution:_**`  
 `**_def numberOfConsecutiveOnes(self, n):_**`  
 `**_MOD = 10**9 + 7_**`

####  `**_if n == 1:_**`  
 `**_return 0_**`

####  `**_dp = [[0]*2 for _ in range(n+1)]_**`

####  `**_# Base cases_**`  
 `**_dp[1][0] = 1_**`  
 `**_dp[1][1] = 1_**`

####  `**_for i in range(2, n+1):_**`  
 `**_dp[i][0] = (dp[i-1][0] + dp[i-1][1]) % MOD_**`  
 `**_dp[i][1] = dp[i-1][0] % MOD_**`

####  `**_total_valid_strings = (dp[n][0] + dp[n][1]) % MOD_**`  
 `**_total_strings = pow(2, n, MOD)_**`  
 `**_answer = (total_strings - total_valid_strings + MOD) % MOD_**`

####  `**_return answer_**`

  
  

..... see more

0

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Sriharsha Yelugu](https://auth.geeksforgeeks.org/user/yelugusriharsha/practice/)1 month ago

**#easy java solution**

class Solution {  
    static int numberOfConsecutiveOnes(int N) {  
        // Base cases  
        if (N == 2) return 1;  
        if (N == 3) return 3;  
          
        // Recursive calculation  
        return numberOfConsecutiveOnes(N - 1) + power(2, N - 1) / 2 + numberOfConsecutiveOnes(N - 2);  
    }

    static int power(int base, int exponent) {  
        // Base case: exponent is 0  
        if (exponent == 0) return 1;

        // Recursive calculation for positive exponent  
        if (exponent > 0) {  
            int result = base;  
            for (int i = 1; i < exponent; i++) {  
                result \*= base;  
            }  
            return result;  
        }   
        // Recursive calculation for negative exponent  
        else {  
            int result = base;  
            for (int i = 1; i < -exponent; i++) {  
                result \*= base;  
            }  
            return 1 / result;  
        }  
    }  
}

..... see more

0

8

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Timofey Lastname](https://auth.geeksforgeeks.org/user/rvtiemdd/practice/)1 month ago

SImple optimized dp solution in Python3:

```
class Solution:
    def numberOfConsecutiveOnes (ob,N):
        # code here 
        
        if N ==2:
            
            return 1
            
        elif N ==3:
            
            return 3
            
        
            
        n0 = 0
        
        n1 = 0
        
        n2 = 1
        
        
        
        
        for i in range(3, N+1):
            
            
            n0,n1, n2= n1, n2, n1 + n2 + 2**(i-2)
            
            
        return n2
```

..... see more

1

2

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Husoski](https://auth.geeksforgeeks.org/user/husoski/practice/)5 months ago

Another way to view this problem is the number of different outcomes of N coin tosses that have consecutive heads.  Looking around for that might get you to https://oeis.org/A008466, where you'll find a neat formula for the answer:  
    f(n) = 2^n - Fibonacci(n+2)  
Scroll down to "FORMULAS", and there's a more directly useful formula:  
    f(1) = 0, f(2) = 1, f(3) = 3  
    f(n) = 3\*f(n-1) - f(n-2) - 2\*f(n-3) \[for all n>3\]

That gives a simple O(n) time and O(1) space solution.

..... see more

1

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Akash Singh](https://auth.geeksforgeeks.org/user/akashja8/practice/)5 months ago

class Solution{     
public:  
    int solve(int n)  
    {  
        if(n==2) return 1;  
        if(n==3) return 3;  
        int x=solve(n-1);  
        int y=pow(2,n-1)/2;  
        int z=solve(n-2);  
        return x+y+z;  
    }  
    int numberOfConsecutiveOnes(int n){  
        // code here   
        if(n==2) return 1;  
        if(n==3) return 3;  
          
       return solve(n);  
          
    }  
};

..... see more

0

2

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Ayushi Agarwal](https://auth.geeksforgeeks.org/user/agarwalayushi735/practice/)7 months ago

\----- Easy 2 line solution (using recursion)--------

  
class Solution{     
public:  
    int numberOfConsecutiveOnes(int N){  
      if(N==2) return 1;  
      if(N==3) return 3;  
        
      return numberOfConsecutiveOnes(N-1) + pow(2,N-1)/2+ numberOfConsecutiveOnes(N-2);  
    }  
};

..... see more

2

8

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Chiru vishal](https://auth.geeksforgeeks.org/user/molletichiruvishal/practice/)9 months ago

class Solution{     
public:  
    int numberOfConsecutiveOnes(int N){  
          
        int countend0=1,countend1=1,sum=countend0+countend1;  
        for(int i=2;i<=N;i++){  
            countend1=(countend0);  
            countend0=sum;  
            sum=(countend1+countend0);  
        }  
        return pow(2,N)-sum;  
    }  
};

..... see more

1

2

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[ManideepS](https://auth.geeksforgeeks.org/user/manideepkkl9/practice/)10 months ago

**int numberOfConsecutiveOnes(int N){  
        int dp\[N+1\];  
        dp\[0\]=0;  
        dp\[1\]=0;  
        dp\[2\]=1;  
        for(int i=3;i<N+1;i++){  
            dp\[i\]=(dp\[i-1\]+dp\[i-2\])+pow(2,i-2);  
        }  
        return dp\[N\];  
    }**

..... see more

1

2

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Hamza Bharmal](https://auth.geeksforgeeks.org/user/b_hamza/practice/)11 months ago

**Easiest Approach**

If we trace the pattern for N values, we observe that 

possible combinations for N are : Combinations for (N-1)\*2 + Fibonacci's Nth Term.

        if(N == 1){  
            return 0 ;  
        }  
        else{  
            int a = 1;  
            int b = 1 ;  
            int c = 2 ;  
            int count = 1 ;  
            for(int i = 2 ; i < N ; i++){  
                c = a+b ;  
                count = count\*2 + b ;  
                a=b;  
                b=c;  
            }  
              
            return count ;  
        }  
        

..... see more

1

1

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[MD Mostafa Kamal](https://auth.geeksforgeeks.org/user/m0stafa_/practice/)11 months ago

For a string which will costruct only 5 numbers of binary number as 1s,0s.  
Now you have to calculate that how many string which doesn't contain any consecutive 1's .  
  
it makes like a fibonacci series.

> void generate(){
> 
>          dp\[0\] = 1;  
>          dp\[1\] = 2;  
>          for(int i=2 ; i<= 30; i++){  
>              dp\[i\] = ((dp\[i-1\]) + (dp\[i-2\]));  
>          }  
>     }

for n size of string ,it can make 2^n number of different string .  
  
now determine that   
total\_distinct\_string = consecutive\_1's +not\_consecutive 1's  
  
int numberOfConsecutiveOnes(int N){  
        generate();  
         return (1<<N)-dp\[N\];  
    }

..... see more

0

0

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Divyansh Gupta](https://auth.geeksforgeeks.org/user/divyanshgupta0103/practice/)11 months ago

int fib(int n){  
    if(n==3) return 1;  
    if(n==4) return 2;  
    return fib(n-1)+fib(n-2);  
}  
    int numberOfConsecutiveOnes(int N){  
        if(N<=2) return N-1;  
        return 2\*numberOfConsecutiveOnes(N-1)+fib(N);  
    }

..... see more

1

1

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Jeremy Phan](https://auth.geeksforgeeks.org/user/jeremypy0p7/practice/)2 years ago

```
#Python3 Solution
def numberOfConsecutiveOnes (ob,N):
    x, a, b = 1, 0, 0
    for i in range(N-1):
        c = x + a + b
        x, a, b = x<<1, c, a
    return c
```

..... see more

1

1

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Maddigunta Narendra](https://auth.geeksforgeeks.org/user/naren69/practice/)2 years ago

```
class Solution{   
    public:
    long long int dp[30];
	const int mod = 1e9+7;
	int fc = 0;
	private:
	void generate(){
	    dp[0] = 1;
	    dp[1] = 2;
	    for(int i=2 ; i<= 30; i++){
	        dp[i] = ((dp[i-1])%mod + (dp[i-2])%mod)%mod;
	    }
	}
	public:
    int numberOfConsecutiveOnes(int N){
        // code here 
        if(fc == 0){
            generate();
            fc++;
        }
        return (1<<N)-dp[N];
        
    }
};
```

..... see more

0

1

Reply

![User](https://media.geeksforgeeks.org/img-practice/user_web-1598433228.svg)

[Alok Singh](https://auth.geeksforgeeks.org/user/aloksinghmp55/practice/)2 years ago

int numberOfConsecutiveOnes(int N){

        int ans;

        int first=0;

        int second=1;

        for(int i=1;i<N+2;i++){

            ans=first+second;

            first=second;

            second=ans;

        }

        ans=pow(2,N)-ans;

        return ans;

    }

..... see more

0

0

Reply

Load More Comments

Report An IssueIf you are facing any issue on this page. Please let us know.