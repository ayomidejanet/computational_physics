 A. Writing the Dimensionless Equations of Motion & Modeling the Orbit of Mercury


### Scaling Problem

Using the equation of motion for the gravitational force with the relativistic correction term, we get the following equations of motion.   

$$\frac{dx}{dt} = v_x $$  
$$\frac{dy}{dt} = v_y $$  
$$\frac{dv_x}{dt} = \left[-\frac{G(M + m)}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha}{(x^2 + y^2)^2}\right]\vec{x}$$ 
$$\frac{dv_y}{dt} = \left[-\frac{G(M + m)}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha}{(x^2 + y^2)^2}\right]\vec{y}$$ 

Next, we need to scale the variables dependent on space and time to rewrite the equations in dimensionless units. To do this, we first have to define the dependent and independent variables in terms of the new dimensionless variables and the charateristic scaling parameters. $\chi$ is used to represent scaling of the dependent variable and $\tau$ is used to represent scaling of independent variable, typically.  

$$x = x'\chi$$  
$$y = y'\chi$$  
$$v_x = v_{x}'\frac{\chi}{\tau}$$  
$$v_y = x_{y}'\frac{\chi}{\tau}$$  

where $x'$, $y'$, $v_x'$, and $v_y'$ are the new dimensionless variables and $\chi$ and $\tau$ have spaital and temporal units respectively. If we rewrite the above equations in terms of these dimensionless quanities by substituting $x$, $y$, $v_x$, and $v_y$ with above expressions, we will end up with equations in *almost* dimensionless units as desired.  

$$\frac{dx'}{dt'} = v_x'$$  
$$\frac{dy'}{dt'} = v_y'$$  
$$\frac{dv_x}{dt} = \left[-\frac{G(M + m)}{(x^2 + y^2)^{\frac{3}{2}\chi^3}} + \frac{\alpha 4\pi^2}{G(M + m)(x^2 + y^2)^2\chi^4}\right]x'\tau^2$$ 
$$\frac{dv_y}{dt} = \left[-\frac{G(M + m)}{(x^2 + y^2)^{\frac{3}{2}\chi^3}} + \frac{\alpha 4\pi^2}{G(M + m)(x^2 + y^2)^2\chi^4}\right]y'\tau^2$$ 

The next step is to define $\chi$ and $\tau$ in such a way that the coefficients become dimensionless. Ideally, we want to define $\chi$ and $\tau$ such that our coefficients become 1. Since alpha is assumed to be dimensionless using the scaling factors from class [1], we will use these parameters and group the resultant constants all into alpha. Thus, $\chi$ is the semi major axis of Mercury's orbit, and $\tau$ is the orbital period of Mercury given by Kepler's Third Law.

$$\chi = a = \frac{r_p}{1-e}$$
$$\tau = \sqrt{\frac{4\pi^2 a^3}{G(M+m)}}$$

where $a$ is the semi-major axis of Mercury's orbit, $r_p$ is the perihelion of Mercury's orbit, and $e$ is the eccentricity of Mercury's orbit. Thus, the equations of motion in dimensionless units are

$$\frac{dx'}{dt'} = v_x'$$  
$$\frac{dy'}{dt'} = v_y'$$  
$$\frac{dv_x}{dt} = \left[-\frac{4\pi^2}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha 4\pi^2}{G(M + m)(x^2 + y^2)^2\chi}\right]x' = \left[-\frac{4\pi^2}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha}{(x^2 + y^2)^2}\right]x'$$ 
$$\frac{dv_y}{dt} = \left[-\frac{4\pi^2}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha 4\pi^2}{G(M + m)(x^2 + y^2)^2\chi}\right]y' = \left[-\frac{4\pi^2}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha}{(x^2 + y^2)^2}\right]y'$$ 

Now, lets modify the code we developed in class using the 4th ordered Runge-Kutta method to model the orbit of Mercury around the Sun with and without the relativistic correction where $\alpha$ = 0.2.  

**Note:** Units of G, M, and m are blah blah and why (understand the code).
 
### Runge-Kutta Method
The Runge-Kutta Method is a numerical method of approximating the solutions to first order differential equations starting from a known initial condition. The first order ODEs for us are the following:

$$\frac{dx'}{dt'} = v_x'$$  
$$\frac{dy'}{dt'} = v_y'$$  
$$\frac{dv_x}{dt} = \left[-\frac{4\pi^2}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha}{(x^2 + y^2)^2}\right]x'$$ 
$$\frac{dv_y}{dt} = \left[-\frac{4\pi^2}{(x^2 + y^2)^{\frac{3}{2}}} + \frac{\alpha}{(x^2 + y^2)^2}\right]y'$$ 

where we want to approximate the solutions for $x'$, $y'$, $v_x'$, and $v_y'$ which are functions of time and space. We start by assigning k1 to be the derivative of each of these variables (as shown above) evaluated at the initial time condition. The initial conditions for us are the following at $t_0$ = 0:

$$x(0) = r_p$$
$$y(0) = 0$$
$$v_x(0) = 0$$
$$v_y(0) = v$$

which places Mercury at the point of perihelion along the x-axis and the linear velocity of Mercury tangent to the orbital path pointing only in the y-direction. The goal is to approximate the solutions of these functions by doing a Taylor series expansion of the functions at a small, later time step, $dt$, and use a fourth order approximation of the derivative for each function since we will trunciate the series after the second term. 

Process of Fourth Order Approximation of Derivative for Each Function
1. We start with letting k1 equal the slope (derivative) of the function at the beginning of the time step such that t = 0. Or in other words, k1 is the derivative of the function evaluated at the initial time condition.
2. Then, we approximate the value for the function at half the time step ($t = dt/2$) using Taylor expansion with the derivative now being the estimated slope at the midpoint of k1 which is then assigned to k2. 
3. We continue with a similar method where we approximate the function at half the time step but the derivative now being the slope at the midpoint of k2 which is then assigned this value to k3.
4. The last step is to approximate the function at the time step $t = dt$ and assign the slope estimation at the end of the time step to be k4.
5. Finally, we approximate the function at the later time step with again the Taylor expansion about $t = 0$ but the first derivative is not the weighted sum of these slopes to get best estimate of derivative at $t = t + dt$.





## C. Various Values for $\alpha$

Now, let's investigate how increasing the value of $\alpha$ will effect the relativistic corrections of Mercury's orbit. We will consider when $\alpha = 0, 0.2, 0.5,$ and 1 and compare and contrast the results. 

Based on the resulting plots, as $\alpha$ increases the precession of Mercury's orbit increases. However, I suspect there should be more of shift in the perihelion than what is shown in the above plots? My first thought was that, in scaling the equations of motion, I had $\alpha$ absorb the $4\pi^2$ term in addition to the other variable coefficients that had units such as $\chi$, $M$, $m$, and $G$. However, $4\pi^2$ is a dimensionless quantity and should be left out. I changed the scaling in the code below and got the following new results for various alphas. 
This shows the shift in Mercury's orbit much more dramatically. Even further, as $\alpha$ increases, the eccentricity of Mercury's orbit appears to increase as well causing the orbits to take a more elongated shape. This would cause the aphelion (further distance in orbit from Sun) to increase. Thus, the relativistic correction term changes the orientation and eccentricity of a planets orbit.




## D. Demonstrate Numerical Error with Euler Method

What can be said about the stability of the orbit? What does the numerical error mean? Where does it come from? 

The Euler Method, named after the pioneering physicist Leonhard Euler (1707-1783), is an alternative numerical method used to approximate the solutions of linear first order ordinary differential equations (ODEs)[4] like the Runge-Kutta method. There are a couple of variations to the Euler method, but similar to in class, we will be using the explicit or forward Euler method where we approximate an unknown function at a later time $t+dt$ based on its previous known value at time $t$.

How does the method work?
Given a Nth order linear ODE with initial conditions, we can break the equation up into N first order linear ODEs which can be numerically solved using the Euler method. We start by discretizing our continous dependent variable (in this case $x$ and $y$) by discretizing our independent variable (in this case time, $t$). The shorter the interval, $\Delta t$, between consecutive points ($x$, $x + \Delta t$, $x + 2\Delta t$, and so on) the more accurate the approximation. However, the shorter the interval the more iterations need to be done increasing computational time and expenses. Thus, the user has to provide the number of iterations they wish to perform, $N$, to get their approximate solution similar to specifying the number of time steps with the Runge-Kutta method.  

The positions and velocities are then solved for at later time $\Delta t$ by using a Taylor series expansion similar to Runge-Kutta method. However, the key difference is that the derivative of the functions are only approximated once at $t = \Delta t$ assuming initial time to be 0. Thus, the Euler method is essentially the first order Runge-Kutta method.  

Since we ignore the higher order terms in the Taylor expansion for both methods at each time step, we introduce numerical errors in our solution at each iterative step due to this approximation. However, the numerical error accumlated with the Euler method is greater than RK4 method because the derivative used in the Taylor expansion to approximate the functions at later time step is only a first order approximation versus with RK4 it is a fourth order approximation. As a result, the truncation error in Rk4 method is less compared to in the Euler method.

We can demonstrate how numerical error arises in approximating the orbital path for Mercury using the Euler method. This is because with RK4 you approximate the function at much smaller times steps since you do higher order approximations of the slope rather than with the Euler method you only approximate the slope at each time step. Thus, the orbit of Mercury appears unstable because it will take many and very small time steps to reach accuracy of RK4. 
