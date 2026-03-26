# Ads.txt Version 1.1

## About ads.txt 

The ads.txt Specification was developed in the spring of 2017. This document is the final ads.txt Specification Version 1.1; a peer-reviewed standard developed with the support of the Programmatic Supply Chain working group. This document is available at [https://iabtechlab.com/ads-txt](https://iabtechlab.com/ads-txt). 
  
The ads.txt specification focuses on protecting advertising inventory hosted by the website publishing the ads.txt file by allowing publishers to publicly and transparently declare who is authorized to sell their inventory. To meet the requirements for software applications distributed through mobile app stores, connected television app stores, and other distribution channels of that nature, refer to the companion app-ads.txt specification, also available at [https://iabtechlab.com/ads-txt](https://iabtechlab.com/ads-txt). 

## About IAB Tech Lab 

The IAB Technology Laboratory is a nonprofit research and development consortium charged with producing and helping companies implement global industry technical standards and solutions. The goal of the Tech Lab is to reduce friction associated with the digital advertising and marketing supply chain while contributing to the safe growth of an industry. 
  
The IAB Tech Lab spearheads the development of technical standards, creates and maintains a code library to assist in rapid, cost-effective implementation of IAB standards, and establishes a test platform for companies to evaluate the compatibility of their technology solutions with IAB standards, which for 18 years have been the foundation for interoperability and profitable growth in the digital advertising supply chain. Further details about the IAB Technology Lab can be found at [https://iabtechlab.com](https://iabtechlab.com). 
  
### License 

Ads.txt by Programmatic Supply Chain Working Group is licensed under a Creative Commons Attribution 3.0 License. To view a copy of this license, visit creativecommons.org/licenses/by/3.0/ or write to Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA. 
 	 
### Disclaimer 
THE STANDARDS, THE SPECIFICATIONS, THE MEASUREMENT GUIDELINES, AND ANY OTHER MATERIALS OR SERVICES PROVIDED TO OR USED BY YOU HEREUNDER (THE “PRODUCTS AND SERVICES”) ARE PROVIDED “AS IS” AND “AS AVAILABLE,” AND IAB TECHNOLOGY LABORATORY, INC. (“TECH LAB”) MAKES NO WARRANTY WITH RESPECT TO THE SAME AND HEREBY DISCLAIMS ANY AND ALL EXPRESS, IMPLIED, OR STATUTORY WARRANTIES, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AVAILABILITY, ERROR-FREE OR UNINTERRUPTED OPERATION, AND ANY WARRANTIES ARISING FROM A COURSE OF DEALING, COURSE OF PERFORMANCE, OR USAGE OF TRADE. TO THE EXTENT THAT TECH LAB MAY NOT AS A MATTER OF APPLICABLE LAW DISCLAIM ANY IMPLIED WARRANTY, THE SCOPE AND DURATION OF SUCH WARRANTY WILL BE THE MINIMUM PERMITTED UNDER SUCH LAW. THE PRODUCTS AND SERVICES DO NOT CONSTITUTE BUSINESS OR LEGAL ADVICE. TECH LAB DOES NOT WARRANT THAT THE PRODUCTS AND SERVICES PROVIDED TO OR USED BY YOU HEREUNDER SHALL CAUSE YOU AND/OR YOUR PRODUCTS OR SERVICES TO BE IN COMPLIANCE WITH ANY APPLICABLE LAWS, REGULATIONS, OR SELF-REGULATORY FRAMEWORKS, AND YOU ARE SOLELY RESPONSIBLE FOR COMPLIANCE WITH THE SAME, INCLUDING, BUT NOT LIMITED TO, DATA PROTECTION LAWS, SUCH AS THE PERSONAL INFORMATION PROTECTION AND ELECTRONIC DOCUMENTS ACT (CANADA), THE DATA PROTECTION DIRECTIVE (EU), THE E-PRIVACY DIRECTIVE (EU), THE GENERAL DATA PROTECTION REGULATION (EU), AND THE E-PRIVACY REGULATION (EU) AS AND WHEN THEY BECOME EFFECTIVE. 
   
### Significant Contributors to the 1.1 Release: 

Justin Adler-Swanberg, Director Marketplace Quality, MediaMath; Paul Bannister, Chief Strategy Officer, CafeMedia; Per Bjorke, Group Product Manager, Google; Eric Bozinny, Sr Director Marketplace Quality, Pubmatic; Katie Chang, Sales Operations & Strategy Lead, Yahoo; Zack Dugow, Founder and CEO, Insticator; Emma Fenlon, Sr. Manager Exchange Quality, Yahoo; Jeremy Grant, Sr. Product Manager, Index Exchange; Chris Kane, Founder, Jounce Media; Curt Larson, Chief Product Officer, Sharethrough; Curtis Light, Staff Software Engineer, Google; Don Marti, VP Ecosystem Innovation, CafeMedia; Kristen Moegling, Sr. Technical Solutions,Triplelift; Angie Pennington, Sales and Operations Strategy Lead, Yahoo; Neal Richter, Director, Advertising Science, Amazon DSP, Jud Spencer, Principal Lead Software Engineer, The Trade Desk; Brian Van Horne, Director of Engineering, Magnite;  Jean-Luc Wasmer, VP Partnership Integrations, Triton Digital; Liam Whiteside, Head of Ad Technology, Global; Anna Wolk, Marketplace Quality, The Trade Desk; 
  
### IAB Tech Lab Lead: 

Hillary Slattery, Senior Director, Programmatic, Product Management, IAB Tech Lab 
  
## TABLE OF CONTENTS  
 
- [ABOUT IAB TECH LAB](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#about-iab-tech-lab)	
- 2. [INTRODUCTION](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#2-introduction)	
    - 2.1 [CHANGE LOG](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#21-change-log)	
- 3. [SPECIFICATION](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#3-specification)	
    - 3.1 [ACCESS METHOD](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#31-access-method)	
    - 3.2 [FILE FORMAT](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#32-file-format)	
        - 3.2.1 [FILES WITHOUT AUTHORIZED ADVERTISING SYSTEM RECORDS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#321-files-without-authorized-advertising-system-records)	
    - 3.3 [THE DATA RECORD](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#33-the-data-record)	
    - 3.4 [SYNTAX DEFINITION](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#34-syntax-definition)	
        - 3.4.1 [COMMENTS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#341-comments)	
        - 3.4.2 [THE RECORD](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#342-the-record)	 
        - 3.4.3 [EXTENSION FIELDS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#343-extension-fields)	
    - 3.5 [VARIABLE DECLARATION RECORDS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#35-variable-declaration-records)	
        - 3.5.1 [SUPPORTED VARIABLES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#351-supported-variables)	
    - 3.6 [EXPIRATION	](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#36-expiration)
- 4. [EXAMPLES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#4-examples)	
    - 4.1 [SINGLE SYSTEM DIRECT](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#41-single-system-direct)	
    - 4.2 [SINGLE SYSTEM RESELLER](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#42-single-system-reseller)	
    - 4.3 [MULTIPLE SYSTEMS AND RESELLERS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#43-multiple-systems-and-resellers)	
    - 4.4 [CONTACT RECORDS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#44-contact-records)	
    - 4.5 [SUBDOMAIN REFERRAL](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#45-subdomain-referral)	
    - 4.6 [INVENTORYPARTNERDOMAIN REFERRAL](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#46-inventorypartnerdomain-referral)	
    - 4.7 [OWNERDOMAIN USAGE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#47-ownerdomain-usage)
    - 4.8 [MANAGERDOMAIN USAGE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#48-managerdomain-usage)
    - 4.9 [FILE WITHOUT AUTHORIZED ADVERTISING SYSTEMS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#49-file-without-authorized-advertising-systems)	
- 5. [IMPLEMENTER’S NOTES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#5-implementers-notes)	
    - 5.1 [VERSION](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#51-version)	
    - 5.2 [GUIDANCE BY PARTY](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#52-guidance-by-party)	
        - 5.2.1 [SSP/EXCHANGE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#521-sspexchange)	
        - 5.2.2 [DSP](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#522-dsp)	
        - 5.2.3 [PUBLISHERS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#523-publishers)	
    - 5.3 [INTEROPERABILITY](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#53-interoperability)	
    - 5.4 [SECURITY](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#54-security)	
    - 5.5 [SUBDOMAIN DIRECTIVES	](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#55-subdomain-directives)
    - 5.6 [ADS.TXT CRAWLERS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#56-adstxt-crawlers)	
    - 5.7 [INVENTORYPARTNERDOMAIN DIRECTIVES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#57-inventorypartnerdomain-directives)	
    - 5.8. [OWNERDOMAIN DIRECTIVE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#58-ownerdomain-directive)	
    - 5.9 [MANAGERDOMAIN DIRECTIVE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#59-managerdomain-directive)	
- 6. [SCOPE AND FUTURE DIRECTIONS ](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#6-scope-and-future-directions)
    - 6.1 [SCOPE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#61-scope)	
    - 6.2 [OPEN ISSUES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#62-open-issues)	
    - 6.3 [FUTURE DIRECTIONS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#63-future-directions)	
- 7. [ACKNOWLEDGEMENTS](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#7-acknowledgements)	
- 8. [REFERENCES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md#8-references)	

 	 
## 1. ABSTRACT 
  
As part of a broader effort to eliminate the ability to profit from counterfeit inventory in the open digital advertising ecosystem, provide a mechanism to enable content owners to declare who is authorized to sell their inventory. 

## 2. INTRODUCTION 
  
For brevity, we’ll assume readers are already familiar with the problem of fraud in ad tech and its vast scale [1][2][3].  Fraud can come in various forms, here we are concentrating on the form wherein ad inventory is being offered to buyers with a misrepresented label and account during the real-time bidding process.  Typically the domain of the webpage, or the ID of the mobile app has been falsified to look like a site or app they do not have authorization to sell. 
  
Here, we propose a new standard to enable content owners to explicitly declare a set of advertising systems and resellers who are authorized to sell their inventory. This will enable buyers to acquire advertising space through safe supply chains via authorized entities. 
  
### 2.1 CHANGE LOG 
  
|Version |	Date |	Changes |
|---|---|---|
|1.0 |	June 27, 2017 |	First Version |
|1.0.1 |	August 30, 2017 |	Minor revisions based upon community feedback. Clarifications in 3.1 and adding support for contact and subdomain variables in 3.2 3.5, 4.4, 4.5 and 5.5. |
|1.0.2 |	March 4, 2019 |	Minor revisions based upon community feedback. Adds 3.2.1 and 4.7 containing guidance for using a placeholder record to indicate the intent of an empty ads.txt file, deprecating the prior method. Adds differentiation between ads.txt and app-ads.txt in the “about” section. |
|1.0.3 |	December 2020 public comment March 2021 – final release |	Added the “inventorypartnerdomain” directive (and more detail in 4.6 & 5.7) to aid with CTV and similar use cases. |
|1.1 |	April 2022 public comment July 2022 final release |	Added the “managerdomain” and “ownerdomain” variables (more details in 3.5.1, 4.7, 4.8, 5.8 and 5.9) |
  
  
 	  
## 3. SPECIFICATION 
 
This memo specifies a mechanism for publisher content distributors to publicly declare their authorized advertising systems and identifiers within those systems.  This specification is meant to be used in partnership with site.domain or app.bundle within OpenRTB bid requests, or equivalent information in other transaction methods. It also describes the format for encoding the instructions to be consumed by advertising systems and their customers.   Advertising systems should retrieve these declarations before buying or selling advertising claiming to be on the website. 
  
This specification is specifically inspired by the robots.txt standard [5][6].  A key attribute is that the file is posted to the web serving system of the content, thus proving that the website authored the file.  We refer the reader to various other advertising API specifications such as IAB Tech Lab’s OpenRTB [7] and Google’s AdX API [8] for real-time ad space sales and IAB Tech Lab’s OpenDirect [9] for non real-time sales. 

### 3.1 ACCESS METHOD 

Publishers should post the "/ads.txt" file on their root domain and any subdomains as needed.  For the purposes of this document the “root domain” is defined as the “public suffix” plus one string in the name. Crawlers should incorporate Public Suffix list [16] to derive the root domain. 
  
The declarations must be accessible via HTTP and/or HTTPS from the website that the instructions are to be applied to under a standard relative path on the server host: "/ads.txt" and HTTP request header containing "Content-Type: text/plain".  It may be advisable to additionally use "Content-Type: text/plain; charset=utf-8" to signal UTF8 support.  
  
It is also advisable to prefer HTTPS connections over HTTP when crawling ads.txt files. In any case where data is available at an HTTPS and an HTTP connection for the same URL, the data from HTTPS should be preferred. 
 
For convenience we will refer to this resource as the "/ads.txt" file, though the resource need in fact not originate from a file-system. 
  
If the server response indicates Success (HTTP 2xx Status Code,) the advertising system must read the content, parse it, and utilize the declarations. 
  
If the server response indicates an HTTP/HTTPS redirect (301, 302, 307 status  codes), the advertising system should follow the redirect and consume the data as authoritative for the source of the redirect, if and only if the redirect is within scope of the original root domain as defined above.  Multiple redirects are valid as long as each redirect location remains within the original root domain.  For example an HTTP to HTTPS redirect within the same root domain is valid.  
  
Only a single HTTP redirect to a destination outside the original root domain is allowed to facilitate one-hop delegation of authority to a third party's web server domain. If the third party location returns a redirect, then the advertising system should treat the response as an error.  A future version may address other delegation of authority to a third-party web server. Any other redirect should be interpreted as an error and ignored. 
  
If the server response indicates the resource is restricted (HTTP 401) the advertising system should seek direct contact with the site for authorization keys or clarification. 
  
If the server response indicates the resource does not exist (HTTP Status Code 404), the advertising system can assume no declarations exist and that no advertising system is unauthorized to buy and sell ads on the website.  For any other HTTP error encountered for a URL which the crawler previously found data, the last successfully retrieved data set should be utilized. 

### 3.2 FILE FORMAT 
  
The data is encoded as a formatted plain text object, described here. The HTTP Content-type should be ‘text/plain’, and all other Content-types should be treated as an error and the content ignored. A complete description of the syntax of this format is given in section 3.4 below. 
  
The format logically consists of: 

- A non-empty set of records, separated by line breaks. The records consist of a set of lines of the form: 
  
`<FIELD #1>, <FIELD #2>, <FIELD #3>, <FIELD #4>` 
  
or 
  
`<VARIABLE>=<VALUE> `
  
- Lines starting with # symbol are considered comments and are ignored. 
- Lines containing the data format have syntax defined in section 3.4 
- Lines containing the variable format have syntax defined in section 3.5 
  
#### 3.2.1 FILES WITHOUT AUTHORIZED ADVERTISING SYSTEM RECORDS 

Some publishers may choose to not authorize any advertising system by publishing an empty ads.txt file, indicating that no advertising system is authorized to buy and sell ads on the website. So that consuming systems properly read and interpret the empty file (differentiating between web servers returning error pages for the /ads.txt URL), at least one properly formatted line must be included which adheres to the format specification described above. For files that do not otherwise contain authorized advertising system records, use the following "placeholder" record to indicate that the file adheres to the ads.txt specification: 
  
`placeholder.example.com, placeholder, DIRECT, placeholder `
  
The domain "example.com" bears no significance: it is used here so that the line will start with a properly formatted, permanently reserved ([https://tools.ietf.org/html/rfc6761](https://tools.ietf.org/html/rfc6761)) alternative domain to a real advertising system domain. 
  
Prior versions of the ads.txt specification indicated that publishers may simply use an empty ads.txt file to indicate that no advertising system is authorized to buy or sell ads on the website. That method is now deprecated because of ambiguities it creates and should be ignored by consuming systems after March 1, 2020. 
  
### 3.3 THE DATA RECORD 

The following defines the contents within each field.  We refer to the IAB OpenRTB [7] and IAB OpenDirect [9] specs as needed. 
  
|FIELD |	NAME |	DESCRIPTION |
|---|---|---|
|Field #1 |	Domain name of the advertising system |	(Required) The canonical domain name of the SSP, Exchange, Header Wrapper, etc system that bidders connect to.  This may be the operational domain of the system, if that is different than the parent corporate domain, to facilitate WHOIS and reverse IP lookups to establish clear ownership of the delegate system. Ideally the SSP or Exchange publishes a document detailing what domain name to use. |
|Field #2 |	Publisher’s Account ID |	(Required) The identifier associated with the seller or reseller account within the advertising system in field #1.  This must contain the same value used in transactions (i.e. OpenRTB bid requests) in the field specified by the SSP/exchange.  Typically, in OpenRTB, this is publisher.id.  For OpenDirect it is typically the publisher’s organization ID. |
|Field #3 |	Type of Account/ Relationship |	(Required) An enumeration of the type of account.  A value of ‘DIRECT’ indicates that the Publisher (content owner) directly controls the account indicated in field #2 on the system in field #1.  This tends to mean a direct business contract between the Publisher and the advertising system.  A value of ‘RESELLER’ indicates that the Publisher has authorized another entity to control the account indicated in field #2 and resell their ad space via the system in field #1.  Other types may be added in the future.   Note that this field should be treated as case insensitive when interpreting the data. |
|Field #4 |	Certification Authority ID |	(Optional) An ID that uniquely identifies the advertising system within a certification authority (this ID maps to the entity listed in field #1).  A current certification authority is the Trustworthy Accountability Group (aka TAG), and the TAGID would be included here [11]. Declaration of certification IDs are superseded by the *identifiers* object in sellers.json. Note: This field may be deprecated in a future version of ads.txt. |
  
Note that if a parent company is operating multiple distinct SSP/Exchanges, the domain in field #1 should refer to the domain of the RTB connection that the bidder is receiving bid requests from. 
 
Certification IDs in Field #4 are connected to the “advertising system” (e.g., SSP) and it is preferred to declare within the sellers.json file. 
 
### 3.4 SYNTAX DEFINITION 

#### 3.4.1 COMMENTS 

Comment are denoted by the character "#".  Any line containing "#" should inform the data consumer to ignore the data after the "#" character to the end of the line. 
 
#### 3.4.2 THE RECORD 

The core syntax is a comma separated format with three defined fields and one record per line.  
  
The consumer systems should ignore any sequence of whitespace or tabs.  If the data is obviously corrupted or malformed the contents of the file should be ignored.  No field should contain tabs, commas or whitespace, otherwise it should be escaped with URL encoding [13]. 
  
Individual records are separated by an end-of-line marker.  The consumer systems should liberally interpret CR, CRLF etc as a record separator. 
  
The allowed identifiers in field #1 and by definition assumed to be valid DNS domain names obeying RFC 1123 [10], associated errata for RFC 1123 or subsuming RFCs. 
  
Identifiers in field #2 can be strings or integers. For reference OpenRTB’s publisher.id [14] is a string field. 

#### 3.4.3 EXTENSION FIELDS 

Extension fields are allowed by implementers and their consumers as long as they utilize a distinct final separator field ";" before adding extension data to each record. 

### 3.5 VARIABLE DECLARATION RECORDS 
Any line containing a pattern of `<VARIABLE>=<VALUE>` should be interpreted as a variable declaration and the crawler should store the data associated with the root domain. 
  
The `<VARIABLE>` is a string identifier without internal whitespace.  The only supported separator is the equals sign ‘=’.  The `<VALUE>` is an open string that may contain arbitrary data. 
  
The declaration line is terminated by the end-of-line marker.  The consumer systems should liberally interpret CR, CRLF etc as a line separator. 
  
For human readability it is recommended that variables be declared at the end of the file, but this is not a strict requirement and should not be assumed by crawlers. 

#### 3.5.1 SUPPORTED VARIABLES 

The following variables are officially supported. Other variables may be added in the future.  If the crawler finds multiple lines with the same variable it should read and store all of them associated with the root domain. 
  
|VARIABLE |	VALUE |	DESCRIPTION |
|---|---|---|
|CONTACT |	Contact information |	(Optional) Some human readable contact information for the owner of the file.  This may be the contact of the advertising operations team for the website.  This may be an email address, phone number, link to a contact form, or other suitable means of communication. |
|SUBDOMAIN |	Pointer to a subdomain file |	(Optional) A machine readable subdomain pointer to a subdomain within the root domain, on which an ads.txt can be found. The crawler should fetch and consume associate the data to the subdomain, not the current domain. This referral should be exempt from the public suffix truncation process.  Only root domains should refer crawlers to subdomains. Subdomains should not refer to other subdomains. |
|INVENTORYPARTNERDOMAIN |	A pointer to the domain of an entity that is explicitly authorized to monetize ads within the application's content.  The partner's corresponding ads.txt file will be hosted at this domain. |	(Recommended where relevant) When a site or an app contains ad inventory that is owned by another partner - the app or site may list all domains for those partners via this directive rather than the original method of maintaining a separate line for every relationship under that partner. It is expected that the INVENTORYPARTNERDOMAIN reference is followed to an ads.txt file only (not app-ads.txt). See the implementers notes for more details as this feature requires coordination with your advertising system.| 
|OWNERDOMAIN |	Specifies the business domain of the business entity that owns the domain/site/app (e.g., example.com owns example1.com, example2.com, etc.) |	(Recommended) This should be the same value as the sellers.domain in this Publisher’s entries in referenced sellers.json files. Like sellers.domain, this should be Public Suffix List+1, not a full hostname or a URL. For OpenRTB SupplyChain objects that are complete, the node representing the originating publisher (the node listed first in the schain object) should have sellers.domain that matches the OWNERDOMAIN. If more than one instance of this variable is included only the first should be used. It is recommended that this field is included even if the OWNERDOMAIN is the same as the domain on which the ads.txt file is found. It is also recommended that buyers mandate for sellers that are listed as BOTH in sellers.json to correctly list OWNERDOMAIN in all ads.txt files that they own OR represent.| 
|MANAGERDOMAIN |	Specifies the business domain of a primary or exclusive monetization partner of the publishers inventory |	(Optional, use only when relevant) When the owner of the site does not manage monetization either globally or in a specific country, the domain of the exclusive management company is included in this variable. Syntax of the domain is [PSL+1 domain, required], [ISO 3166-1 alpha-2 country code, optional, blank=global] This variable should only be used for a seller who is not the publisher but is the primary or exclusive programmatic seller for this site. This will typically only apply if the publisher is not selling their own inventory in the given market.  It is expected that ad opportunities monetized by the manager, the domain listed in MANAGERDOMAIN is also that of the node representing the originating publisher in a complete supply chain object. There can be more than one MANAGERDOMAIN value but only one per country. A global/default MANAGERDOMAIN should not have a country “extension” on the variable line. The default can be overridden by other entries with country extensions included. See example for country declaration format. Consult the implementation guide for details on use cases and potential SPO implications. |
 
### 3.6 EXPIRATION 

Consuming systems of /ads.txt should cache the files, but if they do they must periodically verify the cached copy is fresh before using its contents. 
 
Standard HTTP cache-control mechanisms can be used by both origin server and robots to influence the caching of the /ads.txt file.  Specifically, consumers and replicators should take note of HTTP Expires header set by the origin server. 
 
If no cache-control directives are present consuming systems should default to an expiry of 7 days. 

## 4. EXAMPLES 

As defined above there are three required fields.  The optional certification authority ID field is included in some of the examples. 

### 4.1 SINGLE SYSTEM DIRECT 

This example is a website with only one authorized system that is directly controlled/operated by the website owner. 
  
http://example.com/ads.txt 

`greenadexchange.com, XF7342, DIRECT, 5jyxf8k54 `
  
### 4.2 SINGLE SYSTEM RESELLER 

This example is a website with only one authorized system that is operated by a separate company doing resale of inventory.  Their advertising system is not registered with a Certification Authority, so the optional fourth field is omitted. 
  
http://example.com/ads.txt 

`redssp.com, 57013, RESELLER` 
 
### 4.3 MULTIPLE SYSTEMS AND RESELLERS 

This example is a website with multiple authorized systems and multiple resellers.  Some of their authorized advertising systems are registered with a Certification Authority and have an ID issued. 
  
http://example.com/ads.txt 

```
# ads.txt file for example.com: 
greenadexchange.com, 12345, DIRECT, d75815a79 
silverssp.com, 9675, RESELLER, f496211 
blueadexchange.com, XF436, DIRECT 
orangeexchange.com, 45678, RESELLER 
silverssp.com, ABE679, RESELLER
``` 
  
### 4.4 CONTACT RECORDS 

This example is a website with multiple authorized systems and multiple contact records.  
  
http://example.com/ads.txt 

```
# ads.txt file for example.com: 
greenadexchange.com, 12345, DIRECT, d75815a79 
blueadexchange.com, XF436, DIRECT 
contact=adops@example.com 
contact=http://example.com/contact-us
``` 
  
### 4.5 SUBDOMAIN REFERRAL 

This example is a website that refers the crawler to a subdomain with a different set of authorized systems. The crawler should take the subdomain as another URL to fetch data from and associate to the subdomain and NOT the parent domain. 
  
http://example.com/ads.txt 

```
# ads.txt file for example.com: 
greenadexchange.com, 12345, DIRECT, d75815a79 
blueadexchange.com, XF436, DIRECT 
subdomain=divisionone.example.com
```
 
http://divisionone.example.com/ads.txt 

```
# ads.txt file for divisionone.example.com: 
silverssp.com, 5569, DIRECT, f496211 
orangeexchange.com, AB345, RESELLER
``` 
  
### 4.6 INVENTORYPARTNERDOMAIN REFERRAL 

This example is an app (or a website) that refers the crawler to an “inventory partner” with a different set of authorized systems. The crawler should take the *inventorypartnerdomain* as a domain and construct an ads.txt URL to fetch data from the partner’s ads.txt file and and associate it to the app (or website)’s authorized sellers list. 

For more detailed implementation information and scenarios, please refer to the implementation guide: [https://iabtechlab.com/wp-content/uploads/2021/03/ctv-app-ads-explainer-guide.pdf](https://iabtechlab.com/wp-content/uploads/2021/03/ctv-app-ads-explainer-guide.pdf)  Note - Any inventorypartnerdomain entries in the second ads.txt file should NOT be processed (only follow one hop) 
  
http://devsite.vMVPDB.com/app-ads.txt 

```
# app-ads.txt file for vMVPD B: 
ssp.com, vwxyz, DIRECT 
inventorypartnerdomain=programmerA.com
```
  
http://programmerA.com/ads.txt 

```
# ads.txt file for Programmer A 
ssp.com, abcde, DIRECT
``` 

When moving from a traditional ads.txt/app-ads.txt model to the inventorypartnerdomain directive, the file changes will reflect: 
  
**BEFORE**

vMVPDB must list every seller account on Programmer A’s ads.txt file to authorize those accounts to sell the inventory: 

http://devsite.vMVPDB.com/app-ads.txt 

```
# app-ads.txt file for vMVPD B: 
ssp.com, vwxyz, DIRECT 
ssp.com, abcde, DIRECT 
ssp.com, fghij, RESELLER 
ssp.com, klmno, RESELLER 
ssp.com, pqrst, RESELLER
```

http://programmerA.com/ads.txt 


```# ads.txt file for Programmer A: 
ssp.com, abcde, DIRECT 
ssp.com, fghij, RESELLER 
ssp.com, klmno, RESELLER 
ssp.com, pqrst, RESELLER
```
  
**AFTER**

vMVPDB only needs to point to Programmer A’s domain to authorize every seller account on Programmer A’s ads.txt (NOT app-ads.txt) file to sell the inventory: 

http://devsite.vMVPDB.com/app-ads.txt 

```
# app-ads.txt file for vMVPD B: 
ssp.com, vwxyz, DIRECT 
inventorypartnerdomain=programmerA.com
```
  
### 4.7 OWNERDOMAIN usage 
 
The OWNERDOMAIN variable will be used to connect the sellers.domain in a sellers.json file to the domain on which the ads.txt file is found. It is recommended, for clarity, that this value is included in every ads.txt file even if the OWNERDOMAIN does not differ from the domain on which the ads.txt file is hosted. 
 
If this variable is absent, it should be assumed that the OWNERDOMAIN is the same as the domain being monetized and where the ads.txt file was found. 
 
For more detailed implementation information and scenarios, please refer to the implementation guide: [https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf](https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf)  
 
In this example “MediaCompany.com” is the business owner of “example.com”. Therefore, the example.com/ads.txt file includes an entry to specify the business owner. 
 
http://example.com/ads.txt  

```
OWNERDOMAIN=mediacompany.com 
greenadexchange.com, XF7342, DIRECT, 5jyxf8k54
 ```
 
### 4.8 MANAGERDOMAIN usage  

The MANAGERDOMAIN variable should be used to represent a publisher’s relationship with a primary or exclusive monetization partner. In these instances, the MANAGERDOMAIN should be the most direct path to purchase the publisher’s inventory. 
For more detailed implementation information and scenarios, please refer to the implementation guide: [https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf](https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf) 
 
http://example.com/ads.txt  

```
OWNERDOMAIN=mediacompany.com 
MANAGERDOMAIN=yellowmediamanager.com, FR 
MANAGERDOMAIN=bluemediamanager.com, US 
 
greenadexchange.com, XF7342, DIRECT, 5jyxf8k54
```

### 4.9 FILE WITHOUT AUTHORIZED ADVERTISING SYSTEMS 

This example is a website that does not publish any authorized advertising systems, reflecting this intent within a properly formatted ads.txt file. 
  
http://example.com/ads.txt 
```
placeholder.example.com, placeholder, DIRECT, placeholder 
```
  
## 5. IMPLEMENTER’S NOTES 

### 5.1 VERSION 

This is version 1.1 of the specification and every attempt will be made to make future versions backward compatible if possible. 

### 5.2 GUIDANCE BY PARTY 

#### 5.2.1 SSP/EXCHANGE 

SSPs and exchanges should decide which canonical domain they wish to be used in field #1. They should make documentation available to publishers and DSPs. Publisher-facing documentation should indicate how publishers can retrieve the appropriate ID for field #2. DSPfacing documentation should indicate which field in bid requests should be used by DSPs for checking against the ads.txt file. 

It is recommended that any system creating OpenRTB bid requests place the seller’s account ID in the Publisher.ID field. Also ensure that the Site.Domain field is populated with the domain that hosts an ads.txt file where the account ID is publicly posted. 
  
Ideally, implementing SSPs/exchanges should provide a tool to generate the exact lines for a publisher to place in the ads.txt file. SSPs/exchanges should also consider crawling publishers’ domains and notifying publishers (e.g. a warning in the publisher dashboard, e-mail, etc.) of the absence of an ads.txt file or the absence of appropriate declarations in the file. 

#### 5.2.2 DSP 

DSPs should consult documentation provided by SSPs/exchanges as to the canonical domain used by the exchange (field #1) and the appropriate field in bid requests to be checked against ads.txt (field #2). 

#### 5.2.3 PUBLISHERS 

Publishers should consult documentation provided by SSPs/exchanges as to the canonical domain used by the exchange (field #1) and the appropriate ID to place in field #2. 

### 5.3 INTEROPERABILITY 

Implementers should pay particular attention to the robustness in parsing of the /ads.txt file. It is expected that the /ads.txt files are created with automated systems or manual platform-specific text editors consumers of the data should be liberal in accepting files with different end-of-line conventions, specifically CR and LF in addition to CRLF and varying whitespace or field separation characters. 

### 5.4 SECURITY 
The /ads.txt declarations are retrieved and applied in separate, possibly unauthenticated HTTP transactions, and it is possible that one server can impersonate another or otherwise intercept a request for /ads.txt, and provide a consuming system with false information. 
  
If this is a worry then the website owner should redirect unsecure http requests to https requests for the /ads.txt file. 

### 5.5 SUBDOMAIN DIRECTIVES 

When writing crawlers, implementers should request the /ads.txt from the root domains that are driving significant requests for advertising.  Publishers should always post the /ads.txt file on their root domain.  The crawler should strip the subdomains when creating the crawler’s URL list.  The public suffix list [12][16] should be utilized in implementing subdomain stripping. 
  
In cases where specific subdomains have different authorized advertising systems, the publisher should post ads.txt files only on those subdomains and declare each of those subdomains explicitly in the ads.txt on the root domain using the "subdomain=" variable.  Crawlers should only crawl for ads.txt files on subdomains that are listed using the "subdomain=" variable in the ads.txt on the root domain. 
 
When the ads.txt on the root domain declares a subdomain and an ads.txt exists on that subdomain, only advertising systems listed in the subdomain ads.txt are authorized to sell inventory on that subdomain. When the ads.txt on the root domain doesn't declare a subdomain or an ads.txt does not exist on the subdomain, only advertising systems listed in the root domain ads.txt are authorized to sell inventory on that subdomain. 

### 5.6 ADS.TXT CRAWLERS 

A reference implementation of an ads.txt data crawler can be found on github [15]. 
  
Crawlers that may want to crawl publisher content beyond ads.txt and read and display publisher content, advertisements, and connected metadata may do so if not prohibited by the instructions in robots.txt. 
 
Declarations for the specification version number or the last updated date within the ads.txt file specifications are not specified variables. While implementers are welcome to use comments to include these variables, the working group does not want to make them official variables of the specification because there are more reliable methods for crawlers to obtain this information. 
 
Last Updated Date would be used by crawlers to determine how recently the ads.txt file has been updated. We recommend the use of two data points to make this determination.  

1.	Last-Modified response HTTP header 

2.	Checksum of the last known file contents against the new file contents to determine if the file is the same 

Between the two above methods, crawlers should be able to determine whether the file content has changed without requiring publishers to maintain another variable like lastupdateddate. 
 
Specification Version would be used by crawlers to determine which version of the ads.txt specification a publisher is using. Since the creation of ads.txt in 2017, there have been no breaking changes to the specification. The enhancements for each version have been to include new variables such as CONTACT, SUBDOMAIN, INVENTORYPARTNERDOMAIN and now, MANAGERDOMAIN and OWNERDOMAIN. There are no decisions that a crawler would make based on what version of ads.txt a publisher is using. Instead, a crawler should focus on which variables are supported within the file and ensure that they have support for all new variables. 

### 5.7 INVENTORYPARTNERDOMAIN DIRECTIVES 

In many cases, especially in Mobile and CTV video streaming apps (aka OTT apps) it is common to license and curate content from other companies, and to authorize distribution/retransmission of the content to multiple distributor apps. 

These relationships are enumerated via the INVENTORYPARTNERDOMAIN directive.  Please see the “ads.txt for CTV explainer doc” (also available at [https://iabtechlab.com/ads-txt/](https://iabtechlab.com/ads-txt/)) for more details. 

The crawler should fetch entries at one hop from the originating app/ads.txt (any inventorypartnerdomain entries in the partners’ ads.txt files should not be consumed) 

This directive is only applicable if the domain is passed in the bid request using the OpenRTB spec for bid level authorization: 

- *app.inventorypartnerdomain* 

*OR*

- *site.inventorypartnerdomain*
   
### 5.8. OWNERDOMAIN DIRECTIVE 

Many publishers and app developers own and monetize multiple domains (sites) and apps.  To make it clear who owns the domain/app. Example: 

ExamplePublisher.com owns example1.com and example2.com.  

For more detailed implementation information and scenarios, please refer to the implementation guide: [https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf](https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf) 

### 5.9 MANAGERDOMAIN DIRECTIVE 

To help clarify various relationships in the ecosystem, the spec has been updated to allow publishers to specify the business entity that owns a domain/app, and declare managers (e.g., sales houses) if they outsource monetization to another company. 

For more detailed implementation information and scenarios, please refer to the implementation guide: [https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf ](https://iabtechlab.com/wp-content/uploads/2022/04/Ads.txt-1.1-Implementation-Guide.pdf)
 
## 6. SCOPE AND FUTURE DIRECTIONS 

### 6.1 SCOPE 

Scope of this initial version of this standard is to define a mechanism to define authorized sellers for web content from the perspective of the domain owner, for the purpose of addressing some of the fraud scenarios related to counterfeit inventory. 

### 6.2 OPEN ISSUES 

Open issues to be considered for resolution in a future version of the spec should be brought to attention via contacting support@iabtechlab.com. 

### 6.3 FUTURE DIRECTIONS 

Future directions include covering allowed ad formats, syndication, and delegating authority to a third party.  
 	 
 
 
## 7. ACKNOWLEDGEMENTS 
 
The authors would like to thank the original authors of the robots.txt [5][6] file for providing inspiration.  We would also like to thank numerous people within the IAB Tech Lab, TAG and multiple companies for their comments on the early drafts and supporting the initiative. 

## 8. REFERENCES 
  
1.	[https://techcrunch.com/2016/01/06/the-8-2-billion-adtech-fraud-problem-that-everyoneis-ignoring/](https://techcrunch.com/2016/01/06/the-8-2-billion-adtech-fraud-problem-that-everyoneis-ignoring/) 
2.	[http://adage.com/article/digital/ana-report-7-2-billion-lost-ad-fraud-2015/302201/](http://adage.com/article/digital/ana-report-7-2-billion-lost-ad-fraud-2015/302201/) 
3.	[http://boingboing.net/2016/12/21/methbot-a-3m-5mday-video-a.html](http://boingboing.net/2016/12/21/methbot-a-3m-5mday-video-a.html) 
4.	[https://www.emarketer.com/Article/Ad-Industrys-Focus-on-Fraud-HasIntensified/1014430](https://www.emarketer.com/Article/Ad-Industrys-Focus-on-Fraud-HasIntensified/1014430) 
5.	[http://www.robotstxt.org/norobots-rfc.txt](http://www.robotstxt.org/norobots-rfc.txt)
6.	[https://en.wikipedia.org/wiki/Robots_exclusion_standard](https://en.wikipedia.org/wiki/Robots_exclusion_standard) 
7.	[https://www.iab.com/guidelines/real-time-bidding-rtb-project/ ](https://www.iab.com/guidelines/real-time-bidding-rtb-project/)
8.	[https://developers.google.com/ad-exchange/rtb/downloads](https://developers.google.com/ad-exchange/rtb/downloads) 
9.	[https://www.iab.com/guidelines/iab-opendirect-specification/](https://www.iab.com/guidelines/iab-opendirect-specification/) 
10.	[https://tools.ietf.org/html/rfc1123](https://tools.ietf.org/html/rfc1123) 
11.	[https://www.tagtoday.net](https://www.tagtoday.net) 
12.	[https://publicsuffix.org/](https://publicsuffix.org/) 
13.	[https://www.w3schools.com/tags/ref_urlencode.asp](https://www.w3schools.com/tags/ref_urlencode.asp) 
14.	[http://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-25-FINAL.pdf](http://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-25-FINAL.pdf)
15.	[https://github.com/InteractiveAdvertisingBureau/adstxtcrawler](https://github.com/InteractiveAdvertisingBureau/adstxtcrawler)
16.	[https://publicsuffix.org/list/public_suffix_list.dat](https://publicsuffix.org/list/public_suffix_list.dat) 
17.	[ads.txt explainer doc](https://iabtechlab.com/wp-content/uploads/2021/03/ctv-app-ads-explainer-guide.pdf) 
18.	[https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)  
