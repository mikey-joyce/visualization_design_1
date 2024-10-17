# visualization_design_1

## Data
- Dataset is the IGPS (Indianapolic Glaucoma Progression Study), which is the same dataset that I discussed in the last assignment
- NOTE: In the last assignment I did not realize that we were not supposed to do the visualization. I had already done the multidimensional visualization beforehand, which I provided here.
- Data file: year0_0.csv

## Software
- I provided the software that generates the visualizations. It is contained within a Jupyter notebook. Personally, I believe that Jupyter is the best platform for working on visualizations in Python since it is an interactive sandbox, where you can easily see your product in the output of the cells.
- Code file: normalization_check.ipynb

## Description
- Here I discuss why I made this visualization.
- Brief description of the visualization: I have a dataset that involves glaucoma patients. Our research team has a simulator that can simulate flows of fluids within the eye and generate simulated data points that we end up utilizing in an unsupervised learning algorithm to try and group different cohorts of glaucoma patients with different risks of progression associated with each patient. Since unsupervised learning algorithms rely on high separability of data, we want to look at how our normalization methods affect the data at hand to ensure that the data has high separability. Because of this I aim to create a visualization that allows us to see if our data has high separability post normalization.

- Choices:
    - Choice #1: Visualize everything on the MAP (mean arterial pressure) vs. IOP (intraocular pressure) plane.
    - Reasoning: I decided to visualize our data like this for a good reason. Since our data is glaucoma patient data, that means doctors could potentially be reviewing these visualizations at some point. Doctors already are familiar with MAP and IOP with respect to glaucoma and the interplay of these variables. Along with this it is our research team's assumption that the simulated variables that we generate have differences when projected onto the MAP vs. IOP plane. If the data does not have differences on this plane it is very probable that our clustering algorithm will be met with failure, which is why this visualization is extremely important for this research. 

    - Choice #2: Project the simulated variable onto the MAP vs. IOP plane utilizing a colorbar. 
    - Reasoning: I decided to do this because it should be immediately recognizeable to the viewer if the data has significant spots with different values within. If the data all has similar values the color will be similar and we will immediately know that this normalization method is probably not something that we want to utilize. 

    - Results:
        - Min-Max, Robust Scaler, Quantile Transformer: In these visualzations we can come to the conclusion that this normalization method won't be strong for our clustering algorithm. We can tell because many of the features have very similar values (based on the color of each point being similar), which shows that the data is not left with significant separability which could inhibit the performance of the clustering algorithm.
        - Hyperbolic Tangent, Hyperbolic Tangent + Log Transform on R5: We can tell that these normalization methods will be strong for our clustering algorithm because they ensure that the data has high separability within. The tanh + log transform on R5 is even better because it deals with the significant skew of the R5 variable that other variables did not have present. 
