# some_algorithms
# Jumping frog:
  def frog_jump (a):
    b=[]
    c=[]
    d=[]
    no_stone = 0
    for i in (0, len(a)):
      if a[i]==1: # there is a stone
         for j in (0, len(b)):
           b.append(i)
      elif a[i]==0: # there is no stone 
         no_stone=no_stone+1   # number of empty units ( no stone in it)
    for j in (0, len(b)):
      x= b[j+1]-b[j]
      c.append(x)
    for k in (0, len(c)):
      while b[j]==c[k]:
        y= b[j]+1
        z= b[j]-1
        d.append(z)
        d.append(c[j])
        d.append(y)
        if d[k-1]==d[k-2] | d[k-1]==d[k-3] | d[k-1]==d[k-4]:
          return ("true")
        return("false")
# Max window :
  def max_window(a,k):
    b=[]
    c=[]
    if k>len(a):
      return ("impossible!!!")
    for i in (0, len(a)):
      c=a[i:i+1]
      for j in (i,i+k):
        w_max=max(c)
        b.append(w_max)
      return b
# Max window 2:
  def max_element_of(A,m,n):                  #Finding the max value of A from element m to n
      max=A[m]
      for i in range(m,n):
          if A[i]>max:
              max=A[i]
      return max
  def max_ele_of_window(A,k):                 #Scan all windows
      T=[]
      for i in range (0,len(A)-k+1):
          T.append(max_element_of(A, i, i+k))
      return T

  #testbench
  T = [1,3,-1,-3,5,3,6,7]
  k = 3
  print(max_ele_of_window(T, k))
  T = [1,-1]
  k = 1
  print(max_ele_of_window(T, k))

# matrix of queens:
  def printSolution(N):
      for i in range(N):
          for j in range(N):
              print (chess_board[i][j],end=' ')
          print()
  #checking diagonal/row/colomn
  def is_it_wanted(chess_board,row,clm): #checking colomn only from one direction
    for i in range(clm):
      if chess_board[row][1]==1:
        return False
    for i,j in  zip(range(row,-1,-1), range(clm,-1,-1)): 
        #checking diagonal only from 
        #direction up-->down
      if chess_board[i][j]==1:
        return False
    for i,j in zip(range(row,N,-1), range(clm,-1,-1)): 
       #checking diagonal only from 
       #direction down-->up
      if chess_board[i][j]==1:
        return False
    return True

  def placed_or_not(chess_board, col):
      if clm >= N:
          return True
      for i in range(N):
         if is_it_wanted(chess_board, i, clm)== true :
              board[i][col] = 1 # placing the queen
              # placing rest of the queens
              if placed_or_not(board, col + 1) == True:
                  return True
              board[i][col] = 0
      # if the queen cannot placed anywhere
      return False
  def solved():
      if placed_or_not(chess_board, 0) == False:
          print ("Solution does not exist")
          return False
      return True

  # driver program to test above function
  solved()

