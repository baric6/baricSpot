# Managing Datamodels and Sets

{% embed url="https://help.splunk.com/en/splunk-enterprise/manage-knowledge-objects/knowledge-management-manual/9.4/manage-and-explore-datasets/manage-datasets" %}

#### To look inside a data model to see if the correct data is there

```
| datamodel Authentication Authentication search
```

#### To look at the Data model itself "Generics"

```
| datamodel Authentication
```

#### With the output

* objectNameList
  * List of all the different datasets that are apart of the data-model&#x20;
* objectSummary
  * high level summery of dataset&#x20;
* objects
  * Detailed configuration of each dataset stored, may show only the root authentication dataset&#x20;

#### Count each tag in datamodel for ingested data&#x20;

If there is any events in the tag, good to see what datamodel has a event

```
* | stats count by tag
| search tag IN ("authentication","email","ids","malware","network","endpoint","web","vulnerablity")
| sort - count
```

#### Failed Auth

Check if you have any failed auth in datamodel

```
| from datamodel:"Authentication"."Failed_Authentication"
```

