# Bent-Electrostatics
---
## Project Description
This code runs simulations of positively and negatively charged particles near an undulating dielectric interface. It takes advantage of an analytical method developed [here](https://doi.org/10.1063/5.0185570). This approach allows for faster computation and simulation than numerical methods, and makes it easier to study charged systems near heterogeneous boundaries, such as membranes in aqueous solutions.

---
## Theoretical and Computational Approach
The potential due to a point charge in 3 dimensions can be written:  

$$\nabla^2 \phi = -\frac{4 \pi \rho}{\epsilon_1}$$  

where $\phi$ is the electrostatic potential, $\rho$ is the charge density, and $\epsilon_1$ is the system's dielectric constant. Assuming that this system is periodic in 2 dimensions, this equation can be rewritten:  

$$\nabla^2 G(\vec{r},\vec{r_i}) = -\frac{4 \pi Q_i}{\epsilon_1} \sum_{m_x,m_y=-\infty}^{\infty} \delta (\vec{r}-\vec{r_i} + m_x L_x \hat{x} + m_y L_y \hat{y})$$  

where $G(\vec{r},\vec{r_i})$ is the Green's function for the system. This can be re-expressed as a Fourier transform:

$$\nabla^2 G(\vec{r},\vec{r_i}) = -\frac{4 \pi Q_i}{\epsilon_1L_xL_y} \delta (z-z_i) \sum_{\vec{m}=-\infty}^{\infty} e^{2 \pi i \left[\frac{m_x}{L_x}(x-x_i)+\frac{m_y}{L_y}(y-y_i)\right]}$$

where $\vec{m}=(m_x,m_y)$. We solve this equation by assuming that, in general, $G(\vec{r},\vec{r_i})$ can be decomposed into $G(z,z_i)$ times $e^{2 \pi i \left[\frac{m_x}{L_x}(x-x_i)+\frac{m_y}{L_y}(y-y_i)\right]}$. We additionally perturb $G(\vec{r},\vec{r_i})$ in accordance with the interfacial perturbation, yielding

$$G(\vec{r},\vec{r_i})=\frac{1}{L_xL_y} \sum_{\vec{m}=-\infty}^{\infty} \left(g_{\vec{m}}^{(0)}(z,z_i) + h(x,x_i,y,y_i)g_{\vec{m}}^{(1)}(z,z_i)\right) e^{2 \pi i \left[\frac{m_x}{L_x}(x-x_i)+\frac{m_y}{L_y}(y-y_i)\right]}$$

This leads to simple differential equations at each order which can be solved using standard electrostatic boundary conditions (constant potential and normal displacement fields at the dielectric interface). The results of those computations are implemented in simulation code. To improve convergence, we decompose the electrostatic potential as $\phi_{total}=\phi_C+\phi_{pol}$ where $\phi_C$ represents the standard pairwise Coulomb contribution to the electrostatic potential, and $\phi_{pol}$ represents the component of the potential due to polarization. 

---
## Results and Conclusions

Our simulations show that charges are repelled from these dielectric interfaces, and that this repulsion is stronger near local 'troughs' in the undulating surface than near local 'peaks'. As the magnitude of the repulsion scales with charge, asymmetric combinations of charge valences can lead to net charge densities near bent interfaces.



## Instructions
Simulation specifications including simulation length, number and valence of particles, and particle sizes can be edited in 'main.c'. To run simulations, compile 'main.c' and run from the command line. The compile command is provided at the top of 'main.c'. Running the code requires one command line argument which denotes the run number you are performing. Some folder names might need to be changed to write output files to desired destinations.

