# MASFit
MASFit (Milano Antineutrino Spectrum Fitter)

MASFit is a code intended to simulate the antineutrino spectrum that JUNO will receive and evaluate the sensitivity of the experiment with a CHI squared test. 
The code will produce a simulated spectrum and fit it with both normal and inverted models, computing the difference between the two CHI squared.

You can run the code "MASFit_1.py" with Python giving as input the file "input_MASFit_1.txt", "inputFlux.txt" and "bkg_geo_nu.txt".
Command line example: python3 MASFit_0.py input_MASFit_0.txt inputFlux.txt
The file "inputFlux.txt" contains the un-obscillated flux of anti-neutrinos from reactor. It has to have the same number of elements of the Nbin in the main code (you can set it from the input file).
The file "MASFit_func.py" is called in the main code and contains some of the funtions used.
The code will produce two different outputs: if you use an Asimov data-set (Fluctuations=0) the output will be a plot of the simulated data with the two fits (called "MASFit_plot.png")
and a file with all the free parameters of the fit and their reconsructed values (called "MASFit_parameters.txt").
If the option Fluctuations is True (1) it will produce an istogram with the distribution of the Delta Chi Squared, doing M fits.

This is an explanaion of the input file, in which you can control everything of the simulation (names and values as to be separated form "tab"):

- Fluctuations? if the answer is 0 it will produce an Asimov data-set, if the answer i 1 it will introduce stathistical fluctuation (Poisson) on the Asimov data-set
      and it will do multiple fit and produce a plot of the distribution of the chi squared.
- M  Number of fits you want to do with statystical fluctuations (1000 fits takes nearly 1 hour)

- Nbin	is the number of bin in which you divide the istogram (suggested 200)
- Emin(MeV)	is the lower energy for the simulation (don't go under 1.806)
- Emax(MeV)	is the maximun energy for the simulation
- Ncont	is the number of events you want to simulate (6y=100000, 20y=330000 etc..)
- Dist(km)	is the mean distance between the reactors and JUNO

The following entries are the phisical parameters for neutrino oscillation
- Sin2Theta12
- Sin2Theta13_NO
- Sin2Theta13_IO
- DeltaM21
- DeltaM31_NO
- DeltaM32_IO

The following lines are parameters for the energy resolution and the sistematic uncertainties
- a(%)	First term of the energy resolution (a/sqrt(E))
- b(%)	Second term of the energy resolution (the constant one)
- c(%)	Third therm in the energy resolution (c/E)
- sigma_a(%)	Uncertainties on the terms of the energy resolution
- sigma_b(%)	""
- sigma_c(%)	""
- sigma_alphaC(%)	Correlated reactor uncertainty
- sigma_alphaD(%)	Detector uncertainty
- sigma_b2b(%)	Bin to bin uncertainty
- sigma_alphaR(%)	Reactor uncorrelated uncertainty
- sigma_sh_B_vu(%) Systematic on background shape for geo-neutrini
- sigma_B_nu(%)  Systematic on background rate for geo-neutrini
- Systematics?	If the answer is 0 it will do a fit with the standard chi squared and some pull terms on a,b,c. If the answer is 1 it will use the chi squared with systematic.
- Scan?	If the answer is 1 it will produce a plot with the chi squared scan in function of Delta m^2(3l), otherwise nothing will be produced.

Here you have the possibility to chose which parameter of the fit are free anch which are fixed. If you put 0 the parameter will be free, if you put 1 it will be fixed
- Fix_M21
- Fix_M3l
- Fix_Theta13
- Fix_Theta12
- Fix_N
- Fix_a
- Fix_b
- Fix_c

The last option is if you want the plot to pop up, or just be saved
- Plot?	if the answer is 1 it will pop up and block the terminal until you have closed it, if it is 0 it won't appear, but will be saved anyways.
