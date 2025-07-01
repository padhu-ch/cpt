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






