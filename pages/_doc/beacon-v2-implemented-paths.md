---
title: "Beacon v2: Path Examples"
layout: default
permalink: /doc/beacon/paths-examples.html
www_link: https://github.com/progenetix/bycon
excerpt_separator: <!--more-->
date: 2021-04-23
category:
  - API
tags:
  - API
  - code
  - documentation
  - Beacon
  - BeaconV2
  - bycon
  - Python
  - Bycon
  - services
---

## {{ page.title }}

The Beacon v2 protocol uses a REST path structure for consistant data access.

The Beacon+ implementation - developed oin the [`bycon` project](https://github.com/progenetix/bycon/)
implements an expanding set of those Beacon v2 paths for the [Progenetix](http://progenetix.org)
resource.

<!--more-->

### Examples

#### Base `/filtering_terms`

##### `/filtering_terms/`

* [/filtering_terms/](https://progenetix.org/beacon/filtering_terms/)


##### `/filtering_terms/` + query

* [/filtering_terms/?filters=PMID](https://progenetix.org/beacon/filtering_terms/?filters=PMID)
* [/filtering_terms/?filters=NCIT,icdom](https://progenetix.org/beacon/filtering_terms/?filters=NCIT,icdom)

#### Base `biosamples`

##### `/biosamples/` + query

* [/biosamples/?filters=cellosaurus:CVCL_0004](https://progenetix.org/beacon/biosamples/?filters=cellosaurus:CVCL_0004)
  - this example retrieves all biosamples having an annotation for the Cellosaurus _CVCL_0004_
  identifier (K562)

##### `/biosamples/{id}/`

* [/biosamples/pgxbs-kftva5c9/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/)
  - retrieval of a single biosample

##### `/biosamples/{id}/variants/`

* [/biosamples/pgxbs-kftva5c9/variants/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/variants/)
  - retrieval of all variants from a single biosample


#### Base `variants`

There is currently (April 2021) still some discussion about the implementation and naming
of the different types of genomic variant endpoints. Since the Progenetix collections
follow a "variant observations" principle all variant requests are directed against
the local `variants` collection.

##### `/variants/` + query

* [/variants/?assemblyId=GRCh38&referenceName=17&variantType=DEL&filterLogic=AND&start=7500000&start=7676592&end=7669607&end=7800000](http://progenetix.org/beacon/variants/?assemblyId=GRCh38&referenceName=17&variantType=DEL&filterLogic=AND&start=7500000&start=7676592&end=7669607&end=7800000)
  - This is an example for a Beacon "Bracket Query" which will return focal deletions in the TP53 locus (by position).

##### `/variants/{id}/` or `/variants_in_sample/{id}` or `/g_variants/{id}/`

* [/variants/5f5a35586b8c1d6d377b77f6/](http://progenetix.org/beacon/variants/5f5a35586b8c1d6d377b77f6/)
* [/variants_in_sample/5f5a35586b8c1d6d377b77f6/](http://progenetix.org/beacon/variants_in_sample/5f5a35586b8c1d6d377b77f6/)

##### `/variants/{id}/biosamples/`

* [/variants/5f5a35586b8c1d6d377b77f6/biosamples/](http://progenetix.org/beacon/variants/5f5a35586b8c1d6d377b77f6/biosamples/)