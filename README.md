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











