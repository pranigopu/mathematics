# Linear algebra

## Conceptual map

- `V`: Vectors
    - `V.base`: General definition of vector & specific interpretations
        - Physics context (_relative change in position_)
        - Computer science & data science context (_ordered list of values_)
        - Mathematics, i.e. generalised context (_generalises all other contexts_)
        - Relation between geometric & numeric interpretations
    - `V.Op`: Vector operations & their meaning w.r.t. geometric interpretation<br> **NOTE**: _Full clarity of some topics requires understanding linear transformations_
        - Vector addition (_obtaining the resultant vector of a series of vector movements_)
        - Scalar product (_scaling a vector, i.e. changing its magnitude while maintaining direction_)
        - Dot product & its meaning (_discussed later_)
        - Vector product & its meaning (_discussed later_)
    - `V.Sp`: Span of a set of vectors
    - `V.M`: Matrices as vectors of vectors
    - `V.VS`: Vector spaces
        - `V.VS.Dim`: Dimensions of a vector space (_in every interpretation, i.e. every context_)
        - `V.VS.B`: Basis of a vector space
        - `LT~V.VS`: Linear transformations as transformations of vector spaces
            - Representing a LT as a transformation of basis vectors
            - Reducing the dimensionality of a vector space through LT

Matrices are deeply tied to linear transformations, so always consider matrix-related topics in the context of LT...

- `M`: Matrices<br> _... extends from_ `V.M`
    - `M.base`: General definition of matrix & specific interpretations
    - `M.Op`: Matrix operations & their meaning w.r.t. vectors
        - Matrix addition (_ordered sequence of multiple vector additions_)
        - Scalar product (_ordered sequence of the scaling of multiple vectors_)
        - Matrix multiplication (_ordered sequence of linear combinations of multiple vectors_)
    - `LT~M`: Linear transformations as matrices
        - Representing a LT as a matrix
        - Linearly transforming a vector with matrix multiplication
        - Relating function composition to composition of LT's to composition of matrices
    - `M.Det`: Determinant
        - `M.Det~LT`: Determinant as a number related to a LT<br> _More specifically, it gives the scale & orientation of the LT_
            - _How and why are scale & orientation represented the way they are?_
            - _What does zero determinant mean?_
        - Calculation & justification of the calculation method
        - Key results on determinants & their validation
            - $\det(A B) = \det(A) \det(B)$
    - `M.Inv`: Inverse of a matrix
        - `M.Det~LT`: Inverse of a matrix as inverse (i.e. reversal) of a LT<br> _LT is a function; think in terms of inverse of functions_
        - Relation between inverse & identity transformations
        - Relation between determinant & inverse
    - `M.SoE`: Systems of equations as matrices
        - `M.SoE~LT`: SoE as finding the preimage of a vector w.r.t. a LT<br> _Looking for the vector(s) that is mapped by the LT to the given vector_
        - Zero determinant & possible solutions given coefficient <br> _Connect with LT_
        - Specifying zero determinant cases using _rank_ <br> _Connect with LT_
        - Obtaining the solution of a SoE using the inverse of the coefficient matrix

Generalising linear transformation topics...

- `LT`: Linear transformation (general concepts)<br> **NOTE**: We shall take for granted that LT's are represented as matrices
    - **REFERENCE FOR INTUITION**: [Inverse matrices, column space and null space | Chapter 7, Essence of linear algebra](https://www.youtube.com/watch?v=uQhTuRlWMxw)
    - `LT.base`: Representing LT as a matrix
    - `LT.Rank`: Rank of a matrix a.k.a. rank of a LT
    - `LT.CS`: Column space of a matrix<br> _Essentially, the span of the transformed basis vectors, i.e. the columns_
        - `LT.Rank~LT.CS`: _Rank is the number of dimensions in the column space_
        - "Full rank" matrix $\implies$ Rank equals the number of columns $\implies$ Maximum dimensions for the column space
    - `LT.DimRed`: Dimensionality reduction of vector space with LT
    - `LT.NS`: Nullspace of a matrix a.k.a. nullspace of a LT<br> _... related to_ `LT.DimRed`
        - _The set of vectors that get mapped by the LT to a null vector, i.e. the origin_
        - _The set of all solution to a homogenous system of equations represented by the matrix_
