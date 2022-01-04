# cartridgeCaseLitReview
Lit review for cartridge case comparison algorithms


## Important Papers

### CMC Papers

- *Proposed “NIST Ballistics Identification System (NBIS)” Based on 3D Topography Measurements on Correlation Cells* Song (2013)

  - [https://www.nist.gov/publications/proposed-nist-ballistics-identification-system-nbis-based-3d-topography-measurements](https://www.nist.gov/publications/proposed-nist-ballistics-identification-system-nbis-based-3d-topography-measurements)

  - Synopsis: Introduces the concept of *correlation areas* and proposes using the comparison of *correlation cells* to estimate the registration phase (translation) and angle of two cartridge cases. The "Contiguous Matching Cells" Method is discussed to quantify the similarity between two cartridge cases.

  - Limitations: There are few details provided in this paper in how the method should actually be implemented, although discussion of an actual implementation was not the focus of this paper. The various thresholds discussed in the paper (e.g., section 4) is based without much justification on the Consecutive Matching Striae paper.

  - Contribution: Provides a conceptual description of the overall CMC pipeline and some hints at how to actually implement the pipeline.

- *Validation Tests for the Congruent Matching Cells (CMC) Method Using Cartridge Cases Fired with Consecutively Manufactured Pistol Slides* Chu et al. (2013)

  - Synopsis: Shares summative results from an implementation of the CMC method as detailed in Song (2013). Using a set of 40 3D topographical scans of cartridge cases from Fadul (2011), describes some of the parameters used to preprocess and compare the cartridge case scans. Their results show that using a CMC count threshold of 6, the CMC count similarity score correctly distinguishes between the matching and non-matching comparisons from this data set.

  - Limitations: There is ambiguity in precisely what parameters and methods were used to perform the comparisons. For example, it appears that grids of 7x7 and 6x6 were both used to compare scans "depending on the actual size of different correlation areas" which the authors do not describe further. In terms of the CMC method performance, there is not much separation between the matching and non-matching CMC count distributions.

  - Contribution: Demonstrates that a particular implementation of the CMC method works on the Fadul cartridge case comparisons.

- *3D topography measurements on correlation cells—a new approach to forensic ballistics identifications* Song et al. (2014)

  - Synopsis: Similar to Chu et al. (2013), applies the CMC method to the 40 scans from Fadul (2011). It appears that some additional preprocessing steps were added to the pipeline outlined in Chu et al. (2013) including applying a band-pass Gaussian filter and "identify[ing] and remov[ing] dropouts and outliers."

  - Limitations: There are additional ambiguities introduced in this paper including what algorithm was used to apply the Gaussian filter, what "dropouts" are in the scans, how the authors define "outliers," and what it means to "remove" these dropouts and outliers.

  - Contributions: Some of the parameters (e.g., the Gaussian bandpass filter wavelength cutoffs) are provided in greater detail. Figure 6 of this article is the exact same as Figure 4(b) in Chu et al. (2013), so it is unclear if the pipeline additions detailed in this paper weren't already in-use in Chu et al. (2013).

- *Fired Cartridge Case Identification Using Optical Images and the Congruent Matching Cells (CMC) Method* Tong et al. (2014)

  - Synopsis: Applies the CMC method to 2D images of the Fadul (2011) cartridge cases. The results (Figure 7(b)) show that, compared to the 3D scans (Song et al. (2014)), when applied to 2D images the CMC method assigns higher CMC scores to non-match comparisons and lower CMC scores to match comparisons.

  - Limitations: Many of the same ambiguities that were in the previous CMC papers are also in this paper. The authors do, however, specify that a grid of 7x7 was used for all scans rather than 7x7 or 6x6.

  - Contributions: This paper does indicate that a "training" set of 20 scans (out of 40 scans) was used to identify the optimal CMC method thresholds $(T_x,T_y,T_{CCF},T_{\theta})$. In particular, amongst a grid of thresholds, the thresholds that result in the largest distance between the largest non-match CMC count and the smallest match CMC count are selected as optimal. Figure 7(b) shows the CMC count distributions for all 40 scans instead of just the 20 hold-out scans not used in the training.

- *An Improved Algorithm of Congruent Matching Cells (CMC) Method for Firearm Evidence Identifications* Tong et al. (2015)

  - Synopsis: Introduces the first "improvement" upon the original CMC method discussed in Song (2013). In subsequent papers, this improved method came to be called the "High CMC" method. The results indicate that the High CMC method yields greater separation in the matching and non-matching CMC count distributions for the comparisons of both the Fadul (2011) 3D scans and 2D images.

  - Limitations: There are ambiguities in how the High CMC method actually works in this paper. In particular, there are multiple readings of the procedure outlined on pages 109 and 110 that yield different versions of the algorithm.

  - Contribution: As the original method CMC count is the lower-bound of the High CMC count, it is indeed an improvement upon the original CMC method of Song (2013).

- *Proposed “Congruent Matching Cells (CMC)” Method for Ballistic Identification and Error Rate Estimation* Song (2015)

  - Synopsis: Song's follow-up to the 2013 paper. This paper was submitted soon after Song (2013) and wasn't published until 2015. This paper emphasizes more how the CMC method should be validated by calculating the false positive/negative error rates. The Discussion/Conclusion alludes the calculation of likelihood ratios using the CMC count distributions.

  - Limitations: Similar to Song (2013), there are few details in this paper on how to actually implement the CMC method. Song (2013) and this paper are much like the "methods" section of a paper while the "results" section is provided in the form of Chu et al. (2013), Song et al. (2014), and Tong et al. (2014).

  - Contribution: This paper adds to the contributions of Song (2013) by detailing the calculation of false positive and false negative error rates as a validation procedure. This paper also coins the *Congruent* Matching Cells as opposed to the "Contiguous" Matching Cells originally proposed in Song (2013).

- *Correlation of firing pin impressions based on congruent matching cross-sections (CMX) method* Zhang et al. (2016)

  - Synopsis: Introduces a CMC-like procedure to be used on 3D scans of firing pins. The base CMX method yields relatively large CMX counts for both the match and non-match comparisons when applied to the Fadul (2011) firing pin scans (Figure 11), although there is perfect separation. The separation between the matching and non-matching CMX count distributions is improved by averaging the 2 largest CMX scores across different rotations (what they call CMX' - Figure 12).

  - Limitations: Again, there are ambiguities in precisely how the method's sub-routimes is implemented (Figure 9 diagram).

  - Contribution: This is the first application of a CMC-like procedure to firing pin scans.

- *Applying 3D measurements and computer matching algorithms to two firearm examination proficiency tests* Ott et al. (2017)

  - Synopsis: Applies the CMC method to new cartridge case and firing pin scans that had previously been used in firearm examiner proficiency tests. The results (Figures 7 and 8) indicate that the CMC and CMX method separate these matching and non-matching comparisons well compared to results in Chu et al. (2013), Song et al. (2014), Tong et al. (2014) indicating a dependency on the data used. Additionally, the authors propose using the sum of the CMC and CMX scores for a particular comparison as its final similarity score.

  - Limitations: The authors point out that the CMC/CMX methods do not perform well when there are large anomalous regions in a scan (Figure 7 - thin bars). None of the implementation ambiguities from the previous papers are clarified here.

  - Contribution: This is a good validation study of the CMC and CMX methods. This was also the first observed use of the CMC plots (Figure 5).

- *A convergence algorithm for correlation of breech face images based on the congruent matching cells (CMC) method* Chen et al. (2017)

  - Synopsis: Introduces the next improvement upon the original CMC method of Song (2013) after Tong et al. (2015) referred to as the "Convergence CMC" method. Additionally, 3 new data sets (Weller (2012), La Porte (2011), and Lightstone (2010)) are used to validate the results. The results indicate that the convergence CMC method assigns smaller CMC scores to non-matching comparison comparable CMC scores to matching comparisons compared to the High CMC method.

  - Limitations: This method adds additional ambiguity in sub-routine implementation (e.g., second order robust Gaussian regression filter). Additionally, while I have implemented this procedure, I have yet to observe results comparable to the results shown in this paper for the Convergence CMC method. 

  - Contribution: This Convergence CMC method seems to be the current favorite amongst the NIST researchers and indeed tends to perform better than the previously proposed method.

- *Estimating error rates for firearm evidence identifications in forensic science* Song et al. (2018)

  - Synopsis:

  - Limitations:

  - Contribution:

- *Valid data based normalized cross-correlation (VDNCC) for topography identification* Tong et al. (2018)

  - Synopsis/Contribution:

  - Limitations

- *A normalized congruent matching area method for the correlation of breech face impression images* Chen et al. (2018)

  - Synopsis/Contribution:

  - Limitations

- *The Use of Correlated Binomial Distribution in Estimating Error Rates for Firearm Evidence Identification* Zhang (2019)

  - Synopsis/Contribution:

  - Limitations

- *Evaluating Likelihood Ratio (LR) for firearm evidence identifications in forensic science based on the Congruent Matching Cells (CMC) method* Song et al. (2020)

  - Synopsis/Contribution:

  - Limitations

- *Convergence-improved congruent matching cells (CMC) method for firing pin impression comparison* Zhang et al. (2020)

  - Synopsis/Contribution:

  - Limitations

- *Statistical models for firearm and tool mark image comparisons based on the congruent matching cells (CMC) method* Zhang et al. (2021)

  - Synopsis/Contribution:

  - Limitations

### Cartridge Case Papers

- *An Empirical Study to Improve the Scientific Foundation of Forensic Firearm and Tool Mark  Utilizing 10 Consecutively Manufactured Slides* Fadul et al. (2011)

  - Synopsis/Contribution:

  - Limitations

- *Confocal microscopy analysis of breech face marks on fired cartridge cases from 10 consecutively manufactured pistol slides* Weller et al. (2012)

  - Synopsis/Contribution:

  - Limitations

- *A Fully Automatic Method for Comparing Cartridge Case Images* Tai and Eddy (2018)

  - Synopsis/Contribution:

  - Limitations

### Ballistics Papers

- *Automatic Matching of Bullet Land Impressions* Hare et al. (2017)

  - Synopsis/Contribution:

  - Limitations

- *Comparison of three similarity scores for bullet LEA matching* Vanderplas et al. (2020)

  - Synopsis/Contribution:

  - Limitations

- *NIST Ballistics Toolmark Research Database* Zheng et al. (2016)

  - Link: [https://www.nist.gov/publications/nist-ballistics-toolmark-research-database#:~:text=The%20NIST%20Ballistics%20Toolmark%20Research,Justice's%20National%20Institute%20of%20Justice.](https://www.nist.gov/publications/nist-ballistics-toolmark-research-database#:~:text=The%20NIST%20Ballistics%20Toolmark%20Research,Justice's%20National%20Institute%20of%20Justice.)

- *A Statistical Study of the Individual Characteristics of Fired Bullets* Biasotti (1959)

### Toolmark Papers

- *Validation of Tool Mark Comparisons Obtained Using a Quantitative, Comparative, Statistical Algorithm* Chumbley et al. (2010)

  - Synopsis/Contribution:

  - Limitations

- *An Improved Version of a Tool Mark Comparison Algorithm* Hadler and Morris (2017)

  - Synopsis/Contribution:

  - Limitations