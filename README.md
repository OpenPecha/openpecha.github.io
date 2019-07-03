## Overview

OpenPecha is a combined online Tibetan language text repository and open source toolkit. It enables publishers, scholars and the public to crowdsource the editing and annotation of Tibetan texts.

### Features

#### Repository features
* GitHub-hosted library includes more than X Tibetan language texts
* Raw text versions of each work are available for scholarly use
* Annotations for each text are stored in separate files for easy export (see toolkit features)
* Optimized versions of each text are available from leading Tibetan-language publishers
* Includes system for reporting spelling, formatting and punctuation errors to publishers
* GitHub’s workflow allows colleagues to easily update existing editions or create new one

#### Toolkit features
* File format converter optimized for Tibetan documents
* Annotation extractor separates annotations into separate files during import and stores them in repository for later use
* Export file function allows users to choose annotation layers to include in new file

### Supported formats
* .ePub
* .pdf
* .doc

To suggest a new file format, create a new issue and include a link to a Tibetan language file that uses that format.

### Supported annotation layers
* Table of contents
* Root text (if text is a commentary)
* Definitions
* Yigchung (liturgical instructions)
* Outlines
* Citations
* Commentaries
* Citation sources
* Names
* Places

To suggest other annotation types, create a new issue and let us know what you’d like us to add.

### Participating publishers
* Shechen Publications
* Tsadra Publications
* Etc.

### OpenPecha file architecture

Each OpenPecha text is stored in its own GitHub repository. This repository contains three main items:
* Main text
* Sources folder
* Layers folder

#### Main text
The raw Tibetan text is stored in the root folder of its respective repository. It is a .txt file.

#### Sources folder
The sources folder contains annotated versions of the text. These texts are offered by participating Tibetan publishers and libraries. They are found in .ePub, .pdf and .doc formats.

#### Layers folder
The layers folder contains a subfolder for each annotation type that OpenPecha supports. Within each subfolder are the annotation files themselves. These have been extracted from marked up versions of each text. Subfolders may contain more than one annotation file. For example, a text that has multiple clickable outlines will have a equal number of outline files. Annotation files are also contained in .txt files. 

### How to find texts on GitHub
Each Tibetan text is stored in its own repository. This repository is named after the text’s TBRC Resource ID, a reference number given by the Buddhist Digital Resource Center (BDRC).
If you don’t know the TBRC Resource ID for the text you’re looking for, search for it directly on the BDRC site. Then search for that TBRC Resource ID on GitHub. Or search for the text’s title in Tibetan on GitHub.

### How to install the OpenPecha toolkit

Open terminal
Type this

### Exporting texts

#### How to export annotated texts

When you export a file from OpenPecha, you can choose the file format you’d like to export to and you can choose the annotation layers you’d like your new version to include

* Open the OpenPecha interface.
* Click on the layers you’d like to include.
* Choose your desired file format
* Choose a download location
* Click on Export

Note: for 

#### How to export plain text files

To get get a Tibetan text for use with natural language processing (NLP) tools such as pybo or to compare them, simply download the .txt version of the main text in the repository for the text you need.

### Importing texts

#### How to add new texts to OpenPecha

* Step one
* Step two
* Step three

#### How to add new annotations to a specific text

* Create a fork of the text
* Use the interface to extract the annotations into your fork
* Choose which layers to add to your fork
* Create a pull request.
* The text owner will review your suggested changes and accept them open approval.

### How to report mistakes in and suggest changes to existing files

#### How to report spelling errors, spacing errors and missing or redundant punctuation

There are two ways:

##### One: create a fork and make a pull request.

* Create a fork, if you haven't already.
* Make your spelling errors, spacing, and or punctuation corrections in the .txt.
* Make a pull request.

Or...
##### Two: create an issue

How to create an issue
* Step one
* Step two

Note: The text owner will review your suggested changes and accept them open approval.

#### How to suggest annotation changes

To suggest annotation mistakes or changes, you will need to import your version of the text to into your GitHub fork and then conduct a pull request.

How to do this:
* Step one
* Step two
* Step three

### Contributors

* Drupchen
* Tenzin
* NT

### Acknowledgements

Thank the publishers and sponsors and the people who maintain the repositories

### Copyright

Same kind of copyright as pybo





