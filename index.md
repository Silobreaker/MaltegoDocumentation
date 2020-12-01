---
layout: index
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
![](https://i.gyazo.com/197887dd031cc549dfe9c961f7025a4d.png)   
    This screen can also be accessed from the transform-picker.
7. You're now ready to use all of the Silobreaker transforms.
  
# Using the Silobreaker transforms in Maltego

### Pre-requisites

Some of our transforms uses **lists** from Silobreaker. For these transforms to work, the API key must belong to an account with the following Silobreaker lists (check availability under My Lists in Silobreaker Premium):

* Attack Types
* Hacker OPs
* Malicious IPs

## Association/relation Transforms

Silobreaker indexes millions of documents and searches these to find mentions of _entities_. Our Maltego transforms use our _In Focus_-API to find entities that are related to your input. An entity is _related_ to another when mentioned in the same context. If you need more information about how this relation was extracted, you can [investigate the relation](#investigating-relations).

### Entity transforms

These transforms will take __any__ type of entity as input.

#### Usernames
> Any &rarr; Usernames returns `silobreaker.Username`

> Find related @usernames

Finds @usernames that are associated with the seed entities. These are _usually_ Twitter-handles but can be from other services that use a similar naming system.

#### Countries
> Any &rarr; Countries returns `maltego.Country`

> Find related Countries

Find countries that are associated with the seed entities. These countries are not necessarily the country the entities came from or where the story originated; the relationship only indicates that the seed and the country are frequently mentioned in the same documents.

#### Cities
> Any &rarr; Cities returns `maltego.City`

> Find related Cities

Finds cities that are _associated_ with the seed entities. This _association_ is based on the fact that the seed and the Cities are frequently mentioned in the same context, in the same documents - not necessarily any actual origin or location. 

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

#### Related Entities
> Any &rarr; returns Any

> Find related Entities of any type

Takes any type of entity as seed and outputs the most related entities, across all Silobreaker entity types. The type of the returning entity will be the same type as if the specific transform was used. Eg. related domains will return as `maltego.DNSname`, which is what [_To Domains_](#to-domains) returns.

#### Related Documents
> Any &rarr; Documents returns `silobreaker.Document`

> Find documents that are related to the seed

Returns the documents that are the most related to your seed. The returned documents contains the URL to the original document on source website as well as Silobreaker URL for further analysis. The documents also include a detail view with the title and teaser.

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

#### Keyphrases

> Any &rarr; Keyphrases returns `maltego.Phrase`

> Find relevant Keyphrases within Silobreaker

Find phrases that are _keyphrases_ within Silobreaker. _Keyphrases_ in Silobreaker are words or phrases that are key to the content of the document. 

![to-keyphrase](images/to-keyphrase.png)

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

#### Pastes
> Any &rarr; Pastes returns `silobreaker.Document`

> Find pastes from Pastebin that are related to the seed

Returns the pastes that are the most related to your seed. The document contains URL to original paste on pastebin.com.

### Cybersecurity Entity Transforms

These transforms work just as the more general transforms above but are focused on cyber-security.

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

![to-malware](images/to-malware.png)

#### Malicious IPs
> Any &rarr; Malicious IPs returns `maltego.IPv4Address`

> Finds related malicious IP-addresses on Silobreaker

Silobreaker maintains lists of IPs that have been reported as _Malicous_. This will let you find Malicious IPs that are associated with the seed.

This finds _Malicous_ _IPs_ that are listed as such in Silobreaker's internal lists.

#### Attack Types
> Any &rarr; Attack Types returns `maltego.Phrase`

> Find related Attack Types, eg. 'Bootkit' or 'HTML-injection'

Silobreaker maintains lists of attack types, this finds the Attack Types which is most frequently mentioned in association with the seed.

#### Threat Actor
> Any &rarr; Threat Actor returns `silobreaker.ThreatActor`

> Find related Threat Actors

Threat Actor is a person or a group of individuals that poses a cyber security threat, such as a hacktivist groups or state sponsored hackers. 

  ![to-threat-actor](images/to-threat-actor.png)

#### Hacker Ops
> Any &rarr; Hacker Ops returns Any

> Find Hacker Operations or 'Ops' that are related to your seed

Hacker Operation or 'Ops' are joint efforts or rushes to attack specific targets; eg. [Operation Antisec](https://en.wikipedia.org/wiki/Operation_AntiSec). Silobreaker automatically identifies and tracks these Operations. This transform allows you to find operations that are related to the seed.

## Matching Entities
> Any &rarr; returns Any

> Finds entities with names or aliases that matches the seed

This special transform makes a general search to find Entities that match your
seed. This only returns Entities with name or alias that __match__ your seed,
__not__ entities that are related or associated to it. You can also use this to
pull entities from a list you have access to by prefixing the list name with
"list:", e.g. to get entities from the list "CVE2014" you name your input
entity "list:CVE2014".

## Investigating Relations

### Document Evidence for Link
> Any Silobreaker Entity &rarr; Link to Evidence `silobreaker.Document`

> Use on entities created by Silobreaker Transforms. Will create links to evidence for said transform

This special transform is used to investigate relations. If you have used any of the _To [...]_ transforms on a Silobreaker entity to find related entities you can use the _Document Evidence for Link_ on the children to find documents that outline the relationship between that child and it's seed.

**Note**: You can only find evidence documents for transforms that was performed on a Silobreaker entity. Any entity returned by another Silobreaker transform is a Silobreaker entity. 

1. Ensure the **initial entity** is a Silobreaker entity. If you want to use your input as initial entity, then perform [Search Entity](#search-entities) on your phrase.

    ![search-entities](images/search-entities.png)
  
2. Use any of the Silobreaker  `To [...]` transforms to find related entities.

    ![search-entities-to-company](images/search-entities-to-company.png)
  
  _**To Companies** used on **Derusbi**_.

3. On any of the generated child nodes, perform the _Document Evidence for Link_ transform.
4. The children that are generated are `silobreaker.Documents` containing url's to the documents that generated this relation on Silobreaker.

    ![document-evidence](images/document-evidence.png)
  
  _So these are the original documents where the relationship between **Derusbi** and **Microsoft Corporation** is established._

### Document Evidence for Link (Including pastes)
> Any Silobreaker Entity &rarr; Link to Evidence `silobreaker.Document`

> Use on entities created by Silobreaker Transforms. Will create links to evidence for said transform

Same as `Document Evidence for Link` including paste results.