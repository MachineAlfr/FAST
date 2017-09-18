# FAST
FAST (Fitting and Assessment of Synthetic Templates) is an IDL-based code that fits stellar population synthesis templates to broadband photometry and/or spectra. FAST is compatible with the photometric redshift code [EAzY](http://www.astro.yale.edu/eazy/) ([Brammer et al. 2008](http://adsabs.harvard.edu/abs/2008arXiv0807.1533B)) when fitting broadband photometry; it uses the photometric redshifts derived by EAzY, and the input files (photometric catalog, master filter file etc.) are the same. FAST also fits spectra, optionally in combination with broadband photometric data points. There is also now the option to simulataneously fit two components, allowing for an AGN contribution in addition to the host galaxy light. Depending on the input parameters, FAST outputs the best-fit redshift, age, dust content, star formation timescale, metallicity, stellar mass, star formation rate (SFR), and their confidence intervals. The main difference with [HYPERZ](http://webast.ast.obs-mip.fr/hyperz/) is that (1) FAST fits fluxes instead of magnitudes, (2) you can completely define your own grid of input stellar population parameters, (3) you can easily input photometric redshifts and their confidence intervals, and (4) FAST calculates calibrated confidence intervals for all parameters. However, note that, although it can be used as one, FAST is not a photometric redshift code 

# How does FAST work? 
FAST reads in a parameter file (see example), and makes a cube of model fluxes for the full stellar population grid, and all filters and/or spectral elements. To determine the best-fit parameters, it simply uses χ2 fitting. To avoid skipping over (multiple) minimums, FAST uses no minimum searching algorithm, but fits every point of the model cube. In case spectroscopic or photometric redshifts are provided, the redshift will be fixed to the closest value in the grid. 
The confidence levels are calibrated using Monte Carlo simulations. The observed fluxes are modified according to their photometric errors, and these modified fluxes are fitted as well. The 68% (95% or 99%) confidence intervals are defined by the χ2 value in the original grid that encloses 68% (95% or 99%) of these simulations. Thus, the confidence intervals on all properties are the minimum and maximum values allowed by this χ2 threshold. In case photometric redshifts (as provided by EAzY) are assumed, the calculation of the confidence intervals is bit more complicated. In the Appendix of Kriek et al. (2009) you can find more about this issue. 

# Download and using FAST
The most recent version is now available on [github](https://github.com/jamesaird/FAST).  
(The 
[ised_del.lr](http://pepper.astro.berkeley.edu/~mariska/FAST_Libraries/ised_del.lr.tar.gz), 
[ised_del.hr](http://pepper.astro.berkeley.edu/~mariska/FAST_Libraries/ised_del.hr.tar.gz), 
[ised_tru.hr](http://pepper.astro.berkeley.edu/~mariska/FAST_Libraries/ised_tru.hr.tar.gz), 
and 
[ised_exp.hr](http://pepper.astro.berkeley.edu/~mariska/FAST_Libraries/ised_exp.hr.tar.gz)
libraries have to be downloaded separately).

If you use the code, please cite the following paper (the description of the code can be found in the Appendix):  
[Kriek et al. (2009)](http://adsabs.harvard.edu/abs/2009ApJ...700..221K)

For recent updates, see also:  
[Aird et al. 2017a](http://adsabs.harvard.edu/abs/2017MNRAS.465.3390A) (appendix describes averaging over templates and redshift-dependent minimum age)
[Aird et al. 2017b](http://adsabs.harvard.edu/abs/2017MNRAS.465.3390A) (appendix describes two-component fitting for AGN+galaxy)  Please also cite these papers if you use these features.

Any questions and remarks are welcome, but please first check the documentation in the parameter file and the FAQ page.

Finally, please always check the output files. Does the fit look okay? Is the output redshift indeed similar to the input redshift, etc. While we tested FAST exhaustively, there might still be bugs. Please email if you do find any or wish to contribute to the project. Note that the use of FAST is at your own risk!
