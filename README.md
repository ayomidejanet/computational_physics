# computational_physics

### Overview
Newton's Law of Gravitation provided a theoretical explanation for the centeral attractive force that causes planets to move in elliptical orbits around their host star, which was previously determiend by Kepler from detailed measurements of the motion of the planets within our solar system. The host star and planet rotate as a two-body system about their center of mass which is one of the focal points in the ellipses and also referred to as the barycenter. Since the mass of the host star is often much larger in comparsion to the orbiting planets, the force acting on each planet is, to a good first order approximation, only due to the host star. Newtons Law of Gravitation as a first order approximation is given by:  
  
$$ F = -G \frac{Mm}{|r|^3}\vec{r} = -G \frac{Mm}{|r|^2}\hat{r} $$

where F is the force experienced by the planet of mass $m$ due to its host star of mass $M$, G denotes the gravitational constant, and $\vec{r} = \vec{r}(t)$ is the planet's positional vector in the radial direction. Since the first order approximation only considers the two bodies interacting with each other, the two-body problem can be reduced to a one-body problem by introducing new cooridinates about the center of mass. The center of mass is treated as a fixed point whose force is acting on the reduced mass of the system. The singular force acting on the reduced mass is equivalent to the two individual forces from the planet and star acting on the center of mass. As derived in class [1], the reduced equation of motion becomes

$$ \frac{d^2\vec{r}}{dt^2} = -G \frac{M + m}{|r|^3}\vec{r} $$

where $r$ is now the distance between the two objects. Although this is a decent approximation for planetary systems similar to ours, the influence from the gravitational pull of another orbiting planet can perturb a planets orbit. This interaction causes the planets major axis to precess (rotate) about the center of mass which shifts the orientation of its orbit in space. The precession of the orbits of all the planets in the solar system, for the most part, can be describe by Newtonian mechanics except for Mercury. 

In 1859, Urbain Le Verrier re-analyzed time observations of Mercury transiting the Sun and showed the rate of precession disagreed with Newton's theory providing an unexplained 38 arcseconds per century [2]. In other words, the perihelion of Mercury's orbit shifted by this angle as shown in the figure below. The perihelion is the point in a celestial bodies orbit at which it is closest to the Sun.
![Screen%20Shot%202022-12-06%20at%208.40.02%20PM.png](attachment:Screen%20Shot%202022-12-06%20at%208.40.02%20PM.png)

**Figure 1:** (a) Shows the predicted orbit of Mercury from Newtonian mechanics [3]. (b) Shows the relativistic orbit of Mercury with the perihelion shifting slightly after each complete orbit around the Sun [3].

Newtonian mechanics predicts a closed elliptical orbit as shown in Figure 1a where Mercury returns to the exact same position after one full orbit. However, observations showed the orbit shown in Figure 1b where the perihelion shifts during each period of rotation. The observed angle (shift) was later corrected by Simon Newcomb in 1882 to be 43" [2]. Theorists began developing new ideas to explain the shift such as a small planet between the Sun and Mercury perturbing its orbit. However, all these explanations only led to more problems and were unable to be proven observationally. It wasn't until Albert Einstein developed his Theory of General Relativity that explained how the curvature of spacetime influenced the gravitational force. This introduced a correction term that varies as 1/r^4. Not only did this match the observed perihelion shift for Mercury, but also provided a solid argument for the legitamacy of his theory. The gravitational force with the relativistic correction term is given by:

$$ \frac{d^2\vec{r}}{dt^2} = \left[-G \frac{M + m}{|r|^3} + \frac{\alpha}{|r|^4}\right]\vec{r} $$

Since this signficiant discovery, the perihelion shift due to relativistic effects has been confirmed for the other planets in our solar system as well. This shows most planets move in ellipses that precess.   

**NOTE:** The barycenter for the orbit of Mercury around the Sun is within the Suns radius. Thus, we will assume the origin (the center of mass) is the Sun.  

### Problem Instructions
General relativity introduces a correction to the inverse square law of gravity. The correction term ~$\frac{\alpha}{r^4}\vec{r}$ is added to the usual inverse square expression of the gravitational force. Our Sun is a relatively small star, thus the $\alpha$ is usually very small and can be neglected at the astronomical unit distances. However, planets closer to the Sun exhibit observable corrections to the Newtonian motion. For the purpose of this problem (just to make a point), lets assume that the $\alpha$ is 0.2 in our dimensionless units.  

