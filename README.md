# Determinant-of-Matrix

#Initialsing the matrix
n = int(input('Enter the dimension of the matrix:'))
Matrix = []
for i in range(n):
    R=[]
    for j in range(n):
        index = int(input('Enter value:'))
        R.append(index)
    Matrix.append(R)

def Determinant(M):
    det=0
    if(len(M)==1):
        return M[0][0] #return the value itself if dimension of matrix is 1
    else:
        for i in range(len(M)):
            L=[]
            for j in range(i): #appending all rows before ith row
                L.append(M[j][1:]) #[1:] as we do not want 1st column
            for k in range(i+1,len(M)): #appending all rows after ith row
                L.append(M[k][1:])
                #L is the minor of ith row 1st column
            # Now updating the determinant
            det += M[i][0]*(-1)**i*Determinant(L)
        return det

#printing matrix in usual form
for i in range(n):
    for j in range(n-1):
        print(Matrix[i][j], end=' ')
    print(Matrix[i][n-1])

print('Determinant of matrix is',Determinant(Matrix))
