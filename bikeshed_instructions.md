# Creating spectext with markdown and bikeshed

## About

[Bikeshed](https://github.com/tabatkins/bikeshed) is a tool that generates specs (spectext html files) from simpler source files, such as markdown.

### Example

The BTCR DID method spec uses bikeshed for generating spectext. We edit the BTCR [index.bs file](https://github.com/w3c-ccg/didm-btcr/blob/gh-pages/index.bs), and then run bikeshed to generate the [index.html file](https://github.com/w3c-ccg/didm-btcr/blob/gh-pages/index.html). [The rendered output is shown here](https://w3c-ccg.github.io/didm-btcr/).

### When to use

Spec authors/editors may prefer to use markdown and bikeshed for the following types of [CCG work items](https://docs.google.com/document/d/1vj811aUbs8GwZUNo-LIFBHafsz4rZTSnRtPv7RQaqNc):

- Community Notes
- Community Commentaries
- Earlier phases of Community Specifications

In later phases of Community Specifications, especially complex ones like the DID spec, participants may prefer direct diffs on the html for precision. 

### Known Issues

While easier to work with than spectext files, this still involves bikeshed tool install/run instructions, and therefore is not non-dev friendly. 

As a workaround, we could stand up a generation tool to allow people to run bikeshed in a browser.

## Installing Bikeshed
```
git clone https://github.com/tabatkins/bikeshed.git
cd <location>/bikeshed
pip install --editable <location>/bikeshed
```

other possible prereqs:
```
brew install python@2
 pip install pygments lxml --upgrade
```

## Starting a spec

Use the [bikeshed quick start](https://github.com/tabatkins/bikeshed/blob/master/docs/quick-start.md).

An example of the BTCR metadata section is here:

```
<pre class='metadata'>
Title: BTCR DID Method
Shortname: didm-btcr
Level: 1
Status: w3c/CG-DRAFT
Group: Credentials Community Group
URL: https://w3c-ccg.github.io/didm-btcr/

Editor: Christopher Allen, http://www.lifewithalacrity.com/
Editor: Kim Hamilton Duffy, https://github.com/kimdhamilton
Editor: Ryan Grant
Editor: Dan Pape, https://github.com/danpape

Abstract: The Bitcoin Reference DID method specification conforms to the requirements specified in the <a href="https://w3c-ccg.github.io/did-spec/">DID specification</a> currently published by the W3C Credentials Community Group. For more information about DIDs and DID method specifications, please see the <a href="https://github.com/WebOfTrustInfo/rwot7/blob/master/topics-and-advance-readings/did-primer.md">DID Primer</a>.

</pre>

```


## Running Bikeshed

```
python bikeshed.py spec ../didm-btcr/index.bs
```
