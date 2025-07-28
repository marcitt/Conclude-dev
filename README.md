# Conclude-dev

## Backend
The Backend is used for managing the application API and server. The server is currently run using Flask, however migrating to FastAPI may be better for future development.

### Getting Started 
All of the steps required to setup the backend will be explained in more detailed below, here is a quick summary:

Backend requirements:
1. Ollama (for running local AI models)
2. llama3:8b model installed locally (using Ollama)
3. tesseract installed on your system


#### Setting Up Ollama

(For local AI models) Install Ollama: https://ollama.com/

To check this has been installed correctly open a terminal/shell and run:
```
ollama --version
```

The model we are currently testing with is llama3.1:8b, it requires 4.9GB of storage. You can view more details of the model here: https://ollama.com/library/llama3.1:8b

To install the model run:
```
ollama pull llama3:8b
```

If you want to test it out locally in the terminal you can run:
```
ollama run llama3:8b
```

If you would prefer to use a different model (e.g. that takes up less storage) you can research here: https://ollama.com/search
However you will need to modify some lines of code in your local repo to make sure everything is working.

Anywhere in the code where an llm is initialised you will have to replace "llama3:8b" with your chosen model:
```
llm = Ollama(model="llama3:8b", temperature=0) 
```

#### Method 1: Setup with conda (preferred method)
I prefer to use Conda (Anaconda) for managing environments - if you already know how to use this I would recommend as it is often easier to manage and work with pytesseract etc. to set-up with Conda instead do this: 

Install anaconda: https://www.anaconda.com/download

Check it has been installed correctly:
```
conda --version
```

Run:
```
conda env create -f environment.yaml
```

```
conda activate conclude
```

If you ever want to deactivate environment:
```
conda deactivate conclude
```

⚠️ Using Anaconda/Conda can change your system PATH which can present issues e.g. it may set the conda installation of Python to your default, which might not be desirable if you typically prefer to work with another Python installation. If you have issues with this I can help out but just a warning in advance.


#### Method 2: Setup with venv (may be easier)

##### Installing Tesseract

To use the OCR library `pytesseract` we need to make sure `tesseract` is installed on the system/PATH. To do this on mac/unix this should be possible by running:

Note: If you are comfortable using Anaconda and conda environments you can skip this step.

```
brew install tesseract
```
This uses homebrew to install tesseract - if you don't have homebrew configured or are on windows you might have to research how to do this yourself. 

For further details on installing tesseract (e.g. for windows) details are included here:
https://www.geeksforgeeks.org/python/introduction-to-python-pytesseract-package/


##### Setting up virtual environment

```
cd backend
```

```
python -m venv venv
```
⚠️ for mac may need to use python3 depending on how Python is configured on your system

```
source venv/bin/activate
```
for windows use: `venv\Scripts\activate`

```
python -m pip install -r requirements.txt
```

```
python setup-test.py
```


## Client
The client (also known as frontend) will be what the user interacts with. We are using React for the frontend.

### Getting started
To setup the client make sure to enter the directory:
```
cd client
```
Then install any dependencies:
```
npm install
```

You should then be able to run the frontend:
```
npm run dev
```
Navigate to the link provided and you should be able to see the frontend running.