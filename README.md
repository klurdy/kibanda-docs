# Kibanda Finda Documentation
This repo is for building documentation for Kibanda Finda using Slate tools. Clone this repo and make sure you have docker installed in your development machine.

First, pull the required docker image

`docker pull slatedocs/slate`

To run the documentation website, run this docker command from the root folder of the project

`docker run --rm --name slate -p 4567:4567 -v $pwd/source:/srv/slate/source slatedocs/slate serve`

Access the docs in this [url](http://localhost:4567)

To build the documentation, run this docker command from the root folder of the project

`docker run --rm --name slate -v $pwd/build:/srv/slate/build -v $pwd/source:/srv/slate/source slatedocs/slate build`

The html files for the documentation will be located in the `build` folder.

To learn more about slate documentation, visit ths [url](https://github.com/slatedocs/slate/wiki/)



