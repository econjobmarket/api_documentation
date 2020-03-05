## Php software for SOAP

To fetch your data, you can use some of the software available here. It is written in php, so you will need to be
 able to run php files from the command line. I know this isn't much help if you use windows of mac. 
 Hopefully I will have some software for these operating systems in the new year.

You can browse all the soap software if you want by visiting 
[https://montoya.econ.ubc.ca/econjobmarket_software/soap/](https://montoya.econ.ubc.ca/econjobmarket_software/soap/) 
the svn repository</a> for this stuff. The simplest way to get it is to use svn. svn client software is 
freely available for windows and mac. At the command line type

```
svn co https://montoya.econ.ubc.ca/econjobmarket_software/soap soap_software
```

That will create a subdirectory called soap_software that will contain a bunch of programs you can use. 
This software bundle uses the nusoap library which is contained in the subdirectory nusoap.  The programs available:

1. create_package.php - this will download all the database information for your organization to a directory on 
your computer. The data will be organized into various subdirectories. 
Once the download is complete you can browse all the information by opening the index.html file in the main directory. 
Running the program will transfer a large number of pdf files to your computer, so it will take a while 
and consume some bandwidth. To run the file do
```
php create-package.php
```
after you change the username, password and database settings in the file so that they match your 
organization's machine account.

1. ejm_setup_soap.php will set up a mysql database on your computer (you have to create the database on your local server). 
The program will create the tables necessary to run the download script that will fill the database with your data.

1. update_cron_soap.php - this will transfer the data for your organization into the database that you setup 
with ejm_setup_soap.php. This program is designed to update the database on a regular basis, 
so you can run it again when you want to refresh.
