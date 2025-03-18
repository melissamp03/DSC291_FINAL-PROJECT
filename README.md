# DSC291_FINAL-PROJECT: MJD Data Release Analysis
DSC Final project repository. 
Authors: Akbota Assan¹ (A69037121), Devana Perupurayil¹ (A69034326), Melissa Medina-Peregrina² (A59016508) ¹Halıcıoğlu Data Science Institute at UC San Diego. ²Department of Physics at UC San Diego. 

Introduction
Neutrinoless double beta decay (0) is a theoretical rare nuclear process whereby a nucleus decays into another one and emits two electrons and no antineutrinos. For each nuclear decay, only a small amount of energy is released and available for detection. The goal is to protect this small signal from the background.

The Majorana Demonstrator experiment searched for 0 of 76Ge using modular arrays of 56 high-purity Ge detectors. The MJD dataset represents a portion of its detector waveforms with corresponding analysis labels released to support the training and test of AI/ML algorithms to get an unambiguous identification of 0 events.

Objective
The objective of this project is to analyze the MJD dataset using Bayesian inference to determine the unknown parameter and other relevant fitting parameters. This analysis will help in extracting the key detector parameters and determine its potential for detecting neutrinoless double-beta decay (0νββ) events in 76Ge.

Methodology
We will analyze the MJD dataset to extract relevant information from the energy spectrums, evaluate classification performance, and fit the unknown parameter θc​ for Detector C in the following way:

Using the NumPy and Pandas libraries, load the four CSV files that conforms the data set into a structured data format. To visualize the energy spectrum of each detector, we will use the ID, classification score, and energy value of each event and build a histogram.

Compute the true positive rate to quantify how effectively the cut retains signal events by setting a classification score threshold based on the 1592 keV peak in detector A to maximize the signal events.

Compute the false positive rate to quantify how many background events there are after the cut based on the 2103 keV peak in Detector B. Evaluate the impact of the classification score threshold applied in the previous step.

Using the SciPy library, build a probability density function for the 2039 keV peak (modeled as a Gaussian distribution with =1 keV) which is the expected signal for 0 decay.
In our analysis, we iteratively apply different energy cuts to neutrinoless double beta decay data to distinguish signal from noise. By filtering energy values within a specific range, we extract meaningful distributions from three detectors (A, B, and C). We then construct probability density functions (PDFs) for each detector using kernel density estimation (KDE). Additionally, we aggregate the filtered data into a DetectorTarget histogram and analyze its shape. Using statistical tools, we compare these PDFs against a Gaussian distribution to determine the optimal energy cut that most closely resembles a Gaussian shape, which may indicate the presence of a genuine signal.

The Bayesian approach will be applied to fit the PDFs to the detector target histogram and estimate the unknown parameters. The process includes:

- Defining Likelihood Function: The observed energy spectrum will be modeled as a Poisson-distributed count in each energy bin.
- Choosing Priors: The priors for 𝜃A, 𝜃B, 𝜃C, and 𝜃NLDBD will be Gaussian distributions, incorporating prior knowledge from calibration detectors and physical constraints.
- The posterior distributions of 𝜃A, 𝜃B, 𝜃C, and 𝜃NLDBD will be computed using Markov Chain Monte Carlo (MCMC) sampling technique.

The Bayesian method is chosen for this analysis because:

- Bayesian inference allows us to integrate prior information from Detectors A and B into the fitting process, making use of previously known calibration data.
- Bayesian inference provides full posterior distributions, allowing for a more comprehensive assessment of uncertainties through credible intervals.
- Bayesian methods use Markov Chain Monte Carlo (MCMC) to explore the parameter space efficiently, even in cases where the likelihood function is complex or non-Gaussian.

Expected outcomes
Histograms showing the energy spectra for each detector.
True Positive and False Positive Rate estimations
Best-fit values for θA, θB, and θC.
Estimation of the 0 signal strength parameter based on the dataset.
Calculation of the upper limit on 0 at 90% confidence level. 
Evaluation of the experimental sensitivity.

References
Arnquist, I. J. et al (MAJORANA Collaboration)(2023). Majorana demonstrator data release for AI/ML Applications. arXiv preprint arXiv:[2308.10856]
