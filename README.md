# Task2 to NapoleonIT
# QuickSort on Python 
import random
def Reverse(A,L,R):
    l = R - L + 1
    B=[]
    for i in range(l):
        B.append(A[R-i])
    for i in range(l):
        A[L+i]=B[i]

def QuickSort(A, L, R,D=0):
    if L >= R:
        return
    i, j = L, R
    base = A[random.randint(L, R)]

    while i <= j:
        while A[i] < base:
            i += 1
        while A[j] > base:
            j -= 1
        if i <= j:
            A[i], A[j] = A[j], A[i]
            i, j = i + 1, j - 1
    QuickSort(A, L, j)
    QuickSort(A, i, R)



def divide(A,N):
    j=N-1; i=0
    while i<j:
        if A[i]%2 != 0:
            if A[j]%2 == 0:
                t=A[i]; A[i]=A[j]; A[j]=t
            else:
                j-=1
        else:
            i+=1
    return(i)

#Main
A=[]
N=int(input("Введите длину массива "))
s=input("Введите все элементы массива через пробел ")
A=s.split(' ')
for i in range(N):
    A[i]=int(A[i])
divide(A,N)
N=len(A)
m=divide(A,N)
QuickSort(A,0,m-1)
QuickSort(A,m,N-1,1)
Reverse(A,m,N-1)
print(A)
