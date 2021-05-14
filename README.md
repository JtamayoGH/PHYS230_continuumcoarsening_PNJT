# PHYS230_continuumcoarsening
## Patrick Noerr, Joshua Tamayo
## PHYS 230, University of California, Merced.
## Code description 
This Jupyter Notebook (Python 3.7) is designed to solve the coupled convective Cahn-Hilliard and Navier-Stokes equation as described by Sabrina, et al., 2015 to model the coarsening dynamics of a binary liquid with active rotation.
The composition (rotation) of each phase is normalized such that clockwise rotation = -1 and is color coded to be dark-blue, and counterclockwise rotation and is color coded to be bright yellow = 1 (see Examples below)
### Required libraries/modules
This code requires the following libraries to be installed in order to run: numpy, matplotlib, IPython, scipy
## Code overview
### Instructions:
Run each cell to import the libaries and initalize the functions, then run forward_solver_full to simulate the binary liquid system and generate movies

### get_initial_configuration(N, lb, ub)
This function generates a domain that has N-by-N grid points. These grid points are points where the velocity and composition of the binary liquid is updated over time. LowBD and upperBD specify the initial composition of the domain following a uniform distribution with the range [lowBD, upperBD], i.e., setting upperBD to be 1.0 will set up the domain to initially have a larger clockwise rotating composition.
### Forward_solver_full(a, b, num_steps, N, lb, ub, interval)
This is the main function that runs all the necessary subfunctions (get_initial_configuration, velocity, etc.) to update the velocity and composition fields with the following inputs:
*	N – Divides the domain into a N-by-N grid where each grid point is a location where the velocity and composition fields are updated
*	lb – Specifies how much of the initial composition is rotating clockwise. NOTE: Setting lb and ub to the same value will result in an even distribution of both phases
*	ub – Specifies how much of the initial composition is rotating counterclockwise. NOTE: Setting lb and ub to the same value will result in an even distribution of both phases
*	num_steps – Total number of steps to iterate. NOTE: Similar to the rational behind choosing an appropriate dt, the total number of steps may be increased to achieve similar results
*	a – Strength of active rotation, this determines how 
*	b – Strength of frictional dampening
*	interval - Specifies how many timesteps a .png image is generated

The code is designed so that when ran, the code will generate a stack of .png images detailing the composition field of the domain over time.

### velocity
This subfunction updates the velocity fields on each grid point. Within this subfunction and commented out are lines of code that induce a velocity field onto the domain to try and mix the binary liquid.

### phi
This subfunction updates the compositional field

## Example parameters & snapshots
As of 5/13/2021, the provided notebook generates passive coarsening for all values of a and b. Movies provided in

### Example 1) Passive coarsening with a = 0.0001, b = 100, lb=-0.1, ub=0.1 num_steps=10000
![alt text](https://github.com/JtamayoGH/PHYS230_continuumcoarsening/blob/main/GitHubImg/0.0001_100_100.00000000001425.png?raw=true)

### Example 2) Beginning of droplet formation: a=10, b=100, lb=-0.1, ub=0.4, num_steps=20000
![alt text](https://github.com/JtamayoGH/PHYS230_continuumcoarsening/blob/main/GitHubImg/dropstart10_100.png?raw=true)

### Example 3) Droplet formation: a=10, b=100, lb=-0.1, ub=0.9, num_steps=20000
![alt text](https://github.com/JtamayoGH/PHYS230_continuumcoarsening/blob/main/GitHubImg/drop10_100.png?raw=true)

## Example movies
* Movie1 - Passive coarsening with a = 0.0001, b = 100, lb=-0.1, ub=0.1 num_steps=10000
* Movie2 - Beginning of droplet formation: a=10, b=100, lb=-0.1, ub=0.4, num_steps=20000
* Movie3 - Droplet formation: a=10, b=100, lb=-0.1, ub=0.9, num_steps=20000
* Movie4 - Swirl flow: Induced flow onto the system a = 10, b = 100, lb=-0.1, ub=0.1 num_steps=10000

### Reference
Sabrina, S., Spellings, M., Glotzer, S. C., & Bishop, K. J. M. (2015). Coarsening dynamics of binary liquids with active rotation. Soft Matter, 11(43), 8409–8416. doi:10.1039/c5sm01753j
