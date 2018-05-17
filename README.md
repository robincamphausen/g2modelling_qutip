# g2modelling_qutip
## proper way to calculate pulsed g2
------------------------------------

g2_by_autocorrelation is the Jupyter notebook that calculates the pulsed g2 from first principle:
- initialises a train of exponential decay pulses
- cross-correlates a single exponential pulse with the pulsetrain
  (this is analogous to adjusting delay on one of the HBT interferometer arms)
- for tau != 0 (tau is Xcorr delay), the crosscorrelation is classical as these pulses originate from different laser excitations
- for tau = 0 the value of the crosscorrelation is given by the photon number representation of g2
  (this can be confirmed with the QuTiP package)
  
- to fit decay parameter to experimental data simply take autocorrelation of single pulse with itself
- plot all of the tau != 0 peaks from experimental coincidences data, and fit


g2_modelling_copiedCode just pastes together a bunch of code mainly from
  http://nbviewer.jupyter.org/github/qutip/qutip-notebooks/blob/master/examples/pulse-wise-second-order-coherence-g2.ipynb
  
hBN_g2modelling is an attempt to calculate g2 using QuTiP package, but note:
- mesolver is unstable with multiple excitation pulses
- mesolver is unstable depending on tau offset (i.e. if "real" zero tau is set to something else)
- therefore more straightforward to only use QuTiP to calculate correlation value for tau = 0 peak, and classical Xcorr for the rest
