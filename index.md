---
layout: default
---

About Silobreaker
----------

> Founded in 2005, Silobreaker is a data analytics company that offers products and services which aggregate, analyze, contextualize and bring meaning to the ever-increasing amount of digital information. Silobreaker Premium is the most powerful intelligence product online and the Silobreaker Software offers a fully customizable solution for those who require installations behind their own firewalls.
>
>
> Silobreaker’s products help many users from the corporate, government, military and financial services sectors around the world. Our customers represent a wide range of use-cases across cyber security, competitive intelligence, incident management, government and military OSINT, geo-political analysis and risk intelligence.

[Read more &raquo;](http://www.silobreaker.com/)

Acquisition and Installation
----------

If you wish to receive a demo or contact our sales team, please see our [contact information](http://www.silobreaker.com/contact-us/).

If you have a license that includes Maltego access, Silobreaker will provide the API-keys for you to use.

#### Installation:

1. Launch Maltego and navigate to the home screen. This should show on launch if you have not switched to any other screens.
2. Find Silobreaker in the grid of transforms.
3. Press the `[INSTALL]` button.
4. Navigate through the short installation process.
5. Still on the _Transform Hub_, press the now displayed `settings`-button for Silobreaker.
6. This will show a dialog where you will have to paste your own API key.   
7. You're now ready to use all of the Silobreaker transforms.
  
# Using the Silobreaker Transforms in Maltego

### Pre-requisites

Some of our transforms use **lists** from Silobreaker. For these transforms to work, the API key must belong to an account with the following Silobreaker lists (check availability under My Lists in Silobreaker Premium):

* Hacktivist Operations

### Entities
Installing Silobreaker transforms also includes a custom entity set. Our transforms can return both Maltego and Silobreaker entities depending on the transform being used. Maltego entities are used when the returned entity type exists in both Maltego and Silobreaker. Otherwise, a Silobreaker custom entity will be returned. In both cases the returned entity will have a Silobreaker icon. Visit our [user guide](https://my.silobreaker.com/Help-v2/basics/entities/#entity-types) to read more about our entities [^1].

### Association/Relation Transforms

Silobreaker indexes millions of documents and searches these to find mentions of _entities_. Our Maltego transforms use our API to find entities that are related to your input. An entity is _related_ to (or associated with) another when mentioned in the same context. If you need more information about how a relation is extracted you can [investigate it](#investigating-relations).

All transforms described below will adhere to the following pattern:
> `Input Entity Type` &rarr; `Output Entity Type`

> Transform description as written in Maltego

To the left of the arrow will be the input to the transform i.e., an entity on the canvas in Maltego. To the right of the arrow is the resulting entity type of the transform.

## General Transforms

These transforms are included with the _**Related General Entities**_ transform set.

### Keyphrases

> Any &rarr; `maltego.Phrase`

> Find related Keyphrases

Find phrases that are _keyphrases_ within Silobreaker. _Keyphrases_ in Silobreaker are words or phrases that are key to the content of the document. 

![keyphrases](images/keyphrases.png)

### Persons
> Any &rarr; `maltego.Person`

> Find related persons

Returns people that are frequently mentioned in the same context as the input entity.

### Companies
> Any &rarr; `maltego.Company`

> Find related companies

### Organizations
> Any &rarr; `maltego.Organization`

> Find related organizations

### Products
> Any &rarr; `silobreaker.Product`

> Find related products

## Cyber Transforms

These transforms are included with the _**Related Cyber Entities**_ transform set.

### Credit Cards
> Any &rarr; `silobreaker.CreditCard`

> Find related credit cards

Credit card numbers are automatically identified by Silobreaker and are usually found in CC dumps on paste sites.

### IINs
> Any &rarr; `silobreaker.IIN`

> Find related Issuer Identification Number

An IIN, issuer identification number, also often referred to as BIN - bank identiciation number. The IIN are the first 6 digits of a credit card and uniquely identifies card issuer and issuing bank. 

### Hashtags
> Any &rarr; `silobreaker.HashTag`

> Find related #Hashtags

Silobreaker automatically finds [hashtags](https://en.wikipedia.org/wiki/Hashtag) based on their formatting, `#example`. While these are usually hashtags on social media, such as twitter, they could be anything using the same formatting. For example IRC uses a hashtag format to identify #channel names.

### Usernames
> Any &rarr; `silobreaker.Username`

> Find related @usernames

Finds @usernames that are associated with the input entities. These are _usually_ Twitter-handles but can be from other services that use a similar naming system.

### IPv4s
> Any &rarr; `maltego.IPv4Address`

> Find related IPv4-addresses

Find IP addresses that are often mentioned in association with the input entity. This association is only based on mentions in documents and is not any type of look-up.

### Email Addresses
> Any &rarr; `maltego.EmailAddress`

> Find related Email-Addresses

### Domains
> Any &rarr; `maltego.Domain`

> Find related domains

Domains such as `facebook.com`, `silobreaker.se` or `plus.google.com` extracted from documents matching the input entity.

### Email Domains
> Any &rarr; `silobreaker.EmailDomain`

> Find related email domains

A email domain is attached to an email address and differs from domain in that it is contextual and only extracted as part of extracting email address entities. 

### URLs
> Any &rarr; `maltego.URL`

> Finds related URLs. Includes the entire path mentioned

E.g., `https://www.facebook.com/example/page` or `http://t.co/123456abc`.

### Vulnerabilities
> Any &rarr; `silobreaker.Vulnerability`

> Find Vulnerabilities listed by CVE identifier

Silobreaker maintains a complete list known vulnerabilities that have been acknowledged and given a  [CVE](https://en.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures) identifier. This transform finds the vulnerabilities that are the most related to your input entity.

### Hashes
> Any &rarr; `silobreaker.Hash`

> Find related hashes

Silobreaker automatically identifies strings that match the length and content of [MD5](https://en.wikipedia.org/wiki/MD5) or [SHA](https://en.wikipedia.org/wiki/Secure_Hash_Algorithm). This transform finds the hashes that are the most related to the input entity.

### Malware
> Any &rarr; `silobreaker.Malware`

> Find related malware, identified by their popularised name

This returns known malware by their names, often given by the security company that discovers them. 

![malware](images/malware.png)

### Malicious IPs
> Any &rarr; `maltego.IPv4Address`

> Find IP addresses related to various malicious activity e.g., Malware or Threat Actors

This will let you find IPs which are associated with different Threat Actors and Malware. They may not necessarily be _malicious_ IP addresses, but they will be associated with malicious activity.

### Attack Types
> Any &rarr; `maltego.Phrase`

> Find related Attack Types, eg. 'Bootkit' or 'HTML-injection'

This finds the Attack Types which are most frequently mentioned in association with the input entity.

### Threat Actors
> Any &rarr; `silobreaker.ThreatActor`

> Find related Threat Actors

Threat Actor is a person or a group of individuals that poses a cyber security threat, such as a hacktivist groups or state sponsored hackers. 

  ![threat-actor](images/threatactors.png)

### Hacker Ops
> Any &rarr; Any Silobreaker type

> Find related cyber entities from the "Hacktivist Operations" list in SB.

Hacker Operation or 'Ops' are joint efforts or rushes to attack specific targets; eg. [Operation Antisec](https://en.wikipedia.org/wiki/Operation_AntiSec). Silobreaker automatically identifies and tracks these Operations. This transform allows you to find operations that are related to the input entity.

## Geo[graphical] Transforms

These transforms are included with the _**Related Geo Entities**_ transform set.

### Countries
> Any &rarr; `maltego.Country`

> Find related Countries

Find countries that are associated with the input entities. These countries are not necessarily the countries the entities come from or where the story originated; the relationship only indicates that the input entity and the country are frequently mentioned in the same documents.

### Cities
> Any &rarr; `maltego.City`

> Find related Cities

Finds cities that are associated with the input entities. The relationship is based on the fact that the input entity and the cities are frequently mentioned in the same context, in the same documents - not necessarily any actual origin or location.

### Provinces
> Any &rarr; `silobreaker.Province`

> Find related Provinces 

Finds provinces that are associated with the input entities.

### Regions
> Any &rarr; `silobreaker.Region`

> Find related Regions 

Finds regions that are associated with the input entities.

### World Regions
> Any &rarr; `silobreaker.WorldRegion`

> Find related World Regions 

Finds world regions that are associated with the input entities.

## Search Transforms

These transforms are included with the _**Search**_ transform set.

### Matching Entities
> Any &rarr; Any Silobreaker type

> Find matching SB entities.

This special transform makes a general search to find Entities that match your
input. The transform will only return Entities with a name or an alias that __match__ your input; it does
__not__ return entities that are related or associated to it. You can also use this to
pull entities from a list you have access to by prefixing the list name with
"list:", e.g. to get entities from the list "CVE2014" you should name your input
entity "list:CVE2014"

### Related Entities
> Any &rarr; any Silobreaker entity

> Find related Entities of any type

Takes any type of entity as input and outputs the most related entities across all Silobreaker entity types.

### Related Documents
> Any &rarr; `silobreaker.Document`

> Find related Documents

Returns the documents that are the most related to your input. See [Document Info](#document-info) for more information about `silobreaker.Document` items.

### Related Pastes
> Any &rarr; `silobreaker.Document`

> Find related Pastes

Pastes are a category of documents in Silobreaker. This transform returns the pastes that are the most related to your input. See [Document Info](#document-info) for more information about `silobreaker.Document` items.

### Related Publications
> Any &rarr; `silobreaker.Publication`

> Find related Publications

Returns the Publications that are related to the input.

## Investigating Relations

Also found in the _**Search**_ transform set, these transforms possess a more specific purpose in that they are used to investigate relationships between the nodes on the canvas. These transforms aim to answer the questions:

* _Why did an earlier transform return this entity?_
* _Where can I find the evidence for this relationship?_

### Document Evidence For Link
> Any Silobreaker entity &rarr; `silobreaker.Document`

> Find document evidence for inbound link

This special transform is used to investigate relations. If you have used any of the entity transforms on a Silobreaker entity to find related entities you can use the _[SB] Document Evidence For Link_ on the child nodes to find documents that outline the relationship between those children and their parent(s). Paste documents are excluded from the result set by default. Run [Document Evidence For Link (Including Pastes)](#document-evidence-for-link-(including-pastes)) to find evidence of pastes in addition to regular documents.

#### Finding the Evidence

1. Insert an entity and use any of the Silobreaker entity transforms to find related entities.

    ![companies](images/companies.png)
  
    _**[SB] Companies** used on **Derusbi**_.

2. On any of the generated child nodes, perform the _[SB] Document Evidence For Link_ transform.
3. The children that are generated are `silobreaker.Document` items.

    ![document-evidence-for-links](images/documentevidenceforlink.png)
  
    _These are the original documents where the relationship between **Derusbi** and **Cisco Systems Inc** is established._

#### Document Info

You can also inspect the _**Detail View**_ (located on the right hand side of the Maltego application) when focused on a document.

![detail-view](images/detailview.png)

The detail view provides you with general information e.g., _**Incoming**_ and _**Outgoing**_ relationships for the entity or entites selected on the canvas. The detail view will also contain a _**Document Info**_ section for `silobreaker.Document` items. This section is made up of 3 main components:

* Headline - This is the headline as written in the original document. Clicking on the headline will open a new tab in your web browser to the document in Silobreaker.
* Publisher and publication date - This line contains the document's original publisher as well as when the document was published. Clicking on this line will open a new tab to the original published source.
* Document teaser - The first few lines from the document.

### Document Evidence For Link (Including pastes)
> Any Silobreaker entity &rarr; Link to Evidence `silobreaker.Document`

> Find document evidence for inbound link (including pastes)

This transform will return paste documents in addition to the other documents that would otherwise be retrieved with [Document Evidence For Link](#document-evidence-for-link).

___
[^1]: You must have a Silobreaker user account to view the user guide.
