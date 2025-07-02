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
    
    






