# Jupyter Notebooks
Jupyter Notebooks are open-source web applications that allows you to create and share documents that contain live code, equations, visualizations and narrative text. Used by data scientists and those wishing to prototype various data cleaning transformation, numerical simulation, statistical modeling, data visualization and machine learning activities.  Juypter supports Python, R and F#. There are several notebooks below that you can clone and experiment with.

There are thousands of tool/packages that can be used. The core tech used in these notebooks is:

+ Ubuntu Linux
+ Miniconda, a small version of the Anaconda package manager for a Python/R data science distribution
+ Python 3
+ Apache Tika, text extracts from files
+ SpaCy, an industrial stength natural language processing (NLP) library
+ tesseract and pytesseract, a popular OCR library and Python wrapper for it
+ Pillow, an imaging library
+ LibROSA, music and audio analysis
+ Matplotlib, a 2D plotting library
+ SpeechRecognition, supports several speech detection APIs
+ Google Speech Recognition API

### Uses

Apart from running interactive data science experiments the results can be published.  You can calculate/run an entire notebook non-interactively and save the results in a variety of formats such as HTML, PDF etc.  This make notebooks a useful tool in reporting schedules and even ETL workflows.  There are even packages that create interactive dashboards for a richer use experience. 

### Set-up

TL;DR Azure Notebooks and online examples are no more use Anaconda, the latest version of Visual Studio Code or even Kaggle https://www.kaggle.com

The easiest way to get started with Juypter is to use the Anaconda platform or a Docker image. See https://www.anaconda.com/ and https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html   There are several Docker images each with different libraries pre loaded.  

Tips for Docker use (Linux example, Windows commands will be similar) 

    - docker pull jupyter/datascience-notebook:latest
    - docker run --name jupyter -e GRANT_SUDO=yes --user root -it --rm -p 8888:8888 -p 4040:4040 -v ~:/home/jovyan/workspace jupyter/datascience-notebook:latest
    - Use the URL output from the docker run command 
    
Important: In development mode you can add the following flags to docker run command to run with elevated permissions. _-e GRANT_SUDO=yes --user root_ this is needed in you need to install additional software and update the container image.
  
Java is needed to support Apache Tika which we use in the text mining example. The docker image we are using did not have Java installed but the Azure Notebook service did. Here is the easiest way to install Java to the container. Take a look at the terminal where you run the container from. It should tell you where the container is running. E.g. http://204cb5712627:8888 We need the first four digits, 204c from this. Replace this with the value you have.

    - docker exec it 204c bash
    - sudo apt update
    - sudo apt install default-jdk
    - exit
    - docker commit <container id> jupyter
    - docker images
 
You should see a new image called Jupyter and the original. The container id can be found by issues a docker ps command. Stop running the current docker container and run the new one.

    - docker run --name jupyter -e GRANT_SUDO=yes --user root -it --rm -p 8888:8888 -p 4040:4040 -v ~:/home/jovyan/workspace jupyter

### Productivity tools
There are a number of useful extensions to a core Jupyter notebook that are recommended for installation, however they are not available in the docker image has installed. Using them would also create a dependency with any note books that you share.

## Named Entity Recognition (NER)
Named Entity Recognition is a way of extracted names of persons, organisations, locations etc. from unstructured text.  This example uses  pre-trained machine learning models.

<br/> 
https://bit.ly/2poVMIW (GitHub)

This Jupyter Notebook demonstrates:

    - Extraction of names mentioned in a tweet
    - Extracting multiple name from a large block of text
    - Basic OCR and name extraction

Tech tools used are:
    
    - spaCy, an industrial stength natural language processing library
    - tesseract and pytesseract, a popular OCR library and Python wrapper for it
    - Pillow, an imaging library 

## Speech Recognition (SR)
With speech becoming an increasing used and reliable method of user interaction for consumers with Alexa, Cortana, Google Assistant and Siri there will be a need to deal with various aspects of speech in business scenarios.  Alexa for Business is one example heading in this direction. 

<br/>
https://bit.ly/2XmgvtE (GitHub)

This Jupyter Notebook demonstrate extracting text from an audio file.

    - Visualising the wave form of the audio file
    - Playback of the audio
    - Extraction of text from a WAV file

Tech tools used are:
    
    - LibROSA, supports music and audio analysis
    - Matplotlib, a 2D plotting library
    - SpeechRecognition, supports several speech detection APIs
    - Google Speech Recognition API

## Text Mining
This example shows how to extract and process text from a PDF file but similar can be achieved from other common formats including Microsoft Office documentx.  This notebook shows how different language model yield different results. The model used are intended for written text (blogs, news, comments).

<br/>
https://bit.ly/2KVt9L5 (GitHub)

This Jupyter Notebook demonstrates:

    - Extracting text from the PDF
    - Processing the data to prepare it for analysis
    - Performing frequency analysis of the text
    - Displaying graphs of our analysis

Tech tools used are:
    
    - NLTK, the leading Python platform for working with natural language data
    - Tika, a highly performant text processing library
    - SpaCy, support large-scale information extraction tasks using trained language models.
    - Pandas, data processing
    - Matplotlib, visuals
    
## Machine Learning (ML)
This example shows how to take a dataset and apply a supervised ML algorithm to make predictions on a diabetics’ waist size given their cholesterol level. A fictitious example using a real world dataset.

https://bit.ly/3822MwZ (Github)

This Jupyter Notebook demonstrates:

    - Matplotlib, visuals and custom styling
    - K-nearest neighbors (KNN) regression

Tech tools used are:
    
    - Scikit-learn, for the pre-built ML algorithms
    - Pandas, data processing
    - Numpy, data processing
    - Matplotlib, visuals
    - colored, for terminal output colours
   
Creating custom styling can be tricky in Matplotlib.  The orignal attempt at colour coding gender in the scatter diagram was based on the following code fragment:

```python
data=[[220,20,0], [194,45, 1] ... ]

def setColour():
    cols=[]
    for row in data:
        if (row[2]==0):
            cols.append('#585094')
        elif (row[2]==1):
            cols.append('#009578')
    return cols
    
 setColour()
 ax = df.plot.scatter(x ='Cholesterol', y='Waist Size', c=cols)
```
The final version simplified the code as follows:

```python
data=[[220,20,0], [194,45, 1] ... ]
ax = df.plot.scatter(x ='Cholesterol', y='Waist Size', c=df['Gender'].apply(lambda x: colours[x])
```

### Machine Learning (ML) Stock Price Prediction
This example shows how to  make share price predictions. We use the Triad share price data available from https://uk.finance.yahoo.com/quote/TRD.L/history?p=TRD.L and use AutoTS (and all the clever packages it uses) to predict future share prices.  You can play with the data taking historic values and make a prediction and compare the results with future actuals.  It does take quite a while (~45 minutes) to run the predictions even on a reduced dataset of 200 stock prices.  The predictions are at the bottom of the vast amount of output showing the processing performed.

https://bit.ly/305oKAd (Github)

This Jupyter Notebook demonstrates:

    - AutoTS Automated Forecasting https://winedarksea.github.io/AutoTS/build/html/index.htmlTS
    - Probabilistic time series modeling using GluonTS
