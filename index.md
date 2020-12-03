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

Acquiring and installation
----------

If you wish to receive a demo or contact our sales team, please see our [contact information](http://www.silobreaker.com/contact-us/).

If you have a license that includes Maltego access, Silobreaker will provide the API-keys for you to use.

#### Installation:

1. Launch Maltego and navigate to the home screen. This should show on launch if you have not switched to any other screens.
2. Find Silobreaker in the grid of transforms.
3. Press the `Install`-button.
4. Navigate through the short installation process.
5. Still on the _Transform Hub_, press the now displayed `settings`-button for Silobreaker.
6. This will show a dialog where you will have to paste your own API key.   
7. You're now ready to use all of the Silobreaker transforms.
  
# Using the Silobreaker transforms in Maltego

### Pre-requisites

Some of our transforms uses **lists** from Silobreaker. For these transforms to work, the API key must belong to an account with the following Silobreaker lists (check availability under My Lists in Silobreaker Premium):

* Hacktivist Operations

### Entities
Installing Silobreaker transforms also includes a custom entity set. Our transforms can return both Maltego and Silobreaker entities depending on the transform being used. Maltego entities are used when the returned entity type exists in both Maltego and Silobreaker. Otherwise, a Silobreaker custom entity will be returned. In both cases the returned entity will have a Silobreaker icon. Visit our [user guide](https://my.silobreaker.com/Help-v2/basics/entities/#entity-types) to read more about our entities [^1].

## Association/relation Transforms

Silobreaker indexes millions of documents and searches these to find mentions of _entities_. Our Maltego transforms use our API to find entities that are related to your input. An entity is _related_ to another when mentioned in the same context. If you need more information about how this relation was extracted, you can [investigate the relation](#investigating-relations).

### General Transforms

These transforms will take __any__ type of entity as input.

#### Keyphrases

> Any &rarr; Keyphrases returns `maltego.Phrase`

> Find relevant Keyphrases within Silobreaker

Find phrases that are _keyphrases_ within Silobreaker. _Keyphrases_ in Silobreaker are words or phrases that are key to the content of the document. 

![keyphrases](images/keyphrases.png)

#### Persons
> Any &rarr; Persons returns `maltego.Person`

> Find associated people

Returns people that are frequently mentioned in the same context as the seed.

#### Companies
> Any &rarr; Companies returns `maltego.Company`

> Find related companies

#### Organizations
> Any &rarr; Organizations returns `maltego.Organization`

> Find related organizations

#### Products
> Any &rarr; Products returns `silobreaker.Product`

> Find related products

### Cyber Transforms

These transforms work just as the more general transforms above but are focused on cyber-security.

#### Credit Cards
> Any &rarr; Credit Cards returns `silobreaker.CreditCard`

> Find Credit Cards identified by Silobreaker

Credit card numbers are automatically identified by Silobreaker and are usually found in CC dumps on paste sites.

#### IIN
> Any &rarr; IIN returns `silobreaker.IIN`

> Find IINs identified by Silobreaker

An IIN, issuer identification number, also often referred to as BIN - bank identiciation number. The IIN are the first 6 digits of a credit card and uniquely identifies card issuer and issuing bank. 

#### Hashtags
> Any &rarr; Hashtags returns `silobreaker.HashTag`

> Find related #Hashtags

Silobreaker automatically finds [hashtags](https://en.wikipedia.org/wiki/Hashtag) based on their formatting, `#example`. While these are usually hashtags on social media, such as twitter, they could be anything using the same formatting. For example IRC use a hashtag format to identify #channel names.

#### Usernames
> Any &rarr; Usernames returns `silobreaker.Username`

> Find related @usernames

Finds @usernames that are associated with the seed entities. These are _usually_ Twitter-handles but can be from other services that use a similar naming system.

#### IPv4s
> Any &rarr; IPv4-addresses returns `maltego.IPv4Address`

> Find related IPv4-addresses

Find IP-addresses that are often mentioned in association as your seed. This association is only based on mentions in documents and is not any type of look-up.

#### Email Addresses
> Any &rarr; Email Addresses returns `maltego.EmailAddress`

> Find related Email-Addresses

#### Domains
> Any &rarr; Domains returns `maltego.Domain`

> Find related domains

Domains such as `facebook.com`, `silobreaker.se` or `plus.google.com` extracted from documents matching the seed.

#### Email Domains
> Any &rarr; Email Domains returns `silobreaker.EmailDomain`

> Find related email domains

A email domain is attached to an email address and differs from domain in that it is contextual and only extracted as part of extracting email address entities. 

#### URLs
> Any &rarr; URLs returns `maltego.URL`

> Finds related URLs. Includes the entire path mentioned

Eg. `https://www.facebook.com/example/page/b.0120201030120.01230123010231.012301230/` or `http://t.co/123456abc`.

#### Vulnerabilities
> Any &rarr; CVE-identifiers returns `silobreaker.Vulnerability`

> Find Vulnerabilities listed by CVE identifier

Silobreaker maintains a complete list known vulnerabilities that have been acknowledged and given a  [CVE](https://en.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures) identifier. This transform finds the vulnerabilities that are the most related to your seed.

#### Hashes
> Any &rarr; Hashes returns `silobreaker.Hash` 

> Find related hashes

Silobreaker automatically identifies strings that matches the length and content of [MD5](https://en.wikipedia.org/wiki/MD5) or [SHA](https://en.wikipedia.org/wiki/Secure_Hash_Algorithm). This transform finds the hashes that are the most related to the seed.

#### Malware
> Any &rarr; Malware returns `silobreaker.Malware`

> Find related malware, identified by their popularised name

This returns known malware by their names, often given by the security company that discovers them. 

![malware](images/malware.png)

#### Malicious IPs
> Any &rarr; Malicious IPs returns `maltego.IPv4Address`

> Find IP addresses related to various malicious activity e.g., Malware or Threat Actors

This will let you find IPs which are associated with different Threat Actors and Malware. They may not necessarily be _malicious_ IP addresses, but they will be contextualized by malicious activity.

#### Attack Types
> Any &rarr; Attack Types returns `maltego.Phrase`

> Find related Attack Types, eg. 'Bootkit' or 'HTML-injection'

This finds the Attack Types which are most frequently mentioned in association with the seed.

#### Threat Actor
> Any &rarr; Threat Actor returns `silobreaker.ThreatActor`

> Find related Threat Actors

Threat Actor is a person or a group of individuals that poses a cyber security threat, such as a hacktivist groups or state sponsored hackers. 

  ![threat-actor](images/threatactors.png)

#### Hacker Ops
> Any &rarr; Hacker Ops returns Any

> Find related cyber entities from the "Hacktivist Operations" list in SB.

Hacker Operation or 'Ops' are joint efforts or rushes to attack specific targets; eg. [Operation Antisec](https://en.wikipedia.org/wiki/Operation_AntiSec). Silobreaker automatically identifies and tracks these Operations. This transform allows you to find operations that are related to the seed.

### Geo Transforms

#### Countries
> Any &rarr; Countries returns `maltego.Country`

> Find related Countries

Find countries that are associated with the seed entities. These countries are not necessarily the country the entities came from or where the story originated; the relationship only indicates that the seed and the country are frequently mentioned in the same documents.

#### Cities
> Any &rarr; Cities returns `maltego.City`

> Find related Cities

Finds cities that are _associated_ with the seed entities. This _association_ is based on the fact that the seed and the cities are frequently mentioned in the same context, in the same documents - not necessarily any actual origin or location. 

#### Provinces 
> Any &rarr; Provinces returns `silobreaker.Province`

> Find related Provinces 

Finds provinces that are _associated_ with the seed entities. 

#### Regions 
> Any &rarr; Regions returns `silobreaker.Region`

> Find related Regions 

Finds regions that are _associated_ with the seed entities. 

#### World Regions 
> Any &rarr; World Regions returns `silobreaker.WorldRegion`

> Find related World Regions 

Finds world regions that are _associated_ with the seed entities. 

### Search Transforms

#### Matching Entities
> Any &rarr; returns Any

> Find matching SB entities.

This special transform makes a general search to find Entities that match your
seed. This only returns Entities with name or alias that __match__ your seed,
__not__ entities that are related or associated to it. You can also use this to
pull entities from a list you have access to by prefixing the list name with
"list:", e.g. to get entities from the list "CVE2014" you name your input
entity "list:CVE2014".

#### Related Entities
> Any &rarr; returns Any

> Find related Entities of any type

Takes any type of entity as seed and outputs the most related entities, across all Silobreaker entity types. The type of the returning entity will be the same type as if the specific transform was used. Eg. related domains will return as `maltego.DNSname`, which is what [_To Domains_](#to-domains) returns.

#### Related Documents
> Any &rarr; Documents returns `silobreaker.Document`

> Find related Documents

Returns the documents that are the most related to your seed. The returned documents contains the URL to the original document on source website as well as Silobreaker URL for further analysis. The documents also include a detail view with the title and teaser.

#### Related Pastes
> Any &rarr; Pastes returns `silobreaker.Document`

> Find related Pastes

Returns the pastes that are the most related to your seed. The document contains a URL to the original paste site.

#### Related Publications

> Any &rarr; returns `silobreaker.Publication`

> Find related Publications

Returns the Publications that are related to the input. The Properties of the returned Publications will include its own Item ID in Silobreaker as well as the Item ID of its Parent.

## Investigating Relations

### Document Evidence for Link
> Any Silobreaker Entity &rarr; Link to Evidence `silobreaker.Document`

> Use on entities created by Silobreaker Transforms. Will create links to evidence for said transform

This special transform is used to investigate relations. If you have used any of the entity transforms on a Silobreaker entity to find related entities you can use the _[SB] Document Evidence For Link_ on the children to find documents that outline the relationship between that child and it's seed.

1. Insert an entity and use any of the Silobreaker entity transforms to find related entities.

    ![companies](images/companies.png)
  
  _**[SB] Companies** used on **Derusbi**_.

2. On any of the generated child nodes, perform the _[SB] Document Evidence For Link_ transform.
3. The children that are generated are `silobreaker.Documents` containing url's to the documents that generated this relation on Silobreaker.

    ![document-evidence-for-links](images/documentevidenceforlink.png)
  
  _So these are the original documents where the relationship between **Derusbi** and **Cisco Systems Inc** is established._

### Document Evidence For Link (Including pastes)
> Any Silobreaker Entity &rarr; Link to Evidence `silobreaker.Document`

> Use on entities created by Silobreaker Transforms. Will create links to evidence for said transform

Same as `Document Evidence For Link` including paste results.

___
[^1]: You must have a Silobreaker user account to view the user guide.
