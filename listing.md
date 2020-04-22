# Adding a model to the list of electrophysiology models

To get your model exposure to show up [in this list](https://models.physiomeproject.org/electrophysiology), follow these steps:

## Step 1: Adding meta data

You'll need to make sure your model code includes meta data identifying it as an "electrophysiology" model.
In CellML 1.0/1.1, this is done by

1. Ensuring your model has a `cmeta:id` attribute with some unique id:

```
<model name="best_model" 
  xmlns="http://www.cellml.org/cellml/1.0#"
  xmlns:cmeta="http://www.cellml.org/metadata/1.0#"
  cmeta:id="MODEL_ID_GOES_HERE">
```

2. Adding some RDF elements into your CellML model:

```
<model ... >
...
  <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" 
           xmlns:bqs="http://www.cellml.org/bqs/1.0#" 
           xmlns:dc="http://purl.org/dc/elements/1.1/">
    <rdf:Description rdf:about="#MODEL_ID_GOES_HERE">
      <bqs:reference rdf:parseType="Resource">
        <dc:subject rdf:parseType="Resource">
          <bqs:subject_type>keyword</bqs:subject_type>
          <rdf:value>
            <rdf:Bag>
              <rdf:li>electrophysiology</rdf:li>
          </rdf:Bag>
        </rdf:value>
      </dc:subject>
    </bqs:reference>
  </rdf:RDF>
</model>
```

Note that the `cmeta:id` attribute does _not_ have a hash (#) before the id, while the `rdf:about` attribute does.

## Step 2: Uploading your model

This involves

1. Creating or forking a ~github repository~ workspace (see [creating.md] or [updating.md])

2. Creating ~a git tag~ an exposure (see [the official guide](https://aucklandphysiomerepository.readthedocs.io/en/latest/quickstart.html) or [updating.md])
