# 部分检查用代码

## 对向量的检查(部分用完删除了)
```py
from playLA.Matrix import Matrix
from playLA.Vector import Vector
if __name__=="__main__":
    vec = Vector([5,2])
    print(vec)
    print(len(vec))
    print("ved[0]={}, vec[1]={}".format(vec[0],vec[1]))

    vec2=Vector([3,1])
    print("{}+{}={}".format(vec,vec2,vec+vec2))
    print("{}-{}={}".format(vec, vec2, vec - vec2))
    print("{} * {} = {}".format(vec, 3, vec * 3))
    print("{}/{}={}".format(vec,3, vec / 3))
    print("{}*{}={}".format(3,vec,3 * vec ))
    zero2=Vector.zero(2)
    print("{}+{}={}".format(vec,zero2,vec+zero2))
    I=Matrix.identity(3)
    print(I)
        print("normalize {} is {}".format(vec, vec.normalize()))
    print(vec.normalize().norm())
    print("normalize {} is {}".format(vec2, vec2.normalize()))
    print(vec2.normalize().norm())
    try:
        zero2.normalize()
    except ZeroDivisionError:
        print("Cannot normalize zero vector {}.".format(zero2))
    print(vec.dot(vec2))
    vec3 = Vector([0, 0])
    print("{} == {}? {}".format(zero2, vec3, vec3 == zero2))
    print("{} == {}? {}".format(vec2, vec3, vec3 == vec2))
    print("{} != {}? {}".format(vec2, vec3, vec3 != vec2))
```

## 对矩阵的检查(部分用完删除了)
```py
from playLA.Matrix import Matrix
if __name__=="__main__":

    matrix=Matrix([[1,2],[3,4]])
    print(matrix)
    matrix2=Matrix([[5,6],[7,8]])
    print("mul:{}".format(matrix * matrix2))
    print("A.dot(B)={}".format(matrix.dot(matrix2)))
```
## 对矩阵的变换（翻转等）的检查
```py
import matplotlib.pyplot as plt
from playLA.Vector import Vector
from playLA.Matrix import Matrix
import math
if __name__=="__main__":

    points=[[0,0],[0,5],[3,5],[3,4],[1,4],
            [1,3],[2,3],[2,2],[1,2],[1,0]]
    x=[point[0] for point in points]
    y=[point[1] for point in points]
    plt.figure(figsize=(5,5))
    plt.xlim(-10,10)
    plt.ylim(-10,10)

    plt.plot(x,y)
    #plt.show()

    P=Matrix(points)
    #T=Matrix([[2,0],[0,1.5]])
    #T=Matrix([[1,0],[0,-1]])
    #T=Matrix([[-1,0],[0,1]])
    #T=Matrix([[-1,0],[0,-1]])
    #T=Matrix([[1,0.5],[0,1]])
    #T=Matrix([[1,0],[0.5,1]])
    theta = math.pi /3
    T=Matrix([[math.cos(theta),math.sin(theta)],[-math.sin(theta),math.cos(theta)]])

    P2=T.dot(P.T())
    plt.plot([P2.col_vector(i)[0] for i in range(P2.col_num())],
             [P2.col_vector(i)[1] for i in range(P2.col_num())])
    plt.show()
```    

## 对线性系统的检查
```py
from playLA.Matrix import Matrix
from playLA.Vector import Vector
from playLA.LinearSystem import LinearSystem

if __name__=="__main__":
    A = Matrix([[1, 2, 4], [3, 7, 2], [2, 3, 3]])
    b = Vector([7, -11, 1])
    ls = LinearSystem(A, b)
    ls.gauss_jordan_elimination()
    ls.fancy_print()
    print()
```   