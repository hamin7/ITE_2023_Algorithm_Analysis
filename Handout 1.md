
Exercise 1.1
Design a traffic light for the following intersection according to the method presented in the first lecture. (Table of incompatible turns, graph showing incompatible turns, graph colouring) Describe the structure of the resulting traffic light system in few words.


Exercise 1.2
Illustrate the operation of merge sort and insertion sort on the array:
A = [3, 41, 52, 26, 38, 57, 9, 49]


Exercise 1.3
Give a description of the Insertion-Sort algorithm in Pseudocode, so that some given sequence of number is sorted in decreasing order instead of increasing order.


Exercise 1.4
Consider the following list of numbers. Your job is to erase as few of those numbers as possible such that the remaining numbers appear in increasing order. For example, erasing everything except the first two numbers leaves an increasing sequence; erasing everything except for first, third, sixth, ad eighth numbers, does the same (but fewer numbers are erased).
9 44 32 12 7 42 34 92 35 37 41 8 20 27 83 64 61 28 39 93 29 17 13 14 55
21 66 72 23 73 99 1 2 88 77 3 65 83 84 62 5 11 74 68 76 78 67 75 69 70 22
71 24 25 26 

list = [9, 44, 32, 12, 7, 42, 34, 92, 35 ,37, 41, 8, 20, 27, 83, 64, 61, 28, 39,  
    93, 29, 17, 13, 14, 55, 21, 66, 72, 23, 73, 99, 1, 2, 88, 77, 3, 65, 83,
    84, 62, 5, 11, 74, 68, 76, 78, 67, 75, 69, 70, 22, 71, 24, 25, 26]
~~~
# 리스트의 모든 요소를 검사하여, 해당 요소가 존재하려면 없어져야하는 수에 패널티를 부과한다. 
# 예를 들 어 저 리스트에서 32( list[2] )가 남으려면 32 왼쪽의 32보다 큰 수들과 
# 32 오른쪽의 32보다 작은 수들은 패널티를 받게 된다.
def deleting(list):
  list_value = {x: 0 for x in list}
   
  for i in range(len(list)):
    if i==0:
      for j in range(2, len(list)):
        if list[j]<list[i]:
          list_value[list[j]] = list_value[list[j]] - 1
    elif i>0:
      for j in range(0, i):
        if list[j]>list[i]:
          list_value[list[j]] = list_value[list[j]] - 1
      for j in range(i+1, len(list)):
        if list[j]<list[i]:
          list_value[list[j]] = list_value[list[j]] - 1

# 패널티를 가장 많이 받은 수를 판별하기 위해 
# 인덱스 key 변수와 받은 패널티를 저장하는 mini 변수를 선언한다.
  key = 0
  mini = -1
     
  for i in range(len(list)):
    if list_value[list[i]] <= mini :
      key = i
      mini = list_value[list[i]]

# 패널티를 가장 많이 받은 수, 즉 다른 수들에게 영향력을 크게 주는 수를 삭제한다.
  del(list[key])

# 리스트가 오름차순이 될 때까지 삭제를 반복한다. 
while True:
  deleting(list)
  cnt = 0
  for i in range(len(list)-1):
    if list[i+1]<list[i]:
      cnt = cnt + 1
  if cnt == 0:
    break
~~~
