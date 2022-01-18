# cartridgeCaseLitReview
Lit review for cartridge case comparison algorithms


## Important Papers

### CMC Papers

- Song (2013) *Proposed “NIST Ballistics Identification System (NBIS)” Based on 3D Topography Measurements on Correlation Cells*

  - Synopsis: Introduces the concept of *correlation areas* and proposes using the comparison of *correlation cells* to estimate the registration phase (translation) and angle of two cartridge cases. The "Contiguous Matching Cells" Method is discussed to quantify the similarity between two cartridge cases.

  - Limitations: There are few details provided in this paper in how the method should actually be implemented, although discussion of an actual implementation was not the focus of this paper. The various thresholds discussed in the paper (e.g., section 4) is based without much justification on the Consecutive Matching Striae paper.

  - Contribution: Provides a conceptual description of the overall CMC pipeline and some hints at how to actually implement the pipeline.

- Chu et al. (2013) *Validation Tests for the Congruent Matching Cells (CMC) Method Using Cartridge Cases Fired with Consecutively Manufactured Pistol Slides*

  - Synopsis: Shares summative results from an implementation of the CMC method as detailed in Song (2013). Using a set of 40 3D topographical scans of cartridge cases from Fadul (2011), describes some of the parameters used to preprocess and compare the cartridge case scans. Their results show that using a CMC count threshold of 6, the CMC count similarity score correctly distinguishes between the matching and non-matching comparisons from this data set.

  - Limitations: There is ambiguity in precisely what parameters and methods were used to perform the comparisons. For example, it appears that grids of 7x7 and 6x6 were both used to compare scans "depending on the actual size of different correlation areas" which the authors do not describe further. In terms of the CMC method performance, there is not much separation between the matching and non-matching CMC count distributions.

  - Contribution: Demonstrates that a particular implementation of the CMC method works on the Fadul cartridge case comparisons.

- Song et al. (2014) *3D topography measurements on correlation cells—a new approach to forensic ballistics identifications*

  - Synopsis: Similar to Chu et al. (2013), applies the CMC method to the 40 scans from Fadul (2011). It appears that some additional preprocessing steps were added to the pipeline outlined in Chu et al. (2013) including applying a band-pass Gaussian filter and "identify[ing] and remov[ing] dropouts and outliers."

  - Limitations: There are additional ambiguities introduced in this paper including what algorithm was used to apply the Gaussian filter, what "dropouts" are in the scans, how the authors define "outliers," and what it means to "remove" these dropouts and outliers.

  - Contributions: Some of the parameters (e.g., the Gaussian bandpass filter wavelength cutoffs) are provided in greater detail. Figure 6 of this article is the exact same as Figure 4(b) in Chu et al. (2013), so it is unclear if the pipeline additions detailed in this paper weren't already in-use in Chu et al. (2013).

- Tong et al. (2014) *Fired Cartridge Case Identification Using Optical Images and the Congruent Matching Cells (CMC) Method*

  - Synopsis: Applies the CMC method to 2D images of the Fadul (2011) cartridge cases. The results (Figure 7(b)) show that, compared to the 3D scans (Song et al. (2014)), when applied to 2D images the CMC method assigns higher CMC scores to non-match comparisons and lower CMC scores to match comparisons.

  - Limitations: Many of the same ambiguities that were in the previous CMC papers are also in this paper. The authors do, however, specify that a grid of 7x7 was used for all scans rather than 7x7 or 6x6.

  - Contributions: This paper does indicate that a "training" set of 20 scans (out of 40 scans) was used to identify the optimal CMC method thresholds $(T_x,T_y,T_{CCF},T_{\theta})$. In particular, amongst a grid of thresholds, the thresholds that result in the largest distance between the largest non-match CMC count and the smallest match CMC count are selected as optimal. Figure 7(b) shows the CMC count distributions for all 40 scans instead of just the 20 hold-out scans not used in the training.

- Tong et al. (2015) *An Improved Algorithm of Congruent Matching Cells (CMC) Method for Firearm Evidence Identifications*

  - Synopsis: Introduces the first "improvement" upon the original CMC method discussed in Song (2013). In subsequent papers, this improved method came to be called the "High CMC" method. The results indicate that the High CMC method yields greater separation in the matching and non-matching CMC count distributions for the comparisons of both the Fadul (2011) 3D scans and 2D images.

  - Limitations: There are ambiguities in how the High CMC method actually works in this paper. In particular, there are multiple readings of the procedure outlined on pages 109 and 110 that yield different versions of the algorithm.

  - Contribution: As the original method CMC count is the lower-bound of the High CMC count, it is indeed an improvement upon the original CMC method of Song (2013).

- Song (2015) *Proposed “Congruent Matching Cells (CMC)” Method for Ballistic Identification and Error Rate Estimation*

  - Synopsis: Song's follow-up to the 2013 paper. This paper was submitted soon after Song (2013) and wasn't published until 2015. This paper emphasizes more how the CMC method should be validated by calculating the false positive/negative error rates. The Discussion/Conclusion alludes the calculation of likelihood ratios using the CMC count distributions.

  - Limitations: Similar to Song (2013), there are few details in this paper on how to actually implement the CMC method. Song (2013) and this paper are much like the "methods" section of a paper while the "results" section is provided in the form of Chu et al. (2013), Song et al. (2014), and Tong et al. (2014).

  - Contribution: This paper adds to the contributions of Song (2013) by detailing the calculation of false positive and false negative error rates as a validation procedure. This paper also coins the *Congruent* Matching Cells as opposed to the "Contiguous" Matching Cells originally proposed in Song (2013).

- Zhang et al. (2016) *Correlation of firing pin impressions based on congruent matching cross-sections (CMX) method*

  - Synopsis: Introduces a CMC-like procedure to be used on 3D scans of firing pins. The base CMX method yields relatively large CMX counts for both the match and non-match comparisons when applied to the Fadul (2011) firing pin scans (Figure 11), although there is perfect separation. The separation between the matching and non-matching CMX count distributions is improved by averaging the 2 largest CMX scores across different rotations (what they call CMX' - Figure 12).

  - Limitations: Again, there are ambiguities in precisely how the method's sub-routimes is implemented (Figure 9 diagram).

  - Contribution: This is the first application of a CMC-like procedure to firing pin scans.

- Ott et al. (2017) *Applying 3D measurements and computer matching algorithms to two firearm examination proficiency tests*

  - Synopsis: Applies the CMC method to new cartridge case and firing pin scans that had previously been used in firearm examiner proficiency tests. The results (Figures 7 and 8) indicate that the CMC and CMX method separate these matching and non-matching comparisons well compared to results in Chu et al. (2013), Song et al. (2014), Tong et al. (2014) indicating a dependency on the data used. Additionally, the authors propose using the sum of the CMC and CMX scores for a particular comparison as its final similarity score.

  - Limitations: The authors point out that the CMC/CMX methods do not perform well when there are large anomalous regions in a scan (Figure 7 - thin bars). None of the implementation ambiguities from the previous papers are clarified here.

  - Contribution: This is a good validation study of the CMC and CMX methods. This was also the first observed use of the CMC plots (Figure 5).

- Chen et al. (2017) *A convergence algorithm for correlation of breech face images based on the congruent matching cells (CMC) method*

  - Synopsis: Introduces the next improvement upon the original CMC method of Song (2013) after Tong et al. (2015) referred to as the "Convergence CMC" method. Additionally, 3 new data sets (Weller (2012), La Porte (2011), and Lightstone (2010)) are used to validate the results. The results indicate that the convergence CMC method assigns smaller CMC scores to non-matching comparison comparable CMC scores to matching comparisons compared to the High CMC method.

  - Limitations: This method adds additional ambiguity in sub-routine implementation (e.g., second order robust Gaussian regression filter). Additionally, while I have implemented this procedure, I have yet to observe results comparable to the results shown in this paper for the Convergence CMC method. 

  - Contribution: This Convergence CMC method seems to be the current favorite amongst the NIST researchers and indeed tends to perform better than the previously proposed method.

- Song et al. (2018) *Estimating error rates for firearm evidence identifications in forensic science*

  - Synopsis: Shares results from implementing the error rate estimation procedure outlined in Song (2015) with some additional contributions. In particular, a binomial model is assumed for all non-matching comparisons while a beta-binomial model (mixing over comparisons) is assumed for all matching comparisons. They calculate the posterior probability of a false positive and false negative to be $1.8 \cdot 10^{-17}$ and $2.2 \cdot 10^{-4}$, respectively, using CMC count decision boundary of 10 CMCs.

  - Limitations: They assume independence between individual cells and across comparisons. They point out the dependence across comparisons due to re-using the same cartridge case scan to calculate multiple CMC scores. Their proposed solution to this is briefly discussed in Appendix B as a model that captures second-order correlation between individual *cells* that make up a single CMC count. Appendix C briefly discusses an alternative to the between-comparison dependence due to scan re-use in which a new data set is constructed whereby each scan is only to calculate a single CMC score. They resample such a data set 100,000 times and estimate the success probability for each data set - finding that the average of these success probabilities is similar to that of the between-comparison dependent success probability.

  - Contribution: This is the first time that an actual model is proposed for the CMC count distributions. Song et al. (2020) builds upon this paper by calculating likelihood ratio estimates.

- Tong et al. (2018) *Valid data based normalized cross-correlation (VDNCC) for topography identification*

  - Synopsis: Proposes a novel way to calculate a cross correlation (the "valid data based normlaized cross-correlation") between a reference cell and target region using only the "valid" data points (i.e., the non-missing matrix values). In particular, missing values are replaced with 0 in both the reference cell and target region before the cross-correlation is calculated - creating so-called "valid data templates."" The authors then show that the standard cross-correlation formula using these valid data templates can be re-written in such a way to speed up computation and avoid actually calculating the correlation at every translation of the reference cell against the target region. When applied to the Fadul and Weller scans, results indicate that the matching and non-matching VDNCC values are more separated than the standard NCC values, although the final CMC results do not appear to be drastically affected.

  - Limitations: The results indicate that this VDNCC method doesn't affect the  final CMC results compared to a standard NCC. It also seems like the VDNCC takes a much longer time than simply using an FFT to calculate the cross-correlation.

  - Contribution: This is the first paper that explicitly deals with missing values, which was an issue that we spent a good deal of time on early on in our exploration of the CMC method. While this doesn't seem to be a particularly impactful contribution to the CMC method, it is good to know that NIST/other researchers were dealing with the same problems.

- Chen et al. (2018) *A normalized congruent matching area method for the correlation of breech face impression images*

  - Synopsis: Rather than using the number of CMCs as a similarity score, this paper proposes using the proportion of a breech face classified as "congruent" as the similarity score - what they refer to as the "normalized congruent matching area." The results indicate that there isn't a large difference in the separation of the matching and non-matching CMC and NCMA distributions. The authors also discuss the selection of the "best" cell size by comparing the NCMA values for the matching comparisons. Their results show that the matching NCMA values are fairly stable between 8x8 to 12x12 cell grids, yet are variable for cell grids smaller than 8x8 and fall quickly for grids larger than 12x12.

  - Limitations: The authors use a binomial/beta-binomial model for the proportion of the breech faces that are classified as congruent - associating independent Bernoulli trials with the congruent/non-congruent status of each pixel in a surface matrix. It seems to me that a beta model would be much more appropriate for these proportions.

  - Contribution: Intuitively, I think that the proportion of a breech face classified as congruent is a more intuitive measure of similarity than the number of CMCs. Additionally, this is the first reference to actually selecting parameters of the CMC algorithms based on some criterion - namely, the stability of the matching NCMA values.

- Zhang (2019) *The Use of Correlated Binomial Distribution in Estimating Error Rates for Firearm Evidence Identification*

  - Synopsis: Proposes using a correlated (Bahadur-Lazarsfeld) binomial model for the CMC counts. This model incorporates assumes dependence between individual cells and models the first-order (pairwise) dependence. The authors propose estimating the success probability and the pairwise correlation parameter using both MLE and nonlinear regression (Levenberg-Marquardt nonlinear LS algorithm).

  - Limitations: The proposed model only incorporates pairwise dependence between cells. Other models could incorporate higher-order dependence. Additionally, the proposed model assumes that the correlation is the same across all matching/non-matching comparisons rather than incorporating a repeated measure effect across individual scans.

  - Contribution: This was the first paper that proposed modeling any sort of dependency between between individual cells.

- Song et al. (2020) *Evaluating Likelihood Ratio (LR) for firearm evidence identifications in forensic science based on the Congruent Matching Cells (CMC) method*

  - Synopsis: Using the binomial/beta-binomial CMC distribution models proposed previously, this paper discusses how to estimate score-based likelihood ratios (they don't make the distinction between LRs/SLRs).

  - Limitations: As discussed previously, the assumption of independence made by the binomial/beta-binomial models is not met in this case.

  - Contribution: This paper shows results from applying the SLR estimation procedure outlined in Song (2015) to Fadul data set.

- Zhang et al. (2020) *Convergence-improved congruent matching cells (CMC) method for firing pin impression comparison*

  - Synopsis: (Note: different Zhang than NIST's Zhang) The authors propose using the DBSCAN (density-based clustering with applications to noise) algorithm for matching firing pin impressions using the (x,y,CCF) data calculated from the CMC cell-based comparison procedure. To initially align the two scans, the authors propose using the CMC algorithm to get an initial estimated registration and then use a pixel-wise least-squares matching procedure to "deform" one scan to the other.

  - Limitations: The authors propose (as I understand it) calling a pair a match if the DBSCAN algorithm identifies *any* cluster in the (x,y) values. I would think that we could have a more nuanced decision rule that, for example, calls any points classified into a cluster a "CMC" and define a match decision boundary based on a minimum number of CMCs.

  - Contribution: This density-based approach seems to be what the original CMC algorithms are *trying* to do. Early empirical evidence suggests that the DBSCAN procedure performs much better than the CMC method (based on TopMatch comparisons).

- Zhang (2021) *Statistical models for firearm and tool mark image comparisons based on the congruent matching cells (CMC) method*

  - Synopsis: This paper seems to summarize the various models that have been proposed by NIST for the CMC count distributions. Their conclusion is that the beta-correlated binomial, correlated binomial, and beta-binomial distributions fit the matching CMC count distributions better than a simply binomial model. The binomial model does appear to fit the non-matchg CMC count distribution sufficiently, although a goodness/lack-of-fit test is not performed.

  - Limitations: There does not appear to be any newly proposed methodology in this paper. The limitations discussed for Song et al. (2018), Song et al. (2020), and Zhang (2020) all apply here.

  - Contribution: The main contribution seems to be a side-by-side comparison of the different models to the Weller data set.

### Cartridge Case Papers

- Md Ghani et al. (2010) *Analysis of geometric moments as features for firearm identification*

  - Synopsis:

  - Limitations:

  - Contribution:  

- Fadul et al. (2011) *An Empirical Study to Improve the Scientific Foundation of Forensic Firearm and Tool Mark  Utilizing 10 Consecutively Manufactured Slides*

  - Synopsis:

  - Limitations:

  - Contribution: For our purposes, the biggest contribution from this study is the set of cartridge cases that we commonly use to test the CMC method.

- Weller et al. (2012) *Confocal microscopy analysis of breech face marks on fired cartridge cases from 10 consecutively manufactured pistol slides*

  - Synopsis/Contribution:

  - Limitations

- Gerules et al. (2013) *A survey of image processing techniques and statistics for ballistic specimens in forensic science*

  - Synopsis:

  - Limitations:

  - Contribution:

- Riva and Champod (2014) *Automatic Comparison and Evaluation of Impressions Left by a Firearm on Fired Cartridge Cases*

  - Synopsis:

  - Limitations:

  - Contribution:

- Roth et al. (2015) *Learning-based Ballistic Breech Face Impression Image Matching*

  - Synopsis

  - Limitations

  - Contribution

- Riva et al. (2016) *Objective Evaluation of Subclass Characteristics on Breech Face Marks*

  - Synopsis

  - Limitations

  - Contribution

- Tai and Eddy (2017) Forensic Data Matching Problems

  - Synopsis

  - Limitations

  - Contribution

- Tai and Eddy (2018) *A Fully Automatic Method for Comparing Cartridge Case Images*

  - Synopsis/Contribution:

  - Limitations

- Tai (2019) *Record Linkage and Matching Problems in Forensics*

  - Synopsis

  - Limitations

  - Contributions

- Riva et al. (2020) *Comparison and interpretation of impressed marks left by a firearm on cartridge cases – Towards an operational implementation of a likelihood ratio based technique*

  - Synopsis

  - Limitations

  - Contributions

### Ballistics Papers

- Biasotti (1959) *A Statistical Study of the Individual Characteristics of Fired Bullets*

- Zheng et al. (2016) *NIST Ballistics Toolmark Research Database*

  - Link: [https://www.nist.gov/publications/nist-ballistics-toolmark-research-database#:~:text=The%20NIST%20Ballistics%20Toolmark%20Research,Justice's%20National%20Institute%20of%20Justice.](https://www.nist.gov/publications/nist-ballistics-toolmark-research-database#:~:text=The%20NIST%20Ballistics%20Toolmark%20Research,Justice's%20National%20Institute%20of%20Justice.)

- Hare et al. (2017) *Automatic Matching of Bullet Land Impressions*

  - Synopsis/Contribution:

  - Limitations

- Vanderplas et al. (2020) *Comparison of three similarity scores for bullet LEA matching*

  - Synopsis/Contribution:

  - Limitations


### Toolmark Papers

- Chumbley et al. (2010) *Validation of Tool Mark Comparisons Obtained Using a Quantitative, Comparative, Statistical Algorithm*

  - Synopsis/Contribution:

  - Limitations

- Hadler and Morris (2017) *An Improved Version of a Tool Mark Comparison Algorithm*

  - Synopsis/Contribution:

  - Limitations