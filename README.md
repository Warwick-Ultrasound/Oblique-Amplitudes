# Oblique-Amplitudes

A simple set of functions for calculating the complex transmission reflection coefficients for oblique incidence at a material boundary. 

The calculation that is performed is dependent on whether the materials are liquids or solids, and what the boundary conditions are between the two interfaces. If one of the media is a liquid, it is assumed that the boundary is described by a rigid condition and the maths is as described in J L Rose "Ultrasonic Guided Waves in Solid Media". For the solid-solid case, two boundary conditions are possible, depending on how the surfaces are mated to eachother. Of a liquid such as water is used, the two boundaries can 'slip' over one another, no motion is transmitted parallel to the boundary, and the mathematics is described by G. J. Kuhn and A. Lutsch “Elastic Wave Mode Conversion at a Solid-Solid Boundary with Transverse Slip". If the materials are rigidly bonded e.g. with a thin layer of solid epoxy, then the mathematics follows that in Rose.

The first letter of the function name indicates the incidence medium (S = solid, L = liquid), and the second indicates the medium the wave is transmitted into.

Each function takes as inputs:

- m1: material structure (incidence medium, defined below)
- m2: material structure (transmission medium)
- theta0: incidence angle measured from the surface normal (degrees)
- f: the frequency of the wave
- inType: a character "L" or "S" for longitudinal or shear incidence respectively

The material structs must contain fields (all in SI units):

- clong: longitudinal speed
- cshear: shear speed
- G: shear modulus
- rho: mass density

The outputs are:

- A: Array of complex amplitudes, assuming incidence amplitude is 1, in the form [RL, RS, TL, TS] where R = reflected, T = transmitted, L = longitudinal, S = shear. 
- theta: Array of angles of reflection/transmission obtained from Snell's law, in the same order as A.

Where one of the media is a liquid, the amplitude and angle for the shear wave in that medium is omitted and the order remains the same. The complex amplitude can be interpreted as a change in both the maplitude and phase of the wave. The factor by which the amplitude changes can be obtained with abs(A) and the phase angle change with angle(A).
