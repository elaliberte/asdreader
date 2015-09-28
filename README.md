[![Travis-CI Build Status](https://travis-ci.org/pierreroudier/asdreader.svg?branch=master)](https://travis-ci.org/pierreroudier/asdreader)
[![CRAN_Status_Badge](http://www.r-pkg.org/badges/version/asdreader)](http://cran.r-project.org/web/packages/asdreader)
[![Total_Downloads](http://cranlogs.r-pkg.org/badges/grand-total/asdreader)](http://cran.r-project.org/web/packages/asdreader)

# asdreader

Reading ASD Binary Files in R

## Scope

This package implements a simple reader for spectroscopy data collected using ASD (now PAN Analytics, Inc.) visible near-infrared spectrometers, and stored using the ASD format (which is documented [here](http://support.asdi.com/Document/Viewer.aspx?id=95)).

The spectra can be extracted from the ASD file as raw (DN),
white reference, radiance, or reflectance. Additionally, the metadata information contained 
in the ASD file header can also be accessed.

## Installation

It's easiest to use the `devtools` package to install `asdreader`:

`devtools::install_github("pierreroudier/asdreader")`

I haven't come around to submit this on CRAN yet.

## Use

The main function is `get_spectra`. It takes one (or more) paths to `*.asd` files and returns a matrix of spectra. The other potentially useful function is `get_metadata`, which returns the contents of the header of a a given `*.asd` file.

A sample `*.asd` file is included for testing/examples purposes. The path to this sample file can be access using the shorthand function `asd_file()`. 

```
fn <- asd_file()
s <- get_spectra(fn)
plot(as.numeric(s), type = 'l')
```

or, for the pipe *afficionados*:

```
library(magrittr)
asd_file() %>% 
  get_spectra %>% 
  as.numeric %>% 
  plot(type = 'l')
```

This package has been developed working on `*.asd` files in version 8 (that's my setup), along with some of the documentation that can be found online. In particular, reading code from @serbinsh ([here](https://github.com/serbinsh/R-FieldSpectra)) and @antoinestevens ([here](https://github.com/antoinestevens/prospectr)) proved to be helpful.

I'm sure this thing could probably become better with help from people with different setups/file format versions --- contributions welcome!
