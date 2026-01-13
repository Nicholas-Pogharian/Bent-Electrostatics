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

where $\vec{m}=(m_x,m_y)$.

---
## Results and Conclusions

## Instructions
Simulation specifications including simulation length, number and valence of particles, and particle sizes can be edited in 'main.c' To run simulations, compile 'main.c' and run from the command line. This requires one command line argument which denotes the run number you are performing.

