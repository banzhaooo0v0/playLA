# numpy的使用

## 用numpy实现向量和计算
```py
import numpy as np

if __name__ == "__main__":
    print(np.__version__)
    lst = [1, 2, 3]
    lst[0] = "Linear Algebra"
    print(lst)
    vec = np.array([1, 2, 3])
    print(vec)
    print(np.zeros(5))
    print(np.ones(5))
    print(np.full(5, 666))
    print(vec)
    print("size =", vec.size)
    print("size =", len(vec))
    print(vec[0])
    print(vec[-1])
    print(vec[0: 2])
    print(type(vec[0: 2]))
    vec2 = np.array([4, 5, 6])
    print("{} + {} = {}".format(vec, vec2, vec + vec2))
    print("{} - {} = {}".format(vec, vec2, vec - vec2))
    print("{} * {} = {}".format(2, vec, 2 * vec))
    print("{} * {} = {}".format(vec, vec2, vec * vec2))
    print("{}.dot({}) = {}".format(vec, vec2, vec.dot(vec2)))
    print(np.linalg.norm(vec))
    print(vec / np.linalg.norm(vec))
    print(np.linalg.norm(vec / np.linalg.norm(vec)))

    # zero3 = np.zeros(3)
    # print(zero3 / np.linalg.norm(zero3))
```

## 用numpy实现矩阵及其变化和计算
```py
import numpy as np

if __name__ == "__main__":
    A = np.array([[1, 2], [3, 4]])
    print(A)
    print(A.shape)
    print(A.T)
    print(A[1, 1])
    print(A[0])
    print(A[:, 0])
    print(A[1, :])
    B = np.array([[5, 6], [7, 8]])
    print(A + B)
    print(A - B)
    print(10 * A)
    print(A * 10)
    print(A * B)
    print(A.dot(B))
    p = np.array([10, 100])
    I = np.identity(2)
    print(I)
    print(A.dot(I))
    print(I.dot(A))
    invA = np.linalg.inv(A)
    print(invA)
    print(invA.dot(A))
    # [[1.0000000e+00 4.4408921e-16]
    #  [0.0000000e+00 1.0000000e+00]]
    print(A.dot(invA))
    # [[1.00000000e+00 1.11022302e-16]
    #  [0.00000000e+00 1.00000000e+00]]
```