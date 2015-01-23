#Suntans Instalation Guide
####This is the recommended way to install SUNTANS and necessary libraries for Ubuntu 14.04
### MPICH
* Download MPICH from http://www.mpich.org/downloads/
* Compile with gcc

OR

* Enter the following command:
 

    sudo apt-get install libcr-dev mpich2 mpich2-doc
    
### ParMetis
*  Download ParMetis 2.0 http://www.mpich.org/downloads/
*  Compile with mpicc (MPICH)

### HDF5
     sudo apt-get install libhdf5-mpich-dev

### NetCDF
* Download latest version of NetCDF http://www.unidata.ucar.edu/downloads/netcdf/current/index.jsp
* Unpack, go into the directory and execute:
 

    LDFLAGS=-L/usr/local/lib CPPFLAGS=-I/usr/local/include ./configure --enable-netcdf-4 --enable-dap --enable-shared --prefix=/usr/local
    make
    make install
    sudo ldconfig
    python setup.py install

### SUNTANS
    svn checkout svn://svn.code.sf.net/p/suntans/code/trunk suntans-code

* Make SUNTANS
* Run a SUNTANS Test
