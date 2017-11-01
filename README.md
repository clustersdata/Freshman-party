# Freshman-party

Freshman party

Problem Description

开学了，又迎来了好多新生。ACMer想为新生准备一个节目。来报名要表演节目的人很多，多达N个，但是只需要从这N个人中选M个就够了，一共有多少种选择方法？

Input

数据的第一行包括一个正整数T，接下来有T组数据，每组数据占一行。

每组数据包含两个整数N（来报名的人数,1<=N<=30），M（节目需要的人数0<=M<=30）

Output

每组数据输出一个整数，每个输出占一行

Sample Input

5 3 2 5 3 4 4 3 6 8 0

Sample Output

3 10 1 0 1

代码：

#include<stdio.h>

#include<math.h>

int main()

{

    int T, n, m, i;
    
    double num;
    
    scanf("%d", &T);
    
    while (T--)
    
	{
  
        scanf("%d%d", &n, &m);
        
        num=1;
        
        for (i=1;i<=m;i++)
        
            num*=(1.0*(n-i+1)/i);
            
        printf("%.f\n",floor(num+0.5));
        
    }
    
    return 0;
    
}


方法二：

这里用到的数学公式为（注意用一维数组来计算此式的技巧）

代码：

#include<stdio.h>

#include<string.h>

#define MAX 1000

int arr[MAX];

long solve(int n,int m)

{

    int i,j;
    
arr[0]=1;

    for(i=1;i<=n;i++)
    
    {
    
        for(j=i;j>-1;j--)
        
        {
        
            if(j==0||i==j)    arr[j]=1;
            
            else        arr[j]+=arr[j-1];
            
        }
        
    }
    
    return arr[m];
    
}

int main()

{

    int num;
    
    int n,m;
    
    scanf("%d",&num);
    
    memset(arr,0,MAX*sizeof(int));
    
    while(num--)
    
    {
    
        scanf("%d%d",&n,&m);
        
        printf("%ld\n",solve(n,m));
        
    }
    
    return 0;
    
} 

