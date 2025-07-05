'''Array Operations
program to consider a list arr=[10, 20, 30, 40] and perform insert operations
and deletion with 50 an d25 at position 2 respectively ,delete 30 and travers  the 
array to fetch a number 52 is present or not 
'''
arr= [10,20,30,40]
#insert
arr.append(50)
arr.insert(2, 25)
#print(arr)
for i in arr:
    print(i, end=' ')
#deletion
arr.remove(30)
arr.pop
#print(arr)
#traversal
for i in arr:
    print(i, end=' ')    
#searching
print("/n 25 in array? ", 25 in arr) 








'''program to check whether the given string is pallindrome or not and count the 
palindromic characters which are repeated
str=madam
output: {'m':2, 'a':2, 'd':1)
str=malayalam'''
txt=input("enter a name:")
if txt==txt[::-1]:
    print("pallindrome")
else:
    print("Not")
freq= {}
for ch in txt:
    freq[ch]=freq.get(ch,0)+1
    print(freq)






"SEARCHINGS":
         Linear Search
         Binary Search
         Sentinel Search
         Fibonacci Search
         Interpolation Search




         




linear search:
in sorted or unsorted arrays
[45,-9,77,32]
1. arr of list of size n
2. key for search element
3. start with zero index
4. compare arr[i]==key
   arr[i]=key return index
   else not (move to next index)
5. repeat same steps till n-1
6. if no match return -1 







"LINEAR SEARCH:"


def linear_search(arr,key):
    for i in range(len(arr)):
        if arr[i]==key:
            return i
    return -1
size=int(input("enter the size of array:"))
arr=[]
print("enter the elements:")
for i in range(size):
    num=int(input(f"Element {i+1}:"))
    arr.append(num)
key=int(input("Enter the element top search:"))
result=linear_search(arr,key)
if result!=-1:
    print(f"\n Element {key} found at {result}")
else:
    print(f"\n Element {key} not found at {result}")
    
    






binary search:
1. array must be sorted
2. array is divided into 2 seperate equivalent halfs
3. set low & high 0-->n-1
4. condition low<=high
5. mid=low+high//2
6. arr[mid]==key return mid
7. arr[mid]<key low mid+1
8. arr[mid]>key high mid-1
9. not found return -1
     












"BINARY SEARCH":
def binary_search(arr,key):
    low=0
    high=len(arr)-1
    while low<=high:
        mid=(low+high)//2
        if arr[mid]==key:
            return mid
        elif arr[mid]<key:
            low=mid+1
        else:
            high=mid-1
    return -1
size=int(input("enter the size of array:"))
arr=[]
print("enter the elements:")
for i in range(size):
    num=int(input(f"Element {i+1}:"))
    arr.append(num)
key=int(input("Enter the element top search:"))
result=binary_search(arr,key)
if result!=-1:
    print(f"\n Element {key} found at {result}")
else:
    print(f"\n Element {key} not found at {result}")
         



'''#jump search
1. size n /sorted
2. create a block key
3.search operation will be performed
arr[m]<var/ke < arr(k+1)[m]
4. compare each jump linearly'''






"JUMP SEARCH":

import math
def jump_search(arr,target):
    if not arr:
        return -1
    n= len(arr)
    step= int(math.sqrt(n))
    prev=0
    while prev<n and arr[prev]<target:
        prev+=step
    for i in range(max(0,prev-step), min(n,prev+1)):
        if arr[i]==target:
            return i
    return -1
arr=[1,3,5,7,9,11]
target=7
result=jump_search(arr, target)
print(f" Element {target} found at index: {result}")




"EXPONENTIAL"

1. sorted numers searching
2. check the array !=0m
3. check the first element
4. find the range using exponential
while for boundary
identify within boundary
5. range perform binary search
6. return result'''




def bsearch_range(arr,target,left,right):
    while left<=right:
        mid=(left+right)//2
        if arr[mid]==target:
            return mid
        elif arr[mid]<target:
            left=mid+1
        else:
            right=mid-1
    return -1
def expo_search(arr,target):
    if not arr:
        return -1
    if arr[0]==target:
        return 0
    n=len(arr)
    i=1
    while i<n and arr[i]<=target:
        i*=2
    return bsearch_range(arr,target,i//2,min(i,n-1))
arr=[2,4,6,8,10,12,14]
target=10
result=expo_search(arr,target)
print(f"Element {target} found at index: {result}")





"FIBONACCI SEARCH"
1. find smallest fibo number'''







def fibsearch(arr,target):
    if not arr:
        return -1
    n=len(arr)
    fib2=0
    fib1=1
    fib=fib2+fib1
    while fib<n:
        fib2=fib1
        fib1=fib
        fib=fib2+fib1
    offset=-1
    while fib>1:
        i=min(offset+fib2,n-1)
        if arr[i]==target:
            return i
        elif arr[i]:
            offset=i
            fib=fib1
            fib1=fib2
            fib2=fib-fib1
        else:
            fib=fib2
            fib1=fib1-fib2
            fib2=fib-fib1
    if fib==1 and offset+1<n and arr[offset+1]==target:
        return offset+1
    return -1
arr=[2,4,6,8,10,12]
target=10
result=fibsearch(arr,target)
print(f"Element {target} found at index: {result}")



"SELECTION SORT"
1. start from the first element in the list/array
2. arr[0]= min
3. compare with all the remaining elements to find the real lowest element
4. perform swapping with current position
5. repeat the same with adding positional values for each , min check

for-->0 to n-1:
            min=i
            for j -> i+1 to n:
               if arr[j]<arr[min]:
                    swap
min=i+1




"SELECTION SORT(SORTING ORDER)"


def selection_sort(arr):
    n=len(arr)
    for i in range(n):
        min_index=i
        for j in range(i+1, n):
            if arr[j]< arr[min_index]:
                min_index=j
        arr[i], arr[min_index]= arr[min_index], arr[i]
    return arr
size=int(input("Enter the number of elements:"))
arr=[]
print("Enter ", size, "elements")
for _ in range(size):
    num=int(input())
    arr.append(num)
result=selection_sort(arr)
print("Sorted array", result)






"SELECTION SORT(DESCENDING ORDER)"


def selection_sort(arr):
    n=len(arr)
    for i in range(n):
        min_index=i
        for j in range(i+1, n):
            if arr[j]> arr[min_index]:
                min_index=j
        arr[i], arr[min_index]= arr[min_index], arr[i]
    return arr
size=int(input("Enter the number of elements:"))
arr=[]
print("Enter ", size, "elements")
for _ in range(size):
    num=int(input())
    arr.append(num)
result=selection_sort(arr)
print("Sorted array", result)




''' "INSERTION SORT"
1. start from the second element(i=1)
2. previous index value element check
3. shift larger element one position to the right
4. insert the current element in the correct position
5. repeat until array sorted
for i -> to n-1:
       key=arr[i]
       j=i-1
       while j>=0 and arr[j]>key:
            arr[j+1]=arr[j]'''



"INSERTION SORT (WITH NUMBERS)"

def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j=i-1
        while j>=0 and arr[j]>key:
            arr[j+1]=arr[j]
            j-=1
        arr[j+1]=key
    return arr
size=int(input("Enter the number of elements:"))
arr=[]
print("Enter ", size, "elements")
for _ in range(size):
    num=int(input())
    arr.append(num)
result=insertion_sort(arr)
print("Sorted array", result)




"INSERTION SORT (WITH STRING)"

def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j=i-1
        while j>=0 and arr[j]>key:
            arr[j+1]=arr[j]
            j-=1
        arr[j+1]=key
    return arr
size=int(input("Enter the number of elements:"))
arr=[]
print("Enter ", size, "elements")
for _ in range(size):
    num=(input())
    arr.append(num)
result=insertion_sort(arr)
print("Sorted array", result)




