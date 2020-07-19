# Stanford Pipeline

 A fork of the OEDA Stanford Pipeline. See the original repo for more detailed information:
 https://github.com/openeventdata/stanford_pipeline

 ## Prerequisites

 The stanford pipeline expects stories to be populated in MongoDB. It reads stories from Mongo and parses sentences into parse trees (sentence diagrams). This step is crucial for allowing the later parts of the event coding pipeline to work.

## Install

### Clone the Repo

```git clone https://github.com/dgmurphy/stanford_pipeline.git```

```cd stanford_pipeline```

### Download the Core NLP Models

```
wget http://nlp.stanford.edu/software/stanford-corenlp-full-2014-06-16.zip
unzip stanford-corenlp-full-2014-06-16.zip
mv stanford-corenlp-full-2014-06-16 stanford-corenlp
cd stanford-corenlp
wget http://nlp.stanford.edu/software/stanford-srparser-2014-07-01-models.jar
```

In the file default_config.ini edit the line:

`stanford_dir = ~/stanford-corenlp`

to use the full path to the stanford-corenlp dir, e.g.:

`stanford_dir = /home/dmurphy/dev/oeda/stanford_pipeline/stanford-corenlp`

### Create Python Environment & Install libraries

In the stanford_pipeline directory create a Python2 virtual environment:

```virtualenv -p /usr/bin/python2.7 venv```

Activate the virtual environment:

```source venv/bin/activate```

Check: make sure your linux command prompt starts with '(venv)'

### Install Python Libraries

```pip install -r requirements.txt```


### Execute a Test Run

```python process.py```

Up to a minute of [Errno 111] Connection refused messages are normal during startup.

Check: The command line should show "processing story" messages.

### MongoDB

Check the 'stories' collection in the 'event_scrape' database to view the scraped content with parse trees.