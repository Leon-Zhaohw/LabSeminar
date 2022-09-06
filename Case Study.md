## ![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\cover.png)

## Case Study

### Problem Description

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\problemDes.png)

---

The Governing Equation is

$$
\nabla \cdot (\rho U \phi) = \nabla \cdot (\Gamma \nabla \phi)
$$

$$
\sum (\rho U \phi)_f \cdot S_f  = \sum (\Gamma \nabla \phi)_f \cdot S_f 
$$

for e surface

$$
(\rho u A \phi)_e = (\Gamma A \frac{d\phi}{dx})_e \tag{1}
$$

for w surface

$$
(\rho u A \phi)_w = (\Gamma A \frac{d\phi}{dx})_w \tag{2}
$$

Eqn (1) - Eqn(2)

$$
(\rho u A \phi)_e - (\rho u A \phi)_w = 
(\Gamma A \frac{d\phi}{dx})_e - (\Gamma A \frac{d\phi}{dx})_w \tag{3}
$$

let $F =\rho u ,D = Γ/\delta x$ 

$$
F_e \phi_e - F_w \phi_w = 
D_e (\phi_E - \phi_P) - D_w (\phi_P - \phi_W) \tag{4}
$$

consider Central Difference 

$$
\phi_e = \frac{(\phi_P + \phi_E)}{2} \\

\phi_e = \frac{(\phi_W + \phi_P)}{2}
$$

Eqn (4) becomes

$$
\frac{F_e}{2} (\phi_P + \phi_E) - \frac{F_w}{2} (\phi_W + \phi_P) = 
D_e (\phi_E - \phi_P) - D_w (\phi_P - \phi_W) \tag{5}
$$

Rearrange Eqn (5)

$$
[(D_w - \frac{F_w}{2}) + (D_e + \frac{F_e}{2})] \phi_P = 
(D_w + \frac{F_w}{2}) \phi_W +( D_e + \frac{F_e}{2})\phi_E \tag{6}
$$

Consider continuity Eqn

$$
\frac{d(\rho u)}{dx} = 0  \ \Rightarrow \ [F_e - F_w = 0]
$$

Eqn(6) becomes

$$
[(D_w - \frac{F_w}{2}) + (D_e + \frac{F_e}{2})+ ( F_e - F_w )] \phi_P 
\\= (D_w + \frac{F_w}{2}) \phi_W +( D_e - \frac{F_e}{2})\phi_E \tag{7}
$$

let

$$
(D_w - \frac{F_w}{2}) + (D_e + \frac{F_e}{2})+ ( F_e - F_w ) = a_P \\
(D_w + \frac{F_w}{2}) = a_W \\
(D_e - \frac{F_e}{2}) = a_E
$$

Eqn (7) can be written

$$
a_P \phi_P = a_W \phi_W + a_E \phi_E
$$

---

### Solution

The method of solution is demonstrated using the simple grid shown in Figure 5.3. The domain has been divided into five control volumes giving $\delta x = 0.2$ m. Note that $F = \rho u, D = Γ/\delta x, Fe = Fw = F$ and $De = Dw = D$ everywhere. The boundaries are denoted by A and B.

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\fig5_3.png)

#### For node 2, 3, 4

$$
[(D_w - \frac{F_w}{2}) + (D_e + \frac{F_e}{2})+ ( F_e - F_w )] \phi_P 
\\= (D_w + \frac{F_w}{2}) \phi_W +( D_e - \frac{F_e}{2})\phi_E
$$

rearrange the Eqn

$$
[(D - \frac{F}{2}) + (D + \frac{F}{2})+ ( F - F )] \phi_P 
\\= (D + \frac{F}{2}) \phi_W +( D - \frac{F}{2}) \phi_E
$$

 ==>

$$
2D \phi_P = (D + \frac{F}{2}) \phi_W +( D - \frac{F}{2}) \phi_E
$$

#### For node 1

$$
\frac{F_e}{2} (\phi_P + \phi_E) - F_A \phi_A  = 
D_e (\phi_E - \phi_P) - 2D_w (\phi_P - \phi_A) 
$$

$$
[(2D_w ) + (D_e + \frac{F_e}{2})+ ( F_e - F_w )] \phi_P 
=  ( D_e - \frac{F_e}{2})\phi_E +F_A\phi_A +(2D_w ) \phi_A
$$

$$
[(2D_w ) + (D_e + \frac{F_e}{2})+ ( F_e - F_w )] \phi_P 
=  ( D_e - \frac{F_e}{2})\phi_E + (2D_w + F_A) \phi_A
$$

#### For node 5

$$
F_B\phi_B - \frac{F_w}{2} (\phi_W + \phi_P) = 
2D_e (\phi_B - \phi_P) - D_w (\phi_P - \phi_W) 
$$

$$
[(D_w - \frac{F_w}{2}) + (2D_e )+ ( F_e - F_w )] \phi_P 
=  ( D_w + \frac{F_w}{2})\phi_E - F_B\phi_B +(2D_e ) \phi_B
$$

$$
[(D_w - \frac{F_w}{2}) + (2D_e )+ ( F_e - F_w )] \phi_P 
=  ( D_w + \frac{F_w}{2})\phi_E + (2D_e -F_B ) \phi_B
$$

---

| Node  | $a_W$   | $a_E$   | $S_P$     | $S_u$          | a_P           |
| ----- | ------- | ------- | --------- | -------------- | ------------- |
| 1     | 0       | $D-F/2$ | $-(2D+F)$ | $(2D+F)\phi_A$ | $a_W+a_E-S_P$ |
| 2,3,4 | $D+F/2$ | $D-F/2$ | 0         | 0              | ..            |
| 5     | $D+F/2$ | 0       | $-(2D+F)$ | $(2D-F)\phi_B$ | ..            |

$u = 0.1 m/s: F = \rho u = 0.1, D = \Gamma /\delta x = 0.1/0.2 = 0.5$

| Node | $a_W$ | $a_E$ | $S_P$ | $S_u$       | a_P  |
| ---- | ----- | ----- | ----- | ----------- | ---- |
| 1    | 0     | 0.45  | -1.1  | 1.1$\phi_A$ | 1.55 |
| 2    | 0.55  | 0.45  | 0     | 0           | 1    |
| 3    | 0.55  | 0.45  | 0     | 0           | 1    |
| 4    | 0.55  | 0.45  | 0     | 0           | 1    |
| 5    | 0.55  | 0     | -0.9  | 0.9$\phi_B$ | 1.45 |

Ax=b becomes

$$
\left[
\begin{array}{ccccc}
  1.55 & −0.45 &  0.00 &  0.00 &  0.00 \\
  −0.55  & 1.00  & −0.45  & 0.00  & 0.00 \\
   0.00  &  −0.55 &  1.00 &  −0.45 &  0 \\
   0.00 & 0.00 & −0.55 &  1.00 &  −0.45 \\
   0.00 & 0.00 & 0.00 & −0.55 & 1.45 
\end{array}
\right]
=
\left[
\begin{array}{c}
    \phi_1  \\
    \phi_2  \\
    \phi_3  \\
    \phi_4  \\
    \phi_5 
\end{array}
\right]
\left[
\begin{array}{c}
    1 \\ 
    0 \\
    0 \\
    0 \\
    0 
\end{array}
\right]

$$

$$
\left[
\begin{array}{c}
    \phi_1  \\
    \phi_2  \\
    \phi_3  \\
    \phi_4  \\
    \phi_5 
\end{array}
\right]

=

\left[
\begin{array}{c}
    0.9421  \\
    0.8006  \\
    0.6276  \\
    0.4163  \\
    0.1579 
\end{array}
\right]
$$

---

### Solve in OpenFOAM

#### Pre-processing

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\mesh.png)

#### Solving

Solver name : laplacianFoam

```cpp
#include "fvCFD.H"
#include "fvOptions.H"
#include "simpleControl.H"

// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

int main(int argc, char *argv[])
{
    argList::addNote
    (
        "Laplace equation solver for a scalar quantity."
    );

    #include "postProcess.H"

    #include "addCheckCaseOptions.H"
    #include "setRootCaseLists.H"
    #include "createTime.H"
    #include "createMesh.H"

    simpleControl simple(mesh);

    #include "createFields.H"

    // * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

    Info<< "\nCalculating temperature distribution\n" << endl;

    while (simple.loop())
    {
        Info<< "Time = " << runTime.timeName() << nl << endl;

        while (simple.correctNonOrthogonal())
        {
            fvScalarMatrix TEqn
            (
                fvm::ddt(T) - fvm::laplacian(DT, T)
             ==
                fvOptions(T)
            );

          Info<< "diag():            " << TEqn.diag() << endl;
          Info<< "upper():           " << TEqn.upper() << endl;
          Info<< "lower():           " << TEqn.lower() << endl;
          Info<< "source():          " << TEqn.source() << endl;
          Info<< "upperAddr():       " << TEqn.lduAddr().upperAddr() << endl;
          Info<< "lowerAddr():       " << TEqn.lduAddr().lowerAddr() << endl;
          Info<< "internalCoeffs():  " << TEqn.internalCoeffs() << endl;
          Info<< "boundaryCoeffs():  " << TEqn.boundaryCoeffs() << endl;
          Info<< "D():               " << TEqn.D() << endl;

            fvOptions.constrain(TEqn);
            TEqn.solve();
            fvOptions.correct(T);


        }

        #include "write.H"

        runTime.printExecutionTime(Info);
    }

    Info<< "End\n" << endl;

    return 0;
```

Boundary Condition

```cpp
FoamFile
{
    version     2.0;
    format      ascii;
    class       volScalarField;
    object      T;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

dimensions      [0 0 0 1 0 0 0];

internalField   uniform 1;
boundaryField
{
    inlet
    {
        type            fixedValue;
        value           uniform 1;
    }

    outlet
    {
        type            fixedValue;
        value           uniform 0;
    }
}
```

```cpp
FoamFile
{
    version     2.0;
    format      ascii;
    class       volVectorField;
    object      U;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

dimensions      [0 1 -1 0 0 0 0];

internalField   uniform (0.1 0 0);

boundaryField
{
    inlet
    {
        type            fixedValue;
        value           uniform (0.1 0 0);
    }

    outlet
    {
        type            fixedValue;
        value           uniform (0.1 0 0);
    }
}
```

Scheme set

```cpp
FoamFile
{
    version     2.0;
    format      ascii;
    class       dictionary;
    object      fvSchemes;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

ddtSchemes
{
    default         steadyState;
}

gradSchemes
{
    default         Gauss linear;

    limited         cellLimited Gauss linear 1;

}

divSchemes
{
    default         none;
    div(phi,U)      bounded Gauss linearUpwind limited;
    div(phi,T)      $turbulence;
}

laplacianSchemes
{
    default         Gauss linear corrected;
}
```

Linear Solver

```cpp
FoamFile
{
    version     2.0;
    format      ascii;
    class       dictionary;
    object      fvSolution;
}
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //

solvers
{
    p_rgh
    {
        solver          GAMG;
        smoother        GaussSeidel;
        tolerance       1e-6;
        relTol          0.1;
    }

    "(U|T|k|omega|epsilon)"
    {
        solver          smoothSolver;
        smoother        symGaussSeidel;
        tolerance       1e-6;
        relTol          0.1;
    }

    p_rghFinal
    {
        $p;
        relTol         0;
    }

    "(U|k|omega|epsilon)Final"
    {
        $U;
        relTol          0;
    }
}
```

Log

```shell
// * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * //
Create time

Create mesh for time = 43


SIMPLE: convergence criteria
    field p	 tolerance 0.0001
    field U	 tolerance 0.0001
    field T	 tolerance 0.0001
    field "(k|omega|epsilon)"	 tolerance 0.0001

Reading field T

Reading field U

Reading transportProperties

Reading diffusivity DT

Reading/calculating face flux field phi

No finite volume options present

Calculating scalar transport

Courant Number mean: 0.5 max: 0.5
Time = 44

diag():                 5(0.55 1 1 1 0.45)
upper():                4(-0.45 -0.45 -0.45 -0.45)
lower():                4(-0.55 -0.55 -0.55 -0.55)
source():               5(0 0 -1.1856234e-17 1.1856234e-17 0)
upperAddr():            4(1 2 3 4)
lowerAddr():            4(0 1 2 3)
internalCoeffs():       
3
(
1(1)
1(1)
0()
)

boundaryCoeffs():       
3
(
1(1.1)
1(0)
0()
)

D():                    5(1.55 1 1 1 1.45)
smoothSolver:  Solving for T, Initial residual = 8.0470009e-05, Final residual = 5.9846711e-06, No Iterations 1
Convection term diag():                 5(0.05 1.3877788e-17 3.469447e-17 -4.8572257e-17 -0.05)
Convection term upper():                4(0.05 0.05 0.05 0.05)
Convection term lower():                4(-0.05 -0.05 -0.05 -0.05)
Convection term source():               5{0}
Convection term internalCoeffs():       
3
(
1(-0)
1(0)
0()
)

Convection term boundaryCoeffs():       
3
(
1(0.1)
1(-0)
0()
)

Convection term D():                    5(0.05 1.3877788e-17 3.469447e-17 -4.8572257e-17 -0.05)

Diffusion term diag():                  5(0.5 1 1 1 0.5)
Diffusion term upper():                 4(-0.5 -0.5 -0.5 -0.5)
Diffusion term lower():                 4(-0.5 -0.5 -0.5 -0.5)
Diffusion term source():                5(-0 -0 -1.1855769e-17 1.1855769e-17 -0)
Diffusion term internalCoeffs():        
3
(
1(1)
1(1)
0()
)

Diffusion term boundaryCoeffs():        
3
(
1(1)
1(0)
0()
)

Diffusion term D():                     5(1.5 1 1 1 1.5)

SIMPLE solution converged in 44 iterations

End
```



Finial Result

```cpp
internalField   nonuniform List<scalar> 
5(0.9422641 0.8010417 0.6282569 0.41681613 0.15815074);
```



#### Post-processing

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\Tresult.png)

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\Tresultsmooth.png)

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\line.png)

---

![](D:\Ph.D%20Course\2022\Seminar\20220907\figs\end.png)
