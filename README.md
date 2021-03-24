# Modeling-Covid-19-in-Lombardy
<br>
Development of simple compartmental models (SEIR, SIR) in order to simulate the spread of COVID-19 the Lombardy Region. The data used for this project refer to the daily number of new infected individuals during the first wave of the pandemic.

This file has been created in order to propose a solution to a Simulation and Modeling assignment:

**Exercise 1: Calibration**
<br>
Definition of a deterministic compartmental model to capture the spread of Covid-19 and calibration on the the first part of the data that is provided (train days for the provinces: LO: 64, PV: 68, SO:74, MN: 74, MI: 68, CO: 68, BS: 68, MB: 68, LC: 70, CR: 66, BG: 66, VA: 73)

# I decided to use a simple SEIR model
       
Individuals can be part of one of the following compartments:

1. Susceptibles ($S$) 
<br>
2. Exposed ($E$)
<br>
3. Infected ($I$) 
<br>
4. Recovered ($R$)


System of differential equations :

\begin{equation}
\frac{\partial S_t}{\partial t} = bN -\beta \frac{I_t}{N} S_t - mS\\
\frac{\partial E_t}{\partial t} = \beta \frac{I_t}{N} S_t - \delta E_t -mE\\
\frac{\partial I_t}{\partial t} = \delta E_t - \gamma I_t -mI\\
\frac{\partial R_t}{\partial t} = \gamma I_t -mR\\
\end{equation}

i = 1,..,12 $\rightarrow$  province index

**Parameters:**
* $\frac{I}{ N}$ : probability of getting in contact with an infected 
* $\beta$: transmission probability
* $\delta$ = rate at which infected become infectious : $\delta =  \frac{1}{\text{latent period}} $ 
* $\gamma$ is the recovery rate :  $\gamma =  \frac{1}{\text{avg duration of infectious period}} $ 
* $b$ = birth rate
* $m$ = natural mortality rate



**Exercise 2: Adding age structure to the model**
<br>
Building of a simple SIR model with age structure, where the average number of contacts between individuals of different age classes is defined by the contact matrix defined in the csv italian_matrix.csv.

# Here is I defined the SIR model
       
Individuals can be part of one of the following compartments:

1. Susceptibles ($S$) 
<br>
3. Infected ($I$) 
<br>
4. Recovered ($R$)


System of differential equations :

\begin{equation}
\frac{\partial S_{i}}{\partial t} = - \sum_j{\beta_{ij}\frac{I_j}{N_j}S_i} \\
\frac{\partial I_{i}}{\partial t} = \sum_j{\beta_{ij}\frac{I_j}{N_j}S_i} - \gamma I_i \\
\frac{\partial R_{i}}{\partial t} = \gamma I_i \\
\end{equation}

j = 0,..,16 $\rightarrow$  age group index

**Parameters:**
* $\frac{I_j}{N_j}$ : proportion of infected for age group j
* $\beta$: WAIFW matrix $\rightarrow$ $\beta = q * C$
    * $q$ = intrinsic probablity of transmission
    * $C$ = contact matrix
* $\gamma$ is the recovery rate :  $\gamma =  \frac{1}{\text{avg duration of infectious period}} $ 



**Exercise 3: Improve the model**
<br>
Extention of the age-stratified model developed in Exercise 2, adding one or more of the restrictive measures that have been implemented in the Lombardy Region in order reduce the spread of the virus. 


