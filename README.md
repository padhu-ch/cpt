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





''' perform insertion sort on strings based on length of the words'''

def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j=i-1
        while j>=0 and len(arr[j])>len(key):
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





def insertion_sort(arr):
    arr=list(arr)
    for i in range(1, len(arr)):
        key = arr[i]
        j=i-1
        while j>=0 and arr[j]>key:
            arr[j+1]=arr[j]
            j-=1
        arr[j+1]=key
    return ''.join(arr)
arr=input("enter")
result=insertion_sort(arr)
print("Sorted array", result)





'''algo:
1.start from the begining of the array/list
2.compare each pair to adjacent number
3.if latest element is greater than adjacent perfom swap
4.repeat the process till n-1
5.aftereach cycle/pass,largest unsorted element would be in correct pos
6. repeat pass till all the elements are sorted 


pseudo:
for i->0to n-1:
for j->0to n-i-2:
if a[j]>a[j+1]
swap(a[j],a[j+1])'''



def bubble_sort(arr):
    n=len(arr) 
    for i in range(n):
        for j in range(0,n-i-1):
            if arr[j]>arr[j+1]:
                arr[j],arr[j+1]=arr[j+1],arr[j]
size=int(input("enter"))
arr=[]
print("enter the elements:")
for _ in range(size):
    arr.append(int(input()))
print("Original list:",arr)
bubble_sort(arr)






non-comparison sort
1. no -ve numbers
2. no-long numbers
3.short confined numbers only ex: 0-100

algo:
1.find max min of array
2. min!<0 
3. create a count array to store frequency of numbers
4.modify the count array for each element to be store the sum of previous counts
                        
5. place the output array back to the original array 
pseudo code:
1. find the max in arr
2. create count(0-max)
                        3. for i->0 to n-1:
                        count [a[i]]+=1
4. for i->1 to max_al:
count[i]+=count[i-1]
create output arr[n]
5. for i->n-1 to 0:
output[count[a[i]]-1]=a[i]
count[a[i]]-=1
copy output to arr
time complexity=O(n+k)






'''COUNTSEARCH SORT'''

def csort(arr):
    if not arr:
        return []
    max_val=max(arr)
    count=[0]*(max_val+1)
    for num in arr:
        count[num]+=1
    for i in range(1,len(count)):
        count[i]+=count[i-1]
    output=[0]*len(arr)
    for num in reversed(arr):
        output[count[num]-1]=um
        count[num]-=1
    for i in range(len(arr)):
        arr[i]=output[i]
arr=[4,2,2,8,3,3,1]
print("Before:",arr)
csort(arr)
print("After:",arr)
csort(arr)





def csortString(s):
    count= [0]*26
    for char in s:
        count[ord(char)-ord('a')]+=1
    sorted_str=''
    for i in range(26):
        sorted_str+=chr(i+ord('a'))*count[i]
    return sorted_str
name=input("enter a single word:")
sorted_name=c
sortString(name)
print("Original string:", name)
print("Sorted string:", sorted_name)






"APPROACH"
Radix sort:
1. find the maximum number to determine number of digits
2. select 10^0, for digit position
3. increment digit position, w.r.t pass
4. maxnum//exp>0
  perform count sort based on current digit
  (num//exp)%10
   multiply exp by 10


"RADIX SORT"


def count_sort(arr, exp):
    n=len(arr)
    output= [0]*n
    count=[0]*10
    for i in range(n):
        index = (arr[i]//exp)%10
        count[index]+=1
    for i in range(1,10):
        count[i]+=count[i-1]
    i=n-1
    while i>=0:
        index=(arr[i]//exp)%10
        output[count[index]-1]=arr[i]
        count[index]-=1
        i-=1
    for i in range(n):
        arr[i]=output[i]
def radix_sort(arr):
    max_num=max(arr)
    exp=1
    while max_num // exp>0:
        count_sort(arr,exp)
        exp*=10
arr=[170,45,75,90,802,24,2,66]
print("before sort", arr)
radix_sort(arr)
print("after sort", arr)






''' pancake sort:
 1.high value
 2.high value flip
 3.total flip
 4.set high value
 
 alg:
 1.start complete array and decrease the size (n-1)
 2.for each size:
   a.find the index of max element
   b.flip the array with max element 
   c.flip the total array to the current size max -> move to the end of 
   the array
 3.repeat step1 ny n-2,n-3...
 for  n th reduced element perform step 2 until
 0 th index value respectively....'''





def flip(arr,k):
     return arr[:k+1][::-1]+arr[k+1:]
def pancake(arr):
    n=len(arr)
    for size in range(n,1,-1):
        max_index=arr.index(max(arr[:size]))
        print("Maximum index",max_index)
        if max_index!=size-1:
            if max_index!=0:
                arr=flip(arr,max_index)
                print(f"Flip at {max_index+1}: {arr}")
            arr=flip(arr,size-1)
            print(f" Flip at {size}: {arr}")
    return arr
nums=list(map(int,input("enter numbers with space:").split()))
sorted_nums=pancake(nums)
print("Sorted",sorted_nums)






"RPLUS"


with open("file1.txt","w") as f:
    f.write("vijay komarapu")
with open("file1.txt",'r+') as f:
    data=f.read()
    print("Previous:", data)
    new_data=data.replace("komarapu", "chandra")
    f.seek(0)
    f.write(new_data)
    f.truncate()
with open("file1.txt",'r') as f:
    print("Latest:", f.read())





sys.argv----------cmd line arg
sys.exit()
sys.stderr--------error msg
sys.version
sys.platform
sys.recursionlimit()
sys.stdout-------- output redirect











exception handling :
errors - logical errors / syntax
exceptions - synchronous and asnchronous
4/0 


1. Exception - for base classes
2. ArithmeticError - math errors
3. ZeroDivisionError - 4/0
4. StopIteration = next method or iterator not available/ condition not available
5. SystemExit - current os exit
6. StandardError = pre defined keyword
7. EOFError = I/O till the endof file
8. ImportError = file existing errors
9. KeyboardInterrupt - execution interrupt
10. NameError - 
11. ValueError -
12. IndexError -
13. TypeError -
14. IOError -
15. SyntaxError -
16. RuntimeError -
17. IndentationError -
18. AttributeError -
19. AssertionError -








try:
    -----------
    -----------
except ---------:





"PROGRAM"

try:
    num=int(input("enter numerator:"))
    num1=int(input("enter denominator:"))
    output = num/num1
    print("Result:",output)
except ZeroDivisionError:
    print("Cannot divide by zero....")





try:
    num=int(input("enter numerator:"))
    num1=int(input("enter denominator:"))
    output = num/num1
    print("Result:",output)
except ZeroDivisionError:
    print("Cannot divide by zero....")









import math
try:
    num = int(input("Enter a number:"))
    if num<0:
        raise ValueError("Negative number.....")
except ValueError:
    print("Enter Positive number only....")
else:
    print("SquareRoot:", round(math.sqrt(num),4))
   





'''delete operation by value'''
class Node:
    def __init__(self,data):
        self.data=data
        self.next=None
class LinkedList:
    def __init__(self):
        self.head=None
    def iae(self,data):
        newnode=Node(data)
        if not self.head:
            self.head=newnode
            return
        current=self.head
        while current.next:
            current=current.next
        current.next=newnode
    def deletevalue(self,key):
        current=self.head
        if not current:
            print("Empty LL")
            return
        if current.data==key:
            self.head=current.next
            print(f"{key} deleted from list")
            return
        prev=None
        while current and current.data!=key:
            prev=current
            current=current.next
        if not current:
            print(f"{key} not found in the LL")
            return
        prev.next=current.next
        print(f"{key} deleted from LL")
    def display(self):
        current=self.head
        if not current:
            print("LL-EMPTY")
            return
        while current:
            print(current.data,end="---")
            current=current.next
        print("None")
ll=LinkedList()
while True:
    print("\n LinkedList - insert at begin...")
    print("1. insert")
    print("2. display")
    print("3. delete by value")
    print("4. exit")
    choice=input("enter your choice:")
    if choice=='1':
        data=int(input("enter a value to insert"))
        ll.iae(data)
    elif choice=='2':
        ll.display() 
    elif choice=='3':
        key=int(input("enter the value,you want to delete:"))
        ll.deletevalue(key)
    elif choice=='4':
        print("Exit the operation.....")
        break
    else:
        print("enter only....1/2/3/4")



'''delete operation at beginning'''
class Node:
    def __init__(self,data):
        self.data=data
        self.next=None
class LinkedList:
    def __init__(self):
        self.head=None
    def iae(self,data):
        newnode=Node(data)
        if not self.head:
            self.head=newnode
            return
        current=self.head
        while current.next:
            current=current.next
        current.next=newnode
    def deletebegin(self):
        if self.head is None:
            print("Empty=LL")
        else:
            print("Deleted node from beginning:",self.head.data)
            self.head=self.head.next
    def display(self):
        current=self.head
        if not current:
            print("LL-EMPTY")
            return
        while current:
            print(current.data,end="---")
            current=current.next
        print("None")
ll=LinkedList()
while True:
    print("\n LinkedList - insert at begin...")
    print("1. insert")
    print("2. display")
    print("3. delete at begin")
    print("4. exit")
    choice=input("enter your choice:")
    if choice=='1':
        data=int(input("enter a value to insert"))
        ll.iae(data)
    elif choice=='2':
        ll.display() 
    elif choice=='3':
        #key=int(input("enter the value,you want to delete:"))
        ll.deletebegin()
    elif choice=='4':
        print("Exit the operation.....")
        break
    else:
        print("enter only....1/2/3/4")





'''delete operation at ending'''
class Node:
    def __init__(self,data):
        self.data=data
        self.next=None
class LinkedList:
    def __init__(self):
        self.head=None
    def iae(self,data):
        newnode=Node(data)
        if not self.head:
            self.head=newnode
            return
        current=self.head
        while current.next:
            current=current.next
        current.next=newnode
    def deleteend(self):
        if self.head is None:
            print("Empty=LL")
            return
        if self.head.next is None:
            print(f"Deleted last node:{self.head.data}")
            self.head=None
            return
        current=self.head
        while current.next.next:
            current=current.next
        print(f"Deleted last node:,{current.next.data}")        
        current.next=None
    def display(self):
        current=self.head
        if not current:
            print("LL-EMPTY")
            return
        while current:
            print(current.data,end="---")
            current=current.next
        print("None")
ll=LinkedList()
while True:
    print("\n LinkedList - insert at begin...")
    print("1. insert")
    print("2. display")
    print("3. delete at end")
    print("4. exit")
    choice=input("enter your choice:")
    if choice=='1':
        data=int(input("enter a value to insert"))
        ll.iae(data)
    elif choice=='2':
        ll.display() 
    elif choice=='3':
        #key=int(input("enter the value,you want to delete:"))
        ll.deleteend()
    elif choice=='4':
        print("Exit the operation.....")
        break
    else:
        print("enter only....1/2/3/4")


"ATM"


class Transaction:
    def __init__(self, transaction_type,amount):
        self.type=transaction_type
        self.amount=amount
        self.next=None
class TransactionHistory:
    def __init__(self):
        self.head=None
    def add_transaction(self,transaction_type,amount):
        nn=Transaction(transaction_type,amount)
        if not self.head:
            self.head=nn
        else:
            current=self.head
            while current.next:
                current=current.next
            current.next=nn
        print(f"{transaction_type} of Rs.{amount} recorded....")
    def show_history(self):
        if not self.head:
            print("No transaction found.....")
            return
        print("\n Transaction History:")
        current=self.head
        count=1
        while current:
            print(f"{count}, {current.type}- Rs{current.amount}")
            current=current.next
            count+=1
history=TransactionHistory()
while True:
    print("\n---------ATM Transaction Menu--------")
    print("1. Deposit")
    print("2. Withdraw")
    print("3. History")
    print("4. Exit")
    choice=input("Enter your choice:")
    if choice=='1':
        amount=float(input("Enter the amount to deposit:"))
        history.add_transaction("Deposit",amount)
    elif choice=='2':
        amount=float(input("Enter amount to withdraw:"))
        history.add_transaction("WithDraw",amount)
    elif choice=='3':
        history.show_history()
    elif choice=='4':
        print("End of transaction..... Exit!!!")
        break
    else:
        print("choose 1/2/3/4 only......." )       





class Node:
    def __init__(self, data):
        self.data=data
        self.next=None
class LinkedList:
    def __init__(self):
        self.head=None
    def insert_end(self, data):
        newnode=Node(data)
        if self.head is None:
            self.head=newnode
            return
        current=self.head
        while current.next:
            current=current.next
        current.next=newnode
    def reverse(self):
        prev=None
        current=self.head
        while current:
            nextnode=current.next
            current.next=prev
            prev=current
            current=nextnode
        self.head=prev
    def print_list(self):
        current=self.head
        while current:
            print(f"{current.data}-", end="")
            current=current.next
        print("null")
ll=LinkedList()
nodes=[11,22,33,44,55]
for val in nodes:
    ll.insert_end(val)
print("Original List:")
ll.print_list()
ll.reverse()
print("Reversed List:")
ll.print_list()




"DOUBLE LINKEDLIST"
"AT ENDING"


class Node:
    def __init__(self,data):
        self.data=data
        self.prev=None
        self.next=None
class DoublyLinkedList:
    def __init__(self):
        self.head=None
    def iae(self,data):
        newnode=Node(data)
        if self.head is None:
            self.head=newnode
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        temp.next=newnode
        newnode.prev=temp
    def display(self):
        temp=self.head
        print("double linked list:")
        while temp:
            print(temp.data,end="<-->")
            temp=temp.next
        print("None")
dll=DoublyLinkedList()
n=int(input("enter the number of elements to insert at end:"))
for i in range(n):
    val=int(input(f"Enter Element{i+1}:"))
    dll.iae(val)
dll.display()





"AT BEGINNING"

class Node:
    def __init__(self,data):
        self.data=data
        self.prev=None
        self.next=None
class DoublyLinkedList:
    def __init__(self):
        self.head=None
    def iab(self,data):
        newnode=Node(data)
        if self.head is None:
            self.head=newnode
        else:
            newnode.next=self.head
            self.head.prev=newnode
            self.head=newnode
    def display(self):
        temp=self.head
        print("double linked list:")
        while temp:
            print(temp.data,end="<-->")
            temp=temp.next
        print("None")
dll=DoublyLinkedList()
n=int(input("enter the number of elements to insert at end:"))
for i in range(n):
    val=int(input(f"Enter Element{i+1}:"))
    dll.iab(val)
dll.display()



"AT POSITION"



class Node:
    def __init__(self,data):
        self.data=data
        self.prev=None
        self.next=None
class DoublyLinkedList:
    def __init__(self):
        self.head=None
    def iap(self,data):
        newnode=Node(data)
        if pos<=0:
            print("Invalid position")
            return
        if pos==1:
            newnode.next=self.head
            if self.head:
                self.head.prev=newnode
            self.head=newnode
            return
        temp=self.head
        for _ i range(pos-2):
            if temp is None:
                print("Position off range")
                return
            temp=temp.next
        if temp is None:
            print("No elements.....")
            return
        newnode.next=temp.next
        newnode.prev=temp
        if temp.next:
            temp.next.prev=newnode
        temp.next=newnode
    def display(self):
        temp=self.head
        print("double linked list:")
        while temp:
            print(temp.data,end="<-->")
            temp=temp.next
        print("None")
dll=DoublyLinkedList()
dll.iap(1,100)
n=int(input("enter the number of elements to insert at end:"))
for i in range(n):
    val=int(input(f"Enter Element{i+1}:"))
    pos=int(input(f"enter the position to insert{val}"))
    dll.iab(pos,val)
dll.display()



"BACKTRAVERSE"

# at the backtraverse
class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iae(self,data):
        newnode=Node(data)
        if self.head is None:
            self.head=newnode
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        temp.next=newnode
        newnode.prev=temp
    def backtraverse(self):
        print("values for traversing backward...")
        temp=self.head
        if not temp:
            print("Empty List")
            return
        while temp.next:
            temp=temp.next
        while temp:
            print(temp.data, end='<--->')
            temp=temp.prev
        print("None")
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")
dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iae(val)
dll.display()
dll.backtraverse()




# at the insertion at beginning and backtraverse  


class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iab(self,data):
        newnode=Node(data)
        newnode.next=self.head
        if self.head:
            self.head.prev=newnode
        self.head=newnode
    def backtraverse(self):
        print("values for traversing backward...")
        temp=self.head
        if not temp:
            print("Empty List")
            return
        while temp.next:
            temp=temp.next
        while temp:
            print(temp.data, end='<--->')
            temp=temp.prev
        print("None")
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")
dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iab(val)
dll.display()
dll.backtraverse()



delete operation DLL:
1. delete at begin / insert at begin
2. delete at begin / insert at end
3. delete at end / insert at end
4. delete at end / insert at begin


"delete at begin / insert at begin"



class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iab(self,data):
        newnode=Node(data)
        newnode.next=self.head
        if self.head:
            self.head.prev=newnode
        self.head=newnode
    def dab(self):
        if not self.head:
            print("Can't perform delete in an empty list...")
        print(f" Deleted: {self.head.data}")
        self.head=self.head.next
        if self.head:
            self.head.prev=None
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")

dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iab(val)
dll.display()
d=int(input("\n how many times you want to perform delete operation:"))
for _ in range(d):
    dll.dab()
    dll.display()




"delete at begin / insert at end"


class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iab(self,data):
        newnode=Node(data)
        newnode.next=self.head
        if self.head:
            self.head.prev=newnode
        self.head=newnode
    def dae(self):
        if self.head is None:
            print("Can't perform delete in an empty list...")
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        print(f" Deleted: {temp.data}")
        if temp.prev:
            temp.prev.next=None
        else:
            self.head=None        
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")

dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iab(val)
dll.display()
d=int(input("\n how many times you want to perform delete operation:"))
for _ in range(d):
    dll.dae()
    dll.display()



"delete at end / insert at end"

class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iae(self,data):
        newnode=Node(data)
        if not self.head:
            self.head=newnode
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        temp.next=newnode
        newnode.prev=temp     
    def dae(self):
        if self.head is None:
            print("Can't perform delete in an empty list...")
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        print(f" Deleted: {temp.data}")
        if temp.prev:
            temp.prev.next=None
        else:
            self.head=None      
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")

dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iae(val)
dll.display()
d=int(input("\n how many times you want to perform delete operation:"))
for _ in range(d):
    dll.dae()
    dll.display()



 "delete at end / insert at begin"



class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iab(self,data):
        newnode=Node(data)
        if not self.head:
            self.head=newnode
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        temp.next=newnode
        newnode.prev=temp                                                                                                
    def dae(self):
        if self.head is None:
            print("Can't perform delete in an empty list...")
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        print(f" Deleted: {temp.data}")
        if temp.prev:
            temp.prev.next=None
        else:
            self.head=None    
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")

dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iab(val)
dll.display()
d=int(input("\n how many times you want to perform delete operation:"))
for _ in range(d):
    dll.dae()
    dll.display()







# insertion at end deletion by value
class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iae(self,data):
        newnode=Node(data)
        if not self.head:
            self.head=newnode
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        temp.next=newnode
        newnode.prev=temp                                                                                                
    def dbv(self,value):
        temp=self.head
        while temp:
            if temp.data==value:
                print(f"Deleted: {temp.data}")
                if temp.prev:
                    temp.prev.next=temp.next
                else:
                    self.head=temp.next
                if temp.next:
                    temp.next.prev=temp.prev
                return
            temp=temp.next
        print(f"{value} not found in the list:")    
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")

dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iae(val)
dll.display()
d=int(input("\n how many times you want to perform delete operation:"))
for _ in range(d):
    val=int(input("enter value to delete:"))
    dll.dbv(val)
    dll.display()




code check the duplicates in a DLL and print the count of frequency
input = 6
10
20
30
20
10
40
output:
DLL
10<-->20<-->30<-->20<-->10<-->40
duplicate values in DLL:
10 appears 2 times
20 appears 2 times



class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None
class Doublylinkedlist:
    def __init__(self):
        self.head = None
    def iae(self, data):  
        newnode = Node(data)
        if not self.head:
            self.head = newnode
            return
        temp = self.head
        while temp.next:
            temp = temp.next
        temp.next = newnode
        newnode.prev = temp                                 
    def dbv(self, value): 
        temp = self.head
        while temp:
            if temp.data == value:
                print(f"Deleted: {temp.data}")
                if temp.prev:
                    temp.prev.next = temp.next
                else:
                    self.head = temp.next
                if temp.next:
                    temp.next.prev = temp.prev
                return
            temp = temp.next
        print(f"{value} not found in the list.")
    def display(self):
        temp = self.head
        print("Doubly linked list:")
        while temp:
            print(temp.data, end="<->")
            temp = temp.next
        print("None")
    def count_duplicates(self):
        freq = {}
        temp = self.head
        while temp:
            freq[temp.data] = freq.get(temp.data, 0) + 1
            temp = temp.next
        print("\nFrequency of elements:")
        for key, count in freq.items():
            print(f"{key} : {count}")
        print("\nDuplicates:")
        for key, count in freq.items():
            if count > 1:
                print(f"{key} appears {count} times")
dll = Doublylinkedlist()
n = int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val = int(input(f"Enter element {i+1}: "))
    dll.iae(val)
dll.display()
dll.count_duplicates()
d = int(input("\nHow many times you want to perform delete operation: "))
for _ in range(d):
    val = int(input("Enter value to delete: "))
    dll.dbv(val)
    dll.display()
    dll.count_duplicates()  




"SNAKE GAME"

import pygame
import random
import sys
pygame.init()
height = 500
width = 700 
block_size=20
screen=pygame.display.set_mode((width,height))
pygame.display.set_caption("🐍 Snake Game")
BLACK=(0,0,0)
GREEN=(0,255,0)
RED=(255,0,0)
WHITE=(255,255,255)

# SPEED OF SNAKE PER FPS
clock=pygame.time.Clock()
font=pygame.font.SysFont(None,36)

# SNAKE AND FOOD
def draw_snake(snake_list):
    for block in snake_list:
        pygame.draw.rect(screen,GREEN,(*block,block_size,block_size))

# FOOD POSITION
def draw_food(pos):
    pygame.draw.rect(screen,RED,(*pos,block_size,block_size))
def message(text,color):
    msg=font.render(text,True,color)
    screen.blit(msg, [width//4, height//2])
    
def game_loop():
    snake=[(100,100)]
    direction="RIGHT"
    change=direction
    food=[random.randrange(0,width,block_size),random.randrange(0,height,block_size)]
    score=0
    while True:
        for event in pygame.event.get():
            if event.type==pygame.QUIT:
                pygame.quit()
                sys.exit()
            elif event.type==pygame.KEYDOWN:
                if event.key==pygame.K_UP and direction !="DOWN":
                    change="UP"
                elif event.key==pygame.K_DOWN and direction !="UP":
                    change="DOWN"
                elif event.key==pygame.K_LEFT and direction !="RIGHT":
                    change="LEFT"
                elif event.key==pygame.K_RIGHT and direction !="LEFT":
                    change="RIGHT"
        direction=change
        x,y=snake[0]
        if direction=="UP":
            y-=block_size
        elif direction=="DOWN":
            y+=block_size
        elif direction=="LEFT":
            x-=block_size
        elif direction=="RIGHT":
            x+=block_size
        head=(x,y)
        if(x<0 or x>=width or y<0 or y>=height or head in snake):
            screen.fill(BLACK)
            message("Game Over! Score :" +str(score), RED)
            pygame.display.update()
            pygame.time.wait(1000)
            return
        snake.insert(0,head)
        if head==tuple(food):
            score+=1
            food=[random.randrange(0,width,block_size),random.randrange(0,height,block_size)]
        else:
            snake.pop()
        screen.fill(BLACK)
        draw_snake(snake)
        draw_food(food)
        score_text=font.render("Score:"+str(score),True,WHITE)
        screen.blit(score_text, [10,10])
        pygame.display.update()
        clock.tick(10)
game_loop()

    
    



