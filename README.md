# Oracle XE 18c Rstudio dev environment

This project consists of two docker images: Oracle 18c Express Edition (free!), and rstudio with ROracle drivers preinstalled.

The Oracle DB image is simply copied from https://github.com/fuzziebrain/docker-oracle-xe

The rstudio image is based on the rocker/rstudio image, but with added drivers for oracle and the ROracle library.

Note that since Oracle likes to keep a close lid on their drivers etc, the builds require some relevant files to be located in the /files folders of each of the images. For the DB, this is mainly the actual install file (.rpm) which can be downloaded by anyone who has created an account on oracle.com, and for the rstudio image it is the drivers (.zip files). These too can be downloaded from the oracle website.
