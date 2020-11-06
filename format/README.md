# OpenPecha Format (OPF)

## OPF structure

OPF is an open folder format, which means it’s not a compiled file, but simply an open folder with a specific hierarchy. Every OpenPecha file consists of a base text (or base texts, in the case of works with multiple volumes) in plain text (ie, v001.txt, also called the base layer) in the “base” folder and its annotations (layer_name.yml) in the corresponding “v001” folder of the “layers” folder. OPF assumes that pecha with a single base layer has only one volume. A sample OPF file might have an internal structure something like this: 
- 📁  P000780.opf
  - 📄 index.yml
  - 📄 meta.yml
  - 📁 base
    - v001.txt
    - v002.txt 
  - 📁 layers
    - 📁 v001
      - 📄 title.yml
      - 📄 author.yml
      - 📄 tsawa.yml
      - 📄 yigchung.yml
    - 📁 v002
      - 📄 title.yml

In the example above, the text has the globally unique and persistent identifier “P000780”; its source text is the “base” directory. (In this case, it comes from an image scan and its raw OCR data found in the github release “v0.1”). It is then formatted as an OPF base text. This OPF has annotation layers for metadata (meta.yml), index/toc (index.yml), and titles (title.yml). “Layers” is simply a list of the annotation layers that are linked to the text, and “title” is a layer that gives formatting annotations for titles (similar to the <title></title> inline tag in HTML).
