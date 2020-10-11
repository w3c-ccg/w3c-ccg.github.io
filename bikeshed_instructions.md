# Creating spectext with bikeshed (markdown)

[Bikeshed](https://github.com/tabatkins/bikeshed) is a tool that generates specs (html/ReSpec files) from simpler source files, such as markdown.

If you're using bikeshed, we recommend performing the conversion to html/ReSec as a github action. You can use the [markdown-to-spec repo](https://github.com/w3c-ccg/markdown-to-spec) as a template.

Use the [bikeshed quick start](https://github.com/tabatkins/bikeshed/blob/master/docs/quick-start.md).

## Example

The [vc-ed-models spec](https://w3c-ccg.github.io/vc-ed-models/) and [source](https://github.com/w3c-ccg/vc-ed-models) demonstrate a spec that's written in bikeshed with a github action that auto-converts to HTML/ReSpec Note the following:
- The "source" file for the html is index.bs, in the main branch
- The [github action](https://github.com/w3c-ccg/vc-ed-models/blob/main/.github/workflows/publish.yml) converts that file to index.html and pushes it to the gh-pages branch

You can run bikeshed locally to preview the results. Instructions are below.

## When to use

Spec authors/editors may prefer to use markdown and bikeshed for the following types of [CCG work items](https://docs.google.com/document/d/1vj811aUbs8GwZUNo-LIFBHafsz4rZTSnRtPv7RQaqNc):

- Community Notes
- Community Commentaries
- Earlier phases of Community Specifications

In later phases of Community Specifications, especially complex ones like the DID spec, participants may prefer direct diffs on the html for precision. 

## Running Locally

### Installing Bikeshed
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

## Additional Examples

The BTCR DID method spec uses bikeshed for generating spectext. We edit the BTCR [index.bs file](https://github.com/w3c-ccg/didm-btcr/blob/gh-pages/index.bs), and then run bikeshed to generate the [index.html file](https://github.com/w3c-ccg/didm-btcr/blob/gh-pages/index.html). [The rendered output is shown here](https://w3c-ccg.github.io/didm-btcr/).

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

Note: In Amira, I ended up adding this line as well for markdown-to-html bolding:

```
Markup Shorthands: css no, markdown yes
```


## Running Bikeshed

```
python bikeshed.py spec ../didm-btcr/index.bs
```
