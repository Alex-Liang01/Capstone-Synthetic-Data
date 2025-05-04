# Privacy Metrics 

To measure the privacy of the synthetic data, we used three privacy metrics: Nearest Neighbor Distance Ratio (NNDR), Nearest Neighbour Adversial Accuracy, and Membership Inference Attack.

## Nearest Neighbour Distance Ratio

Nearest Neighbor Distance Ratio evaluates how close synthetic data points are compared to the simulated data points by comparing distances. NNDR is a ratio from score 0 to 1 with higher scores indicating stronger privacy while values close to 0 have higher disclosure risk. It compares distances to the nearest vs. the distance to the second nearest neighbor.

### Simulated Data from Marginal Distributions

<img width="716" alt="image" src="https://github.com/user-attachments/assets/0137f43e-f52d-4850-8980-bcffb193433e" />

Looking at the results of the NNDR metric for the synthetic dataset that was created using simulated data with provided marginal distributions, it is observed that the results are quite good with all the NNDR results being around 0.95 accross all sample sizes, and missing percentages across all the different synthesizers. This shows that across all the synthesizers, the synthetic data points are quite different from that of the simulated dataset that it is trained on meaning that the privacy of the synthetic datasets are good.

### High Association Data
<img width="717" alt="image" src="https://github.com/user-attachments/assets/0f02a494-3c85-4b27-8596-24a170cb247b" />

Looking at the results of the NNDR metric for the synthetic dataset that was created using simulated data with enforced high associations between variables, it is observed that the results are good with all the NNDR results being around 0.95 accross all sample sizes, and missing percentages across all the different synthesizers. This shows that once again, across all the synthesizers, the synthetic data points are quite different from that of the simulated dataset that it is trained on meaning that the privacy of the synthetic datasets are excellent.


### Moderate Association Data
<img width="711" alt="image" src="https://github.com/user-attachments/assets/bb73fb6e-578e-4f17-98cd-2e316f2b2c12" />

Looking at the results of the NNDR metric for the synthetic dataset that was created using simulated data with enforced moderate associations between variables, it is observed that the results are once again excellent with all the NNDR results being around 0.95 accross all sample sizes, and missing percentages across all the different synthesizers. This shows that once again, across all the synthesizers, the synthetic data points are quite different from that of the simulated dataset that it is trained on meaning that the privacy of the synthetic datasets are great.

### Low Association Data
<img width="715" alt="image" src="https://github.com/user-attachments/assets/1d317e79-63ac-459f-959a-13d1e5ba18a7" />

Looking at the results of the NNDR metric for the synthetic dataset that was created using simulated data with enforced low associations between variables, it is observed that the results are once again excellent with all the NNDR results being around 0.95 accross all sample sizes, and missing percentages across all the different synthesizers. This shows that once again, across all the synthesizers, the synthetic data points are quite different in terms of  from that of the simulated dataset that it is trained on meaning that the privacy of the synthetic datasets are great.

### NNDR Overall

Overall, all the synthetic data synthesizers perform very well in terms of the NNDR metric showing that privacy in the synthetic datasets is very good. None of the synthesizers get affected by different sample sizes, missing percentages, and association strengths in terms of the NNDR metric.

## Nearest Neighbour Adversial Accuracy

Nearest Neighbor Adversial Accuracy evaluates how well an adversary can distinguish real and synthetic data using a nearest neighbor classifier. NNAA is a score from 0 to 1 with lower scores closer to 0 indicating better privacy. Values greater than or equal to 0.5 indicate high privacy loss.

### Simulated Data from Marginal Distributions

<img width="716" alt="image" src="https://github.com/user-attachments/assets/46595d1b-06ae-4fbd-997f-e7d051154d63" />

Looking at the results of the NNAA metric for the synthetic dataset that was created using simulated data with provided marginal distributions, it is observed that GC is consistently around 0.40 meaning that it consistently has moderately good privacy. Looking at CTGAN and TVAE, it is observed that as the sample size of the training data gets larger, the NNAA metric gets lower meaning that as sample size increases, the synthetic dataset privacy gets better. Overall, GC performs moderately well and is consistent across different missing values and dataset sizes while the synthetic datasets trained by CTGAN and TVAE privacy increases as the sample size of the simulated dataset increases. 

### High Association Data

<img width="716" alt="image" src="https://github.com/user-attachments/assets/ff39a582-5566-4f0c-90b7-a7e2c25eed36" />

Looking at the results of the NNAA metric for the synthetic dataset that was created using simulated data with enforced high associations between variables, it is observed that GC's NNAA exceeds that of the benchmark of 0.5 at 10,000 rows indicating slight privacy risk. At sample sizes greater than 25,000, it's privacy gets better with values around 0.3.  Looking at CTGAN and TVAE, it is observed that as the sample size of the training data gets larger, the NNAA metric gets slightly lower meaning that as sample size increases, the synthetic dataset privacy gets better. Overall, GC performs moderately well but only at larger sample sizes while the synthetic datasets trained by CTGAN and TVAE privacy increases as the sample size of the simulated dataset increases. 


### Moderate Association Data
<img width="711" alt="image" src="https://github.com/user-attachments/assets/98449d66-fee8-418d-81a3-363b16474caf" />

Looking at the results of the NNAA metric for the synthetic dataset that was created using simulated data with enforced moderate associations between variables, it is observed that GC consistently performs around 0.3 indicating great privacy. Looking at CTGAN and TVAE, it is observed that once again as the sample size of the training data gets larger, the NNAA metric gets slightly lower meaning that as sample size increases, the synthetic dataset privacy gets better. Overall, GC performs well while the synthetic datasets trained by CTGAN and TVAE privacy increases as the sample size of the simulated dataset increases. 

### Low Association Data
<img width="713" alt="image" src="https://github.com/user-attachments/assets/db47cf8c-da1a-4c8d-b853-4f908749d528" />

Looking at the results of the NNAA metric for the synthetic dataset that was created using simulated data with enforced low associations between variables, it is observed that GC consistently performs around 0.3 indicating great privacy. Looking at CTGAN and TVAE, it is observed that once again as the sample size of the training data gets larger, the NNAA metric gets slightly lower meaning that as sample size increases, the synthetic dataset privacy gets better. Overall, GC performs well while the synthetic datasets trained by CTGAN and TVAE privacy increases as the sample size of the simulated dataset increases.

### NNAA Overall

Overall, looking at the NNAA metric, all the synthesizers generally have good privacy. The statistical method GC performance generally stays consistent across different sample sizes, association strengths, and missing percentages. It only performed slightly worst at small sample sizes and high association between variables. CTGAN and TVAE were quite consistent across the board with the privacy of the synthetic datasets trained with these neural network methods increasing as the sample size of the training dataset increases.

## Membership Inference Attack

Membership Inference Attack evaluates whether an adversary can determine if a specific data point was part of the training set used to create the synthetic data. MIA is a score from 0 to 1 with lower scores less than 0.5 indicating excellent privacy but poor accuracy. Values that are greater than or equal to 0.5 indicate poor privacy and excellent accuracy.

### Simulated Data from Marginal Distributions

<img width="715" alt="image" src="https://github.com/user-attachments/assets/bee3d4ef-920e-417f-bb3f-df85fe58f8ec" />

Looking at the results of the MIA metric for the synthetic dataset that was created using simulated data with provided marginal distributions, it is observed that all the synthesizers perform better than the benchmark of 0.5 indicating that the privacy protection of the datasets trained by these synthesizers are consistently excellent. It is observed that the synthesizers have quite a clear pattern across all sample sizes and rows with GC being most private followed by CTGAN and then TVAE.

### High Association Data

<img width="718" alt="image" src="https://github.com/user-attachments/assets/378be112-8d05-4bc3-a6fb-6f1f371aa955" />

Looking at the results of the MIA metric for the synthetic dataset that was created using simulated data with enforced high association between variables, it is observed that the GC and CTGAN synthesizers perform better than the benchmark of 0.5 indicating that the privacy protection of the datasets trained by these synthesizers are consistently excellent. Looking at TVAE, it is observed that it performs slightly worst than the benchmark of 0.5 at low sample sizes indicating slight privacy risk. It is once again observed that the synthesizers have quite a clear pattern across all sample sizes and rows with GC being most private followed by CTGAN and then TVAE.

### Moderate Association Data

<img width="713" alt="image" src="https://github.com/user-attachments/assets/a6eb0b11-dfb2-4325-8693-a5590408ab15" />

Looking at the results of the MIA metric for the synthetic dataset that was created using simulated data with enforced moderate association between variables, it is observed once again that the GC and CTGAN synthesizers perform better than the benchmark of 0.5 indicating that the privacy protection of the datasets trained by these synthesizers are consistently excellent. Looking at TVAE, it is observed that it performs slightly worst than the benchmark of 0.5 at 50,000 rows 10% missing indicating slight privacy risk. It is once again observed that the synthesizers have quite a clear pattern across all sample sizes and rows with GC being most private followed by CTGAN and then TVAE.

### Low Association Data
<img width="714" alt="image" src="https://github.com/user-attachments/assets/7702584b-f6e6-44a0-abff-cf90ec26ad28" />

Looking at the results of the MIA metric for the synthetic dataset that was created using simulated data with enforced low association between variables, it is once again observed that the GC and CTGAN synthesizers perform better than the benchmark of 0.5 indicating that the privacy protection of the datasets trained by these synthesizers are consistently excellent. Looking at TVAE, it is observed that it again performs slightly worst than the benchmark of 0.5 at 50,000 rows sizes indicating slight privacy risk. It is once again observed that the synthesizers have quite a clear pattern across all sample sizes and rows with GC being most private followed by CTGAN and then TVAE.

### MIA Overall

Overall, looking at the MIA metric, GC is consistently the most private, followed closely by CTGAN. Both of these synthesizers have excellent privacy. TVAE sometiems perform worst than the benchmark of 0.5 indicating that there is slight privacy issues with the TVAE synthesized datasets.

## Privacy Metrics Overall

Overall, looking at all the metrics NNDR, NNAA, and MIA together, it is observed that GC consistently has great performance with it's NNDR, NNAA and MIA always being good. The synthetic datasets trained by CTGAN are consistently excellent as well with it's NNDR, NNAA and MIA being great across all conditions. Looking at TVAE, it is observed that TVAE performed well for NNDR and NNAA but had some slight issues in terms of the MIA metric. With a high NNDR and NNAA, this shows that synthetic datasets trained with TVAE are quite spread out from the real data but there are some patterns in the dataset that are too similar to the real dataset leaking membership information in some scenarios. This is consistent with the data fidelity results where in more complex relationships between variables, TVAE performed the best meaning that it is the most similar to the simulated dataset that it is trained on.
