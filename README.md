Sum of minimum absolute difference in C
Here, in this page we will discuss C Program to find sum of minimum absolute difference of the given array

To find minimum absolute difference of array we will take median of the given array and find out the absolute difference between median and each element of array and add all together

sum of minimum absolute difference
While loop in C
Method Discussed :
Method 1 : Using Brute Force Approach
Method 2 : Using Efficient solution
Method 1 :
Take a variable say result = INT_MAX, to hold the required minimum sum.
Run an outer loop from index 0 to n,
Create a variable say sum = 0,
Run an inner loop from index 0 to n,
Set, sum += abs(arr[i]-arr[j])
After complete iteration of inner loop set,
result = min(result, sum).
Print result.
Method 1 : Code in C
//Write a program to find sum of minimum absolute difference of the given array in C
#include<stdio.h>
#include<limits.h>

int main()
{
    int arr[]={2, 4, 5, 3};
    int result = INT_MAX;

    int n = sizeof(arr)/sizeof(arr[0]);

    for(int i=0; i<n; i++){
        int sum =0 ; // variable to hold the sum
        for(int j=0; j<n; j++){
            int x=arr[i]-arr[j];
            if(x<0)
                sum += -x;

            else sum += x;
        }    
    
        if(sum<result)
            result = sum;
        
    }
    printf("Minimum Absolute Difference Sum is %d", result);
    return 0;
}
Output
Minimum Absolute Difference Sum is 4
Related Pages
Determine Array is a subset of another array or not

Determine can all numbers of an array be made equal

Sort an array according to the order defined by another array 

Replace each element of the array by its rank in the array

Finding equilibrium index of an array

Method 2
Sort the array in increasing order.
Create a variable say median that store the median of the array in it.
If the size of array is even then median= (a[n/2]+a[n/2+1])/2, otherwise median = a[n/2], here a [] is the array and n is the size of the array.
Create a variable say sum that holds the sum in it and initialize it with 0.
Iterate over the array and add the absolute difference in the sum.
Print the sum.
Method 2 : Code in C
//Write a program to find sum of minimum absolute difference of the given array in C
#include<stdio.h>

void sort(int arr[],int n){
    
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(arr[i]<arr[j]){
                int temp=arr[i];
                arr[i]=arr[j];
                arr[j]=temp;
           }
        }
    }
}

int main()
{
    int arr[]={2, 4, 5, 3};

    int n = sizeof(arr)/sizeof(arr[0]);

    sort(arr, n);  //sort first array

    int median ; //variable to store the median

    if(n%2==0)
    median = ((arr[n/2]+arr[n/2+1])/2);

    else median = arr[n/2];

    int sum =0 ; // variable to hold the sum

    for(int i=0; i<n; i++){

        int x=arr[i]-median;
        if(x<0)
            sum += -x;

        else sum += x;
    }    
    printf("Minimum Absolute Difference Sum is %d", sum);
    return 0;
}
Output
Minimum Absolute Difference Sum is 4
