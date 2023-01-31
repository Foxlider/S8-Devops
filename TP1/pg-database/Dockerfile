# Wer base our image on the basic postgres 14.1
FROM postgres:14.1-alpine

# we set up basic env variables
ENV POSTGRES_DB=db \
   POSTGRES_USER=usr

#We copy the sql files to the init folder
COPY scripts/01-CreateScheme.sql /docker-entrypoint-initdb.d
COPY scripts/02-InsertData.sql /docker-entrypoint-initdb.d