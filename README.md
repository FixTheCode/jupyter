# Juypter Notebooks
Jupyter Notebooks are open-source web applications that allows you to create and share documents that contain live code, equations, visualizations and narrative text. Used by data scientists and those wishing to prototype various data cleaning transformation, numerical simulation, statistical modeling, data visualization and machine learning activities.  Juypter supports Python, R and F#. There are a number of notebooks below that demonstrate a number of the features above.

### Set-up
The easiest way to get started with Juypter is to use a cloud based service such as Azure Notebooks or a local Docker image. See https://notebooks.azure.com/ and https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html   There are several Docker images each with different libraries pre loaded.  With Azure Notebook there is a basic configuration on which additional libraries can be loaded as required.  

Tips for Docker use (Linux example, Windows commands will be similar) 

    - docker pull jupyter/datascience-notebook:latest
    - docker run -it --rm -p 8888:8888 -p 4040:4040 -v ~:/home/jovyan/workspace jupyter/datascience-notebook:latest
    - Use the URL output from the docker run command in 

## Named Entity Recognition (NER)
Named Entity Recognition is a way of extracted names of persons, organisations, locations etc. from unstructured text.  This example uses  pre-trained machine learning models.

https://notebooks.azure.com/davehorton/projects/natural-language-processing (Azure)<br/> 
https://tinyurl.com/tp93e42 (GitHub)

This Juypter notebook demonstrates:

    - Extraction of names mentioned in a tweet
    - Extracting multiple name from a large block of text
    - Basic OCR and name extraction

Tech tools used are:
    
    - spaCy, an industrial stength natural language processing library
    - tesseract and pytesseract, a popular OCR library and Python wrapper for it
    - Pillow, an imaging library 

## Speech Recognition
With speech becoming an increasing use method of user interactive for consumers with Alexa, Cortana, Google Assistant and Siri there will be a need to deal with various aspects of speech in business scenarios.  Alexa for Business is one example. 

This Juypter notebook demonstrate extracting text from an audio file.

    - Visualising the wave form of the audio file
    - Extraction of text from a WAV file

Tech tools used are:
    
    - librosa
    - matplotlib
    - numpty
    - scipy

## Statistical Anlysis
