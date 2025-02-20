# flowSpectrum
An R package to produce full spectrum flow cytometry plots outside the acquisition software.

**Author: Christopher Hall, Babraham Institute, UK**

[Babraham Institute Flow Cytometry Facility](https://www.babraham.ac.uk/science-services/flow-cytometry)

## Purpose
The purpose of this package is to produce full spectrum flow cytometry plots outside the acquisition software.
There are three styles designed to roughly mimic the output styles of the Bigfoot, Aurora, and R Viridis.
The package takes flowFrames and flowSets as produced using the flowCore package.
* flowSpectrum wiil not work with the Sony SP6800 as it uses a proprietary format that flowCore can't read.

## Usage
### Quick start

```spectralplot(ff)```

### More information

Load data into R using flowCore either via read.FCS() or read.flowSet(),

Use the spectralplot() function, choose a style, and choose where to output the resulting image.  The default (i.e. just ```spectralplot(ff)```) will produce a viridis plot in the R session.

```{r setup, out.width="100%"}
#install from Github using devtools (or remotes)
devtools::install_github('hally166/flowSpectrum')

#load the package
library(flowSpectrum)

#flowSpectrum has one demo file that can be loaded.  
ff<-read.FCS(system.file("extdata", "PE.fcs", package = "flowSpectrum"))

#create plots using spectralplot(). spectralpolt() will accept a flowFrame or a flowSet
spectralplot(ff, theme='viridis', save=FALSE, bins=512, normalize=FALSE, params=NULL)
```
![PE spectrum](/man/pe.png)

![PE normalized spectrum](/man/PE_normalized.png)


The theme options are 'viridis', 'bigfoot', and 'aurora'.

The save options are TRUE and FALSE.  TRUE will save a PNG into the working directory. FALSE will output to the R session.

Set then granularity of the plot using ```bins =``` [a number].  I use something between 256 and 512.

```Normalize = TRUE``` will produce a normalized spectrum based on the max median intensity. 

Specify which parameters to plot (in the order specified) using ```params =``` [a character vector of parameter names].

Defaults are: ```theme='viridis', save=FALSE, bins=512, normalize=FALSE, params=NULL```
