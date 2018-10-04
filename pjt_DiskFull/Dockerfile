FROM r-base:latest

# Basic Utils for Image Setup  -----------------------------------

RUN apt-get update -y
RUN apt-get install -y libssl-dev
RUN apt-get install -y libxml2-dev
RUN apt-get install -y libmariadbclient-dev
RUN apt-get install -y libcurl4-openssl-dev


# Directory Setup  -----------------------------------

WORKDIR /home
RUN chmod o+w /usr/local/lib/R/site-library


# Package Setup for Docker Image  -----------------------------------

COPY docker_image_setup.R /home
RUN Rscript docker_image_setup.R

RUN mkdir log              
ARG CACHEBUST=1


# Run Main R Script -----------------------------------

COPY . /home
CMD Rscript main.R
