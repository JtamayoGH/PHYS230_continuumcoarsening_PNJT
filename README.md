# PHYS230_continuumcoarsening
## Patrick Noerr, Joshua Tamayo
## PHYS 230, University of California, Merced.
## Code description 
This Jupyter Notebook (Python 3.7) code is designed to solve the coupled convective Cahn-Hilliard and Navier-Stokes equation as described by Sabrina, et al., 2015 to model the coarsening dynamics of a binary liquid with active rotation.
The composition (rotation) of each phase is normalized such that counter-clockwise rotation = -1 and clockwise rotation = 1 (see Example 1 below)
### Required libraries/modules
This code requires the following libraries to be installed in order to run: numpy, matplotlib, IPython, scipy, sympy, numba
## Code overview
### get_initial_configuration(N, lowBD, upperBD)
This function generates a domain that has N-by-N grid points. These grid points are points where the velocity and composition of the binary liquid is updated over time. LowBD and upperBD specify the initial composition of the domain following a uniform distribution with the range [lowBD, upperBD], i.e., setting upperBD to be 1.0 will set up the domain to initially have a larger clockwise rotating composition.
### Forward_solver_full
This is the main function that runs all the necessary subfunctions to update the velocity and composition fields with the following inputs:
*	N – Divides the domain into a N-by-N grid where each grid point is a location where the velocity and composition fields are updated
*	lowBD – Specifies how much of the initial composition is rotating counterclockwise
*	upperBD – Specifies how much of the initial composition is rotating clockwise. NOTE: Setting lowBD and upperBD to the same value will result in an even distribution of both phases
*	dt – Specifies the timestep. NOTE: Since the provided notebook does not implement the semi-implicit Fourier method as described in Sabrina, et al., lower timesteps may be needed to achieve similar results to the published paper
*	num_steps – Total number of steps to iterate. NOTE: Similar to the rational behind choosing an appropriate dt, the total number of steps may be increased to achieve similar results
*	a – Strength of active rotation
*	b – Strength of frictional dampening
## Expected output
The code is designed so that when ran, the code will generate a stack of .png images
## Example parameters & expected results
As of 5/13/2021, the provided notebook generates passive coarsening for all values of a and b.

### Reference
Sabrina, S., Spellings, M., Glotzer, S. C., & Bishop, K. J. M. (2015). Coarsening dynamics of binary liquids with active rotation. Soft Matter, 11(43), 8409–8416. doi:10.1039/c5sm01753j
