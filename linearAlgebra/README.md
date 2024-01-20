# Linear algebra

## Conceptual map

- `V`: Vectors & matrices
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

- `M`: Matrices<br> _... extends from_ `V.M`
    - `M.base`: General definition of matrix & specific interpretations
    - `M.Op`: Matrix operations & their meaning w.r.t. vectors
        - Matrix addition (_ordered sequence of multiple vector additions_)
        - Scalar product (_ordered sequence of the scaling of multiple vectors_)
        - Matrix multiplication (_ordered sequence of linear combinations of multiple vectors_)
    - `LT~M`: Linear transformations as matrices
        - Representing a LT as a matrix
        - Obtaining a vector's LT with matrix multiplication
        - Relating function composition to composition of LT's to composition of matrices
    - `M.Det`: Determinant
        - `M.Det~LT`: Determinant as a number related to a LT<br> _More specifically, it gives the scale & orientation of the LT_
        - Calculation & justification of the calculation method
        - Key results on determinants & their validation
            - $\det(A B) = det(A) det(B)$
