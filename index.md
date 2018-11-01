
### Welcome to Git-hub page for This Project.

The Project allows user to extract Center channel using a source file specified by user. The code is written in MATLAB. 

## Requirements
MATLAB 2012 with signal Processing toolbox installed (Even Scilab can be used. But potentially you may run into heap issues as it allocates only 512 MB by default. I have tested it with Scilab 5.1 32 bit version & 64 bit Version.)
Please make sure that you mention input file path correctly and the file is compatible with wavread() function. Visit Matlab help page for compatibility.

## Algorithm
Transform the left and right channels to frequency domain using the Fast Fourier Transform (FFT)
For each frequency component, where L is the 2D vector from the left channel, and R is the 2D vector from the right channel:
* Compute C = L/|L| + R/|R|.
* Compute α such that (L-αC)∙(R-αC) = 0. Basically, scale C so that when it is subtracted from L and R, the two resultant vectors are perpendicular. Expanding the math gives the equation (C∙C)a2 - C∙(L+R)α + (L∙R) = 0, which can be solved for α by the quadratic formula.
* Compute C' = αC, L' = L-αC, and R' = R-αC.
* Transform L', R', and C' back to time domain.
* Overlap and add every quarter window (1024 samples).
// This is not my algorithm and I have just implemented it in Matlab.I am sorry, I do not remember from where I referred the algorithm. 

Current Issue is that It takes a lot of time to process (Hmmmmm go and grab a coffee till it finishes ) for a small file. I suggest you to use a small clip. There is lot of noise induced in the output file by using this method. solution may be simple but I do not have time to either update or test it. If anyone comes up with the solution can create pull request.
