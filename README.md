# DP-0-N-
# Longest Increasing Subsequence | DP-3
bottom up solution

test=int(input())
while(test>0):
    n=int(input())
    l=[int(x) for x in input().split()]
    c=[1]*n
    for i in range(n-1,-1,-1):
        for j in range(i+1,n):
            if l[j]>l[i] and c[i]<c[j]+1:
                c[i]=c[j]+1
    print(max(c)) 
    test-=1
Input : arr[] = {50, 3, 10, 7, 40, 80}
Output : Length of LIS = 4
The longest increasing subsequence is {3, 7, 40, 80}

problem related to LIS 
[.] Longest Increasing Odd Even Subsequence
Given an array of size n. The problem is to find the length of the subsequence in the given array such that all the elements of the subsequence are sorted in increasing order and also they are alternately odd and even.
Note that the subsequence could start either with the odd number or with the even number.
HINT:- for i in range(n): 
        for j in range(i): 
            if (arr[i] > arr[j] and
                (arr[i] + arr[j]) % 2 != 0 and
                lioes[i] < lioes[j] + 1): 
                    lioes[i] = lioes[j] + 1
Input : arr[] = {5, 6, 9, 4, 7, 8}
Output : 4
{5, 6, 7, 8} is the required longest increasing odd even subsequence.
[.] printing LIS sequence

# Longest Common Subsequence | DP-4
--> recursive solution
def lcs(X, Y, m, n): 
  
    if m == 0 or n == 0: 
       return 0; 
    elif X[m-1] == Y[n-1]: 
       return 1 + lcs(X, Y, m-1, n-1); 
    else: 
       return max(lcs(X, Y, m, n-1), lcs(X, Y, m-1, n));  
X = "AGGTAB"
Y = "GXTXAYB"
print "Length of LCS is ", lcs(X , Y, len(X), len(Y))
--> bottom up sollution

test=int(input())
while(test>0):
    n,m=map(int,input().split())
    s1=input()
    s2=input()
    
    l=[[None for i in range(n+1)] for j in range(m+1)]
    for i in range(n+1):
        l[0][i]=0
    for i in range(m+1):
        l[i][0]=0
    for i in range(1,m+1):
        for j in range(1,n+1):
            if s2[i-1]==s1[j-1]:
                l[i][j]=1+l[i-1][j-1]
            else:
                l[i][j]=max(l[i-1][j],l[i][j-1])
    print(l[m][n])
    test-=1
problem related to LCS->
[.] Printing Longest Common Subsequence
hint-->
  i = m 
    j = n 
    while i > 0 and j > 0: 
  
        # If current character in X[] and Y are same, then 
        # current character is part of LCS 
        if X[i-1] == Y[j-1]: 
            lcs[index-1] = X[i-1] 
            i-=1
            j-=1
            index-=1
  
        # If not same, then find the larger of two and 
        # go in the direction of larger value 
        elif L[i-1][j] > L[i][j-1]: 
            i-=1
        else: 
            j-=1
  
    print "LCS of " + X + " and " + Y + " is " + "".join(lcs) 

