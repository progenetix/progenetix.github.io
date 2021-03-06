---
title:  "BeaconPlus Changes"
layout: default
date: 2021-04-30
permalink: /beaconplus-changelog.html
excerpt_separator: <!--more-->
category:
  - doc
  - news
tags:
  - API
  - documentation
  - Beacon
  - Beacon_v2
  - services
---

## {{ page.title }}

This page lists changes for the [Beacon+](http://beacon.progenetix.org/ui/)
implementation of the ["Beacon" genomics API](http://beacon-project.io).

#### 2021-04-30: Closing in on Beacon v2

As one of the drivers of the Beacon protocol and to drive the Beacon v2 protocol
process we have now started the documentation of Beacon v2 endpoints which
are supported in Progenetix as part of the [**implementations-v2**](https://github.com/ga4gh-beacon/implementations-v2/blob/main/index.md)
project:

* [documentation source](https://github.com/ga4gh-beacon/implementations-v2/blob/main/progenetix-examples.md)
* same as [web page](https://beacon-project.io/implementations-v2/progenetix-examples.html)

<!--more-->

#### 2020-10-01: Moving to `bycon` powered BeaconPlus

We've changed the Beacon backend to the `bycon` code base. The new project's
codebase is accessible through the [`bycon`](http://github.com/progenetix/bycon/)
project. Contributions welcome!

~~#### 2019-09-30: Using the `BeaconAlleleResponses` parameter~~

So far the Beacon+ implementation did not make use of the `BeaconAlleleResponses`
parameter though it is required by the protocol, but instad always interpreted
requests as with the `ALL` parameter.

##### Changes

* UI offers selector for `BeaconAlleleResponses` options
* UI now allows selection of multiple datasets
* API follows Beacon protocol in `BeaconAlleleResponses` interpretation

##### Example

<https://beacon.progenetix.org/cgi/bycon/beaconServer/byconplus.py?referenceBases=G&alternateBases=A&datasetIds=progenetix&assemblyId=GRCh38&referenceName=17&filterLogic=AND&start=7577120&filters=pgxcohort-DIPG>
