# GerPS-Datafield

## abstract
The GerPS-Datafield is an extension for the [GerPs-Onto](https://w3id.org/GerPS-onto/ontology#). Besides the Procceses there are also forms, that contains the data that will be proccesed in Public Service. For this purpose there is the [XDatenfeld-Standard](https://www.xrepository.de/details/urn:xoev-de:fim:standard:xdatenfelder_2.0#version) as an [XöV](https://www.xoev.de/xoev-4987)-Standard. Its basicly an XML-protocoll for trasmitting data about these forms, but its not an semantic standard. So the GerPS-Datafield is the Semantic Version of this XDatenfeld-Standard. We integrated it in the GerPS-Onto to make this more interoperable and extend the possibilities to work with this semantic standards. 

## important path in this Repo

1. [competency Questions](docs/CQ/Answer/CQ_Questions.md)
2. [Ontology](Ontologie/GerPS-Onto-Datenfeld.rdf)
3. [Data](https://github.com/fusion-jena/GerPS-Datafield/tree/main/Ontologie/Data)

## running
In the [Path](./Ontologie/Data) there are three example of XDatafield fiels for create die Population of the Ontologie. Upload these files in the [XUI](https://xui.simplex.fmi.uni-jena.de/xdatenfeld) by drag n' drob. Also you can use your own files or search for suitable Files Via the [Integration](https://xui.simplex.fmi.uni-jena.de/ximport) of the [XDatafield-Repostory](https://schema.fim.fitko.net/docs#/). After this you can Run the "Convert to ..." function and get the result in your preferd semantic format. Step by Step:

1. Upload your files (or choose them) at [XUI](https://xui.simplex.fmi.uni-jena.de/xdatenfeld) 
2. choose "Convert to ..."
3. choose your format
4. execute
5. download result

## Code
The Code will be released at [openCode](https://gitlab.opencode.de/opendva) soon.

## Lizenz

MIT License

Copyright (c) 2023 FUSION

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
