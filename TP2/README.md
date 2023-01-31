# __TP 2__


## __testcontainers__
> 2-1 What are testcontainers?   

Temporary Containers that are used to run unitary tests, it is a `maven` based container that delete the old build and make a fresh one then run tests and return the results. 

## __Github Actions__
> 2-2 Document your Github Actions configurations.

### __CI__

We added a few lines to the default yml :  
It was missing `uses: actions/setup-java@v3`

### __CD__

`.github/workflows/docker.yml` commented


## __Quality Gate__

>Document your quality gate configuration.

On our quality gate we can see all sorts of things like bug vulneraibities or security hotspots. In our case we left the default configuration.We just added a token so the pipeline can push results.   
We have a few issues with the quality of the code because there is 2 code smells, 2 vunerabilites an 3 security hotspots.

# __Bonus__

## __Split CI/CD__

It's split up and working. 

We kept docker pipeline running on `dev` branch to make sure that the image would build correctly but they are not pushed to the repo until it's on `main` 