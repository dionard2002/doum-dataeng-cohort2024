## Writing the Dockerfile
Now that we are done with our pre-requisites. Let us now proceed to writing a dockerfile ourselves. 

First let us create a new folder inside our week-1 directory, name it "docker-sql".

1. Create ```Dockerfile``` inside directory:
```
FROM python:3.9.1

RUN pip install pandas

ENTRYPOINT ["bash"]
```

2. Let's try building it. 
```
docker build -t test:pandas .
```

3. After it has finished building, now we can run our file.
```
docker run -it test:pandas
```
Then let's run python in our bash.
- Once successfully ran, you may then import pandas and check its version ```pandas.__version__```.

## Once image has been successfully created, let us now create our pipeline
