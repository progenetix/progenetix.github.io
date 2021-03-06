---
title: "Beacon v2: Path Examples"
layout: default
permalink: /doc/beacon/paths.html
www_link: https://github.com/progenetix/bycon
excerpt_separator: <!--more-->
date: 2021-04-23
category:
  - documentation
tags:
  - API
  - documentation
  - Beacon
  - Beacon_v2
  - bycon
  - Python
  - services
  - .featured
---

## {{ page.title }}

The Beacon v2 protocol uses a REST path structure for consistant data access.

The Beacon+ implementation - developed oin the [`bycon` project](https://github.com/progenetix/bycon/)
implements an expanding set of those Beacon v2 paths for the [Progenetix](http://progenetix.org)
resource.

<!--more-->

----

#### Base `/`

The root path provides the standard `BeaconInfoResponse`.

* [/](https://progenetix.org/beacon/)

----

#### Base `/filtering_terms`

##### `/filtering_terms/`

* [/filtering_terms/](https://progenetix.org/beacon/filtering_terms/)


##### `/filtering_terms/` + query

* [/filtering_terms/?filters=PMID](https://progenetix.org/beacon/filtering_terms/?filters=PMID)
* [/filtering_terms/?filters=NCIT,icdom](https://progenetix.org/beacon/filtering_terms/?filters=NCIT,icdom)

----

#### Base `/biosamples`

##### `/biosamples/` + query

* [/biosamples/?filters=cellosaurus:CVCL_0004](https://progenetix.org/beacon/biosamples/?filters=cellosaurus:CVCL_0004)
  - this example retrieves all biosamples having an annotation for the Cellosaurus _CVCL_0004_
  identifier (K562)

##### `/biosamples/{id}/`

* [/biosamples/pgxbs-kftva5c9/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/)
  - retrieval of a single biosample

##### `/biosamples/{id}/variants/` & `/biosamples/{id}/variants_in_sample/`

* [/biosamples/pgxbs-kftva5c9/variants/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/variants/)
* [/biosamples/pgxbs-kftva5c9/variants_in_sample/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/variants_in_sample/)
  - retrieval of all variants from a single biosample
  - currently - and especially since for a mostly CNV containing resource - `variants` means "variant instances" (or as in the early v2 draft `variantsInSample`)

##### `/biosamples/{id}/analyses/`

* [/biosamples/pgxbs-kftva5c9/analyses/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/variants/)

----

#### Base `/individuals`

##### `/individuals/` + query

* [/individuals/?filters=NCIT:C7541](https://progenetix.org/beacon/individuals/?filters=NCIT:C7541)
  - this example retrieves all individuals having an annotation associated with _NCIT:C7541_ (retinoblastoma)
  - in Progenetix, this particular code will be part of the annotation for the _biosample(s)_ associated with the returned individual
* [/individuals/?filters=PATO:0020001,NCIT:C9291](https://progenetix.org/beacon/individuals/?filters=PATO:0020001,NCIT:C9291)
  - this query returns information about individuals with an anal carcinoma (**NCIT:C9291**) and a known male genotypic sex (**PATO:0020001**)
  - in Progenetix, the information about its sex is associated with the _Individual_ object (and rtherefore in the _individuals_ collection), whereas the information about the cancer type is a property of the _Biosample_ (and therefore stored in the _biosamples_ collection)

##### `/individuals/{id}/`

* [/biosamples/pgxind-kftx25hb/](http://progenetix.org/beacon/biosamples/pgxind-kftx25hb/)
  - retrieval of a single individual

##### `/individuals/{id}/variants/` & `/individuals/{id}/variants_in_sample/`

* [/individuals/pgxind-kftx25hb/variants/](http://progenetix.org/beacon/individuals/pgxind-kftx25hb/variants/)
* [/individuals/pgxind-kftx25hb/variants_in_sample/](http://progenetix.org/beacon/individuals/pgxind-kftx25hb/variants_in_sample/)
  - retrieval of all variants from a single individual
  - currently - and especially since for a mostly CNV containing resource - `variants` means "variant instances" (or as in the early v2 draft `variantsInSample`)

----

#### Base `/variants`

There is currently (April 2021) still some discussion about the implementation and naming
of the different types of genomic variant endpoints. Since the Progenetix collections
follow a "variant observations" principle all variant requests are directed against
the local `variants` collection.

If using `g_variants` or `variants_in_sample`, those will be treated as aliases.

##### `/variants/` + query

* [/variants/?assemblyId=GRCh38&referenceName=17&variantType=DEL&filterLogic=AND&start=7500000&start=7676592&end=7669607&end=7800000](http://progenetix.org/beacon/variants/?assemblyId=GRCh38&referenceName=17&variantType=DEL&filterLogic=AND&start=7500000&start=7676592&end=7669607&end=7800000)
  - This is an example for a Beacon "Bracket Query" which will return focal deletions in the TP53 locus (by position).

##### `/variants/{id}/` or `/variants_in_sample/{id}` or `/g_variants/{id}/`

* [/variants/5f5a35586b8c1d6d377b77f6/](http://progenetix.org/beacon/variants/5f5a35586b8c1d6d377b77f6/)
* [/variants_in_sample/5f5a35586b8c1d6d377b77f6/](http://progenetix.org/beacon/variants_in_sample/5f5a35586b8c1d6d377b77f6/)

##### `/variants/{id}/biosamples/` & `variants_in_sample/{id}/biosamples/`

* [/variants/5f5a35586b8c1d6d377b77f6/biosamples/](http://progenetix.org/beacon/variants/5f5a35586b8c1d6d377b77f6/biosamples/)
* [/variants_in_sample/5f5a35586b8c1d6d377b77f6/biosamples/](http://progenetix.org/beacon/variants_in_sample/5f5a35586b8c1d6d377b77f6/biosamples/)

----

#### Base `/analyses` (or `/callsets`)

The Beacon v2 `/analyses` endpoint accesses the Progenetix `callsets` collection
documents, i.e. information about the genomic variants derived from a single
analysis. In Progenetix the main use of these documents is the storage of e.g.
CNV statistics or binned genome calls.

##### `/analyses/` + query

* [/analyses/?filters=cellosaurus:CVCL_0004](https://progenetix.org/beacon/analyses/?filters=cellosaurus:CVCL_0004)
  - this example retrieves all biosamples having an annotation for the Cellosaurus _CVCL_0004_
  identifier (K562)
