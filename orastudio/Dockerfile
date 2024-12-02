FROM rocker/rstudio-stable:latest 
## Work-around to make Docker Hub use the Dockerfile 
## from https://github.com/rocker-org/rocker-versioned/tree/master/rstudio 

LABEL MAINTAINER="radbrt <hho@cerx.co>"

ENV \
    INSTACLI=instantclient-basic-linux.x64-19.24.0.0.0dbru.zip \
#    INSTACLI_ODBC=instantclient-odbc-linux.x64-18.3.0.0.0dbru.zip \
    INSTACLI_SDK=instantclient-sdk-linux.x64-19.24.0.0.0dbru.zip \
    # INSTACLI_SQLPLUS=instantclient-sqlplus-linux.x64-18.3.0.0.0dbru.zip \
#    JARFILE=ojdbc8.jar \
    RORAPATH=ROracle_1.3-1.tar.gz \
    LD_LIBRARY_PATH=/instantclient_19_24

COPY ./files/${INSTACLI} /home/rstudio/${INSTACLI}
COPY ./files/${INSTACLI_SDK} /home/rstudio/${INSTACLI_SDK}
# COPY ./files/${INSTACLI_SQLPLUS} /home/rstudio/${INSTACLI_SQLPLUS}
COPY ./files/${RORAPATH} /home/rstudio/${RORAPATH}

# RUN apt-get update && apt-get install -y libaio1

RUN unzip /home/rstudio/${INSTACLI} && \
    unzip /home/rstudio/${INSTACLI_SDK}

# RUN unzip /home/rstudio/${INSTACLI} && \
#     unzip /home/rstudio/${INSTACLI_SDK} && \
#     unzip /home/rstudio/${INSTACLI_SQLPLUS}

RUN Rscript -e "install.packages(c('DBI', 'tidyverse', 'ROracle'))"

# RUN R CMD INSTALL --configure-args='--with-oci-lib=/instantclient_19_24 --with-oci-inc=/instantclient_19_24/sdk/include' /home/rstudio/${RORAPATH}

EXPOSE 1521
