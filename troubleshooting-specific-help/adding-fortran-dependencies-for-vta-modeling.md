# Adding Fortran dependencies for VTA modeling

The FEM-based VTA model \(Horn et al. 2017\) needs Fortran dependencies since it uses the [SimBio toolbox](https://www.mrt.uni-jena.de/simbio/index.php/Main_Page) that is partially based on Fortran code.

## On a Mac

1. Open a Terminal
2. If you don't have home-brew installed, do so by typing

   `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

3. Install gcc by typing `brew install gcc`
4. Add a symbolic link between the file libgfortran.3.dylib to /usr/local/lib/ folder. You can do so by e.g. typing

   `ln /usr/local/Cellar/gcc@4.9/4.9.4/lib/gcc/4.9/libgfortran.3.dylib /usr/local/lib/libgfortran.3.dylib`

   into the Terminal. However, depending on the installation of your local gcc, folders might be a bit different in your case. 

## For Windows

Check if you have the "Intel\(R\) Visual Fortran Redistributables for Windows" installed on your system. Otherwise they can be found here: [https://software.intel.com/en-us/articles/redistributable-libraries-of-the-intel-c-and-fortran-compiler-for-windows/](https://software.intel.com/en-us/articles/redistributable-libraries-of-the-intel-c-and-fortran-compiler-for-windows/)

If you do not have them already you might also need "MicrosoftVisual c++ 2008 Redistributables" as well as a C++ compiler. In our experience the model works when you have c++ 2008 Redistributables version 9.0.30729.6161 and version 9.0.21022 installed. If you experience problems when trying to run the model we recommend to install these versions.

