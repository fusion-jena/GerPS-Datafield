# GerPS-Datafield

## Overview
The GerPS-Datafield is an extension for the [GerPS-onto](https://w3id.org/GerPS-onto/ontology#). GerPS-Datafield and GerPS-onto model different [XöV](https://www.xoev.de/xoev-4987)-Standards:
1. GerPS-onto models process information, which normaly is encoded as [XProzess](https://www.xrepository.de/details/urn:xoev-de:mv:em:standard:xprozess)
2. GerPS-Datafield models information stored in forms, derived from the [XDatenfeld](https://www.xrepository.de/details/urn:xoev-de:fim:standard:xdatenfelder_2.0#version)

Both XProzess and XDatenfeld are XML-Protocols, not semantic standards. For this purpose we modeled GerPS-Datafield as the semantic version of the XDatenfeld-Standard. We integrated it in into GerPS-Onto to ensure interoperability and extend the applications of these semantic standards. 

## Structure

1. [Competency Questions](docs/CQ/Answer/CQ_Questions.md)
2. [Ontology](Ontologie/GerPS-Onto-Datenfeld.rdf)
3. [Data](Ontologie/Data)

## Usage
In [Data](./Ontologie/Data) there are three example XDatenfeld-files to create the entities of the ontology. Upload these files in the [XUI](https://xui.simplex.fmi.uni-jena.de/xdatenfeld) by Drag and Drop. You can also use your own files or search the  Files Via the [XDatafield-Repostory](https://schema.fim.fitko.net/docs#/) using our [import interface](https://xui.simplex.fmi.uni-jena.de/ximport). Afterwards, you can run the "Convert to ..." function and get the result in your preferred semantic format. Step by Step:

1. Upload your files at [XUI](https://xui.simplex.fmi.uni-jena.de/xdatenfeld) 
2. Select "Convert to ..."
3. Choose your format
4. Click "Execute"
5. Download the result using the button below the preview

## Code
The code will be released at [openCode](https://gitlab.opencode.de/opendva) soon.

## Documentation

The documentation is available [here](https://fusion-jena.github.io/GerPS-Datafield/). The source code for the website is located in the [gh-pages branch](https://github.com/fusion-jena/GerPS-Datafield/tree/gh-pages).

## License

This project is licensed under the [CC BY 4.0](LICENSE).
