---
title: "Bycon Services"
layout: default
permalink: /doc/services/services.html
www_link: https://github.com/progenetix/bycon
excerpt_separator: <!--more-->
date: 2020-10-20
category:
  - API
tags:
  - code
  - API
  - documentation
  - Beacon
  - bycon
  - Python
  - Bycon
  - services
  - .featured
---

## {{ page.title }}

The _bycon_ environment provides a number of data services which make use of
resources in the _Progenetix_ environment. Please refer to their specific
documentation.

* [_biosamples_](/doc/services/biosamples.html)
* [_collations_](/doc/services/collations.html)
* [_cytomapper_](/doc/services/cytomapper.html)
* [_deliveries_](/doc/services/deliveries.html)
* [_genespans_](/doc/services/genespans.html)
* [_geolocations_](/doc/services/geolocations.html)
* [_ids_](/doc/services/ids.html)
* [_ontologymaps_](/doc/services/ontologymaps.html)
* [_publications_](/doc/services/publications.html)
* [_schemas_](/doc/services/schemas.html)

### `services.py` and URL Mapping

The service URL format `progenetix.org/services/__service-name__?parameter=value`
is a shorthand for `progenetix.org/cgi-bin/bycon/services/__service-name__.py?parameter=value`.

<!--more-->

The `services` application deparses a request URI and calls the respective
script. The functionality is combined with the correct configuration of a
rewrite in the server configuration:

```
RewriteRule     "^/services(.*)"     /cgi-bin/bycon/services/services.py$1      [PT]
```

### Callback handling

The JSON response (see below) will be wrapped in a callback function if a `callback`
parameter is provided e.g. for Ajax functionality.

* <http://progenetix.org/services/collations?filters=PMID&datasetIds=progenetix&method=counts&callback=4445-9938-cbat-9891-kllt>

### Response formats

Standard responses are provided as `Content-Type: application/json`. The wrapper
format, as defined in the cofigurartion (`config/config.yaml`) provides a `data`
root parameter:

```
response_object_schema:
  parameters: { }
  data: { }
  errors: [ ]
  warnings: [ ]
```

This (incomplete) example response may help with understanding the general
format. Here, the data is a dictionary/object with a single key (`genes`):

##### Request  Example

* <https://progenetix.org/services/genespans?geneId=CDKN2>

##### Response Example

```
{
    "parameters": {
        "assemblyId": "GRCh38",
        "geneId": "CDKN2A"
    },
    "data": {
        "genes": [
            {
                "cds_end_max": 21994330,
                "cds_start_min": 21968228,
                "gene_entrez_id": 1029,
                "gene_symbol": "CDKN2A",
                "reference_name": "9"
            },
            {
                "cds_end_max": 183447426,
                "cds_start_min": 183444797,
                "gene_entrez_id": 55602,
                "gene_symbol": "CDKN2AIP",
                "reference_name": "4"
            },
            {
                "cds_end_max": 134411853,
                "cds_start_min": 134402914,
                "gene_entrez_id": 91368,
                "gene_symbol": "CDKN2AIPNL",
                "reference_name": "5"
            }
        ]
    },
    "errors": [],
    "warnings": []
}
```
<!--/podmd-->
