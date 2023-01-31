# __TP 2__


## __testcontainers__
> 2-1 What are testcontainers?   

Temporary Containers that are used for testing purposes

## __CI__

We added a few lines to the default yml :
It was missing `uses: actions/setup-java@v3`   # Using latest setup java from their repo`

## __CD__

`.github/workflows/docker.yml` commented

## __Split CI/CD__

It's split up and working. 

We kept docker pipeline running on `dev` branch to make sure that the image would build correctly but they are not pushed to the repo until it's on `main` 