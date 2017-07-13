
## HMC Inversion of multidimensional tomography data

This set of programs are built to incorporate MCMC inversion using Hamiltonian Mechanics. Essentially, any amount of
parameters and any forward model can be supplied, as long as one can describe the measurement errors, data uncertainty
and misfit function. This could be used as a framework for building any inversion using HMC. This implementation, based
upon the previous [larsgeb/hmc_vsp](https://github.com/larsgeb/hmc_vsp/), aims at inverting 2D and possibly 3D tomography data.

### Install

First generate data using the makeSynthetics.cpp file. Compile it against the auxiliary and the linearalgebra class and
you're good to go.

The inversion is done using the runSampling.cpp file, which should be compiled against the auxiliary, linearalgebra,
randomnumbers and montecarlo class. These are not finished yet, but the Hamiltonian mechanics is implemented in the
montecarlo::leap_frog().

So, in short:

```{r, engine='bash', building the sampling script with g++ to the executable sampling}
g++ makeSynthetics.cpp linearalgebra.cpp auxiliary.cpp -o synthetics

```

```{r, engine='bash', building the sampling script with g++ to the executable sampling}
g++ runSampling.cpp linearalgebra.cpp randomnumbers.cpp auxiliary.cpp montecarlo.cpp -o sampling

```

Note that the nested templates (and some other compatibility stuff) are compiled only correctly from C++11 onwards. The
following should work if you get an error:

```{r, engine='bash', building the sampling script with g++ to the executable sampling}
g++ -std=c++11 runSampling.cpp linearalgebra.cpp randomnumbers.cpp auxiliary.cpp montecarlo.cpp -o sampling
```

