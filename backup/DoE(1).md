# Design of Experiments projects
When dealing with experiments, it is not always possible to obtain a large number of data points or replicates due to constraints such as cost, time, and logistics. In such cases, DoE techniques prove to be very useful. When performing parametric studies, the goal is to understand how one or more variables affect the outcome of a process. Below, I describe two case studies where I applied different DoE techniques.

## Complete Design $2^k$
In this design, I was investigating a sieving machine for sedimentary rock samples. My goal was to characterize the particle size distribution and their respective amounts in the samples. Data from previous users were inconsistent and did not provide clear guidance on how to set the parameters for sample size, drying time, vibration intensity, and sieving time.

At the time, I was studying DoE techniques and decided to use a full factorial design. Even though it requires a larger number of tests, I believe it is easier to understand and interpret. Below, I present pictures of the machine and the samples used.

Samples                  |  Sieving machine        |
-------------------------|-------------------------|
![quarteamento](https://github.com/user-attachments/assets/9c3bee34-bc24-447c-a377-07713c562a83)  | ![bertel](https://github.com/user-attachments/assets/d5de4930-9f10-4384-88e5-17d685188758)|

After consulting various materials, I identified a sample size that aligns with best practices for achieving good results with this machine. The next step was to determine the remaining parameters. I came up with the following setup:

|Parameter              | Coded variable | Negative level | Positive level|
|-----------------------|----------------|----------------|---------------|
|Drying time (h)        | A              | 2              | 24            |
|Vibration intensity (%)| B              | 2              | 80            |
|Sieving time (min)     | C              | 3              | 15            |

The final design involved 3 parameters at 2 levels each. A total of 8 unique experiments were conducted, with each experiment repeated 3 times, totaling 24 runs. The experimental matrix, including the results, is shown below:

| Sample | Drying time (h) | Vibration intensity (%) | Sieving time (min) | % of mass replicates 1 | % of mass replicates 2 | % of mass replicates 3 | Mean  | s²   |
|--------|-----------------|-------------------------|--------------------|------------------------|------------------------|------------------------|-------|------|
| 1      | 2               | 20                      | 3                  | 55.2                   | 60.6                   | 58.7                   | 58.2  | 7.5  |
| 2      | 24              | 20                      | 3                  | 58.1                   | 54.5                   | 51.5                   | 54.7  | 11.1 |
| 3      | 2               | 80                      | 3                  | 61.7                   | 61.0                   | 61.8                   | 61.5  | 0.2  |
| 4      | 24              | 80                      | 3                  | 60.2                   | 60.1                   | 61.2                   | 60.5  | 0.3  |
| 5      | 2               | 20                      | 15                 | 55.8                   | 58.1                   | 59.7                   | 57.9  | 3.7  |
| 6      | 24              | 20                      | 15                 | 56.1                   | 56.3                   | 55.7                   | 56.0  | 0.2  |
| 7      | 2               | 80                      | 15                 | 62.3                   | 61.6                   | 61.9                   | 62.0  | 0.1  |
| 8      | 24              | 80                      | 15                 | 61.8                   | 61.2                   | 61.9                   | 61.6  | 0.1  |


By analyzing the effect of each parameter on the final results, as shown in the table below:

| Parameter order | Parameter | Effect | Relevancy    |
|-----------------|-----------|--------|--------------|
| 1°              | A         | -1.68  | not relevant |
|                 | B         | 4.72   | relevant     |
|                 | C         | 0.65   | not relevant |
|                 | AB        | 1.00   | not relevant |
| 2°              | BC        | 0.12   | not relevant |
|                 | AC        | 0.59   | not relevant |
| 3°              | ABC       | -0.26  | not relevant |

These results have shown me that the only factor impacting my tests was the vibration intensity, which allowed me to conduct the tests more quickly and with less concern about drying the samples. While the DoE technique is very useful, careful consideration and critical analysis are essential when making decisions. Below is a image of the analysis conducted for 7 replicates, following the parameters identified in this study.

![3eb0e1fe8393faaf3639dab83fdf1cbac24a83e4](https://github.com/user-attachments/assets/b19cbe85-3e4d-4329-9963-83980a2bcbf2)

In this case, the fluctuation observed at lower particle sizes is acceptable. However, it's important to remember that this analysis was based on 3 replicates, which may not fully capture the complete effect of each variable. Increasing the number of replicates could result in more than 100 tests, which is typically not feasible for various reasons. For this reason, more robust techniques should be applied when conducting parametric studies.

A example code of this technique can be seen on [here](https://rubensctoledo.github.io/COdes_examples/Bib_git.ipynb)
## Composite Central Design

In this project I was trying to optimize a variable on a process. When dealing with a somewhat know process, it is possible to apply a second degree model to describe the desirable output. In this example I was investigating the effect of temperature and residence time of some samples during a reaction. I wish to understand what are the optimal configuration to conduct this test if I want to have the maximum yield output which in this case is reaction conversion. The table bellow shows the configuration used in this project:


| Sample | Time (min) | Temperature (°C) | Energy spent (kJ) | \% CO₂ mass captured (\%mg) | y (\% mg/kJ) |
|--------|------------|------------------|-------------------|---------------------------|-------------|
| 1      | 5          | 400              | 8.04              | 6.90                      | 0.86        |
| 2      | 10         | 400              | 8.26              | 10.58                     | 1.28        |
| 3      | 5          | 550              | 8.16              | 14.47                     | 1.77        |
| 4      | 10         | 550              | 8.52              | 25.99                     | 3.05        |
| 5      | 7.5        | 475              | 8.39              | 22.36                     | 2.66        |
| 6      | 7.5        | 475              | 8.35              | 24.40                     | 2.92        |
| 7      | 7.5        | 475              | 8.32              | 19.96                     | 2.42        |
| 8      | 7.5        | 475              | 8.29              | 23.42                     | 2.82        |
| 9      | 4          | 475              | 8.08              | 18.51                     | 2.29        |
| 10     | 11         | 475              | 8.46              | 19.78                     | 2.34        |
| 11     | 7.5        | 370              | 8.16              | 5.28                      | 0.65        |
| 12     | 7.5        | 580              | 8.50              | 25.00                     | 2.94        |


The first difference of the previous configuration are the replicates. On CCD we are exploring the result plane, where the first top experiments on the table represent a "square" within high and low levels (blue dots). Replicates are all setted on the center of the "square" and they are used to estimate the deviation and extrapoled the uncertainty found on the center for the rest of the results (orange central points). The bottom part of the table are the extrapolation, a second square is justaposed above the first in order to extrapolate the investigated experiments (purple dots). The image bellow ilustrate this configuration.

![WhatsApp Image 2024-12-18 at 08 42 26](https://github.com/user-attachments/assets/555f6f6d-f7c8-4799-bca9-d995d12923b5)

The result of this investigation is two 3D plot (bellow) that indicates which are the best combination of the investigated variables to results.

3D plot of results          |  Plot level          | 
----------------------------|----------------------|
![maximum](https://github.com/user-attachments/assets/eeca742b-a75a-4efe-9e47-44103601e0f3) | 
![plot-level](https://github.com/user-attachments/assets/a8f4ccf5-5476-4d2b-8d3f-f78b6b872da6) |

The code example can be found here.

It is possible to use an ANOVA to find also the relevant paremeters and their combination:

| Source            | DF | Adj SS  | Adj MS   | F-value | p-value |
|-------------------|----|---------|----------|---------|---------|
| Model             | 5  | 6.9841  | 1.39683  | 12.10   | 0.004   |
| Linear            | 2  | 4.7699  | 2.38497  | 20.66   | 0.002   |
| Time              | 1  | 0.3956  | 0.39557  | 3.43    | 0.114   |
| Temperature       | 1  | 4.3744  | 4.37437  | 37.90   | 0.001   |
| Square            | 2  | 2.0293  | 1.01465  | 8.79    | 0.016   |
| Time²             | 1  | 0.4791  | 0.47905  | 4.15    | 0.088   |
| Temperature²      | 1  | 1.8332  | 1.83319  | 15.88   | 0.007   |
| 2-Way Int.        | 1  | 0.1849  | 0.18490  | 1.60    | 0.253   |
| Time*Temperature  | 1  | 0.1849  | 0.18490  | 1.60    | 0.253   |
| Error             | 6  | 0.6925  | 0.11542  | -       | -       |
| Lack of fit       | 3  | 0.5498  | 0.18328  | 3.85    | 0.149   |
| Pure error        | 3  | 0.1427  | 0.04757  | -       | -       |
| Total             | 11 | 7.6767  | -        | -       | -       |



[back](https://rubensctoledo.github.io)




