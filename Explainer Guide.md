# ads.txt & app-ads.txt: Guidance for Inventory Sharing

## TABLE OF CONTENTS 
 
- BACKGROUND	
    - SCOPE	
        - IN SCOPE	
        - OUT OF SCOPE	
- UPDATES TO ADS.TXT & APP-ADS.TXT STANDARD	
- EXAMPLE USE CASES	
    - CASE A: PROGRAMMER OWNED APP	
    - CASE B: CONTENT CHANNEL ON VMVPD APP	
        - BUSINESS SCENARIO B.1	
        - BUSINESS SCENARIO B.2	
    - CASE C: PROGRAMMER OWNED APP USING MVPD SIGN-IN (TV EVERYWHERE)	
- USE CASE IMPLEMENTATION LOGIC	
- IMPLEMENTATION GUIDELINES FOR CTV/OTT	
    - CTV APP STORE GUIDANCE	
    - PUBLISHER GUIDANCE	
    - SSP/EXCHANGE GUIDANCE	
    - DSP GUIDANCE	
 	 
## Background 

The Connected TV market introduces a much higher occurrence of complex monetization relationships that make ads.txt & app-ads.txt, as currently designed, insufficient for broader adoption.  (*It is important to note that these relationships are not unique to the CTV environment or OTT content delivery, however, the much higher occurrence of these relationships in CTV/OTT contexts rendered this problem in particular need of resolution.*)  These guidelines & spec enhancements are intended to more seamlessly support site & apps in which multiple entities may have ownership rights over the ad space, commonly referred to as “**inventory sharing**”.  In OTT, these situations often arise from relationships such as content distribution (MVPDs or vMVPDs) or as a result of various carriage agreements (TV Everywhere).  Ultimately, nearly all relationships can be simplified into the case where “some business entity, other than the app/site owner, has ownership over some ad space within the app/site and the right to sell that inventory.” 
 
A simple example of one such situation is a content distributor such as a vMVPD app.  In these content distribution agreements, one entity, a content producer/programmer A, gives rights to a content distributor B, to rebroadcast their content.  As part of the agreement, both A & B have ownership of some portion of ad inventory delivered into the streamed content (the inventory is “shared”).  By using the word “ownership”, we imply that both A & B may legitimately originate an ad request inside an app that will be propagated into the programmatic ecosystem. 
 
In the current ads.txt & app-ads.txt standard, declaring this relationship would require the vMVPD app to authorize Programmer A in their app-ads.txt file, along with the programmers’ authorized seller and reseller information. This increases the cost of generating and maintaining an app-ads.txt file, and incrementally decreases the security benefit of the standard as the number of authorized sellers grows. 
  
It is these scenarios that we intend to define and validate via the Ads.txt & App-ads.txt for Inventory Sharing guidelines for CTV/OTT. 

## Scope

### In Scope  

**Business relationships**: This solution covers **inventory sharing** relationships, where different entities (app/site owner, content owner) may have the right to sell ad space within a piece of content on a given app/site. 
 
**Potential abuse vectors**: This solution is intended to address basic misrepresentations of publishers’ ownership of (and rights to sell) inventory on an app/site; answering the question: 

*“Does publisher A have ownership of (and rights to sell) some inventory on app/site B?”*

### Out of Scope  

**Business relationships**: This solution does not cover **revenue sharing** scenarios, where one entity owns & sells the ad inventory associated with content provided by a content owner (e.g., YouTube, DailyMotion).  The owning entity may share revenue generated from ad sales back with the content owners, but ultimately there is only one entity owning/selling the ad inventory. 
 
**Potential abuse vectors**: This solution does not address additional aspects of content rights ownership or media rights management such as exclusivity or inventory ownership within specific content/shows.  We are not attempting to answer questions: 

*“Does publisher A have rights to sell inventory within this specific TV show or programming?”*

**OR**

*“Does app/site C have the exclusive rights to deliver/stream a specific TV show or programming?”*

While these concepts are increasingly important, especially in the space of Connected TV and OTT streaming, they will require new solutions being developed. 

## Updates to Ads.txt & App-Ads.txt Standard 

In the previous version of ads.txt & app-ads.txt, supporting these scenarios would have required the app/site owner/developer to maintain their ads.txt/app-ads.txt file with the publisher IDs of all the partners (and their resellers) with whom they have negotiated some share of inventory ownership rights - making many ads.txt/app-ads.txt files prohibitively difficult to maintain. Note that moving to this method means that the publisher accepts all entries in the partner’s ads.txt/app-ads.txt file as authorized to sell their inventory and assumes the risk of any changes to that file with or without their knowledge. 
 
Instead, the ads.txt & app-ads.txt specs have been updated to include the ability to designate another domain (aside from the app/site developer’s) that is able to validate the publisher ID of the bid request.  These domains are to be passed through site and app objects in the OpenRTB spec: 

- *app.inventorypartnerdomain*

  OR 

- *site.inventorypartnerdomain* 
 
To validate these domains, the [(app)ads.txt spec](https://iabtechlab.com/ads-txt/) also includes the following additional declaration in ads.txt & app-ads.txt files (defined in ads.txt), intended to be entered by the owner of the app/site:  
 
|VARIABLE |	VALUE |	DESCRIPTION |
|---|---|---|
|inventorypartnerdomain |	Pointer to the domain of the partner (of the site/app owner) with ownership of some portion of ad inventory on the site/app.  The partner’s ads.txt or appads.txt file will be hosted here. |	When a site or an app contains ad inventory that is owned by another partner - the app or site should list all domains for those partners via this directive. |
 
Please see the example use cases later in this document for how these values work together to validate inventory in the new version of app-ads.txt. 

## Example Use Cases 

**Definitions:**

- **Programmer A**: Content owner or content developer - ex: ESPN, CBS, NBC, Crackle, Tastemade, Sky (UK), TF1 (FR), RTL (DE and NL), SBS (AU), Channel 9 (AU), Nippon TV (JP), etc. 
- **(v)MVPD**: (virtual) Multichannel Video Programming Distributor / Content distributor (monetizing partner, doesn’t always have ownership over user-facing content) - Sling TV, Pluto TV, YouTube TV, The Roku Channel, Fubo, Comcast, Sky (UK), Virgin Media (UK), Orange Télécom (FR) and Bouygues Télécom (FR), Foxtel (AU) 

### CASE A: Programmer Owned App 

**Business scenario**:  All of the inventory is being produced and sold by programmer A, in their owned app, via their chosen SSPs.  This is the most straightforward example of OTT inventory and does not differ from the current app-ads.txt authorization model. 
 
**App**: Programmer A App (app bundle ID: 12345) 

**Developer URL domain for the app**: devsite.programmerA.com 

**Seller/Publisher**: Programmer A (publisher ID: abcde) 

**Content Producer**: Programmer A 
  
**OpenRTB Declaration:** 

```json
{ 
  "app": { 
    "bundle": "12345", 
    "storeurl": "https://ctvappstore.com/details/12345/programmerA", 
    "publisher": { 
      "id": "abcde" 
    }, 
  } } 
 ```

**Programmer A app-ads.txt file** (devsite.programmerA.com/app-ads.txt): 

`ssp.com, abcde, DIRECT, *` 
 
**Note: The “Certification Authority ID” field may also be included in ads.txt & app-ads.txt files, but is omitted from these examples as it is optional.*

### CASE B: Content Channel on vMVPD app 

In this case, we will present two different ways that authorization for ads running against licensed content appearing inside a vMVPD app may appear in bid requests and app-ads.txt & ads.txt files.   These are presented as Business Scenarios B.1 and B.2. 

#### Business Scenario B.1 

vMVPD B has rights to sell the ad slot, the ad is served into Programmer A’s content within the vMVPD B app.  Information about the content ownership (i.e., the content is owned by Programmer A) is “blinded” - not declared in the bid request.  This is similar to Case A (app owner selling inventory on their app w/o specific content declaration) and does not differ from the current app-ads.txt authorization model. 
 
**App**: vMVPD B App (app bundle ID: 67890) 

**Developer URL domain for the app**: devsite.vMVPDB.com 

**Seller/Publisher**: vMVPD B (publisher ID: vwxyz) 

**Content Producer**: Programmer A 
  
**OpenRTB Declaration: (by vMVPD B)**

```json
{ 
  "app": { 
    "bundle": "67890", 
    "storeurl": "https://ctvappstore.com/details/67890/vmvpdB", 
    "publisher": { 
      "id": "vwxyz" 
    }, 
  }
} 
```

**vMVPD B app-ads.txt file** (devsite.vMVPDB.com/app-ads.txt): 
`ssp.com, vwxyz, DIRECT`

#### Business Scenario B.2  

Programmer A has rights to sell the ad slot, the ad served into Programmer A content within the vMVPD B app.  
 
**App**: vMVPD B App (app bundle ID: 67890) 

**Developer URL domain for the app**: devsite.vMVPDB.com 

**Seller/Publisher**: Programmer A (publisher ID: abcde) 

**Content Producer**: Programmer A 

 **OpenRTB Declaration: (by Programmer A)**

```json
{ 
  "app": { 
    "bundle": "67890", 
    "storeurl": "https://ctvappstore.com/details/67890/vmvpdB", 
    "inventorypartnerdomain": "programmerA.com”, 
    "publisher": { 
      "id": "abcde" 
    } 
    }
} 
  ```

**vMVPD B app-ads.txt file** (devsite.vMVPDB.com/app-ads.txt): 

```json
ssp.com, vwxyz, DIRECT
inventorypartnerdomain=programmerA.com 
```

*Programmer A ads.txt file* (programmerA.com/ads.txt): 

`ssp.com, abcde, DIRECT`

### CASE C: Programmer Owned App using MVPD sign-in (TV Everywhere) 

**App**: Programmer A App (app bundle ID: 12345) 

**Developer URL domain for the app**: devsite.programmerA.com 

**Seller/Publisher**: vMVPD B (publisher ID: vwxyz) 

**Content Producer**: Programmer A 
 
**Business scenario**: Due to the user login to programmer A’s app with the vMVPD B’s login credentials, vMVPD B has rights to sell the ad slot within programmer A’s app.  Note this is the reverse of Case B: Business scenario 2. 

```json
{ 
  "app": { 
    "bundle": "12345", 
    "storeurl": "https://ctvappstore.com/details/12345/programmerA", 
      "inventorypartnerdomain": "vmvpdB.com”, 
    "publisher": { 
      "id": "vwxyz" 
    } 
  }
} 
```

*Programmer A app-ads.txt file* (devsite.programmerA.com/app-ads.txt): 
```json
ssp.com, abcde, DIRECT
inventorypartnerdomain=vmvpdB.com 
```

**vMVPD B ads.txt file** (vMVPDB.com/ads.txt): 

`ssp.com, vwxyz, DIRECT` 

## Use Case Implementation Logic 

|Scenario |	Do this.. |	Possible outcomes|
|---|---|---|
|Bid request is app*, and does not have $.app.inventorypartnerdomain (Corresponds to business use case A, B.1) |	Attempt lookup of **app-ads.txt** @ developer domain retrieved from app store record for $.app.bundle |	No valid app-ads.txt records found because store record cannot be found, there is no domain available in store record, the domain does not have an app-ads.txt file, the web server returns an error, etc. -> **Nonparticipating inventory**, Valid app-ads.txt file is found & bid request publisher ID + advertising system is not found in file -> **Unauthorized inventory**, Valid app-ads.txt file is found & bid request publisher ID + advertising system is found in file -> **Authorized inventory**  
|Bid request is app*, and has $.app.inventorypartnerdomain (Corresponds to business use cases B.2, C) |	Attempt lookup of **app-ads.txt** @ developer domain retrieved from app store record for $.app.bundle Attempt lookup of **ads.txt** @ domain from $.app.inventorypartnerdomain field from **bid request** |	No valid app-ads.txt records found because store record cannot be found, there is no domain available in store record, the domain does not have an app-ads.txt file, the web server returns an error, etc. -> **Inconclusive: authorization cannot be determined**,	**IF**: Valid app-ads.txt file is found & bid request publisher ID + advertising system is found in app-ads.txt file -> **Authorized inventory**, **ELSE**: Valid app-ads.txt file is found & **app-ads.txt file** does not contain an inventorypartnerdomain directive matching the domain from $.app.inventorypartnerdomain from the **bid request -> Unauthorized inventory**, **App-ads.txt file** contains inventorypartnerdomain directive matching the domain from $.app.inventorypartnerdomain from the **bid request**, but no valid ads.txt records found in the ads.txt file at inventorypartnerdomain because domain does not have an ads.txt file, web server returns an error, etc. -> **Inconclusive: authorization cannot be determined**, **App-ads.txt file** contains inventorypartnerdomain directive matching the domain from $.app.inventorypartnerdomain from the **bid request**, bid request publisher ID + advertising system is not found in inventorypartnerdomain’s ads.txt file -> **Unauthorized inventory**,  **App-ads.txt file** contains inventorypartnerdomain directive matching the domain from $.app.inventorypartnerdomain from the **bid request**, bid request publisher ID + advertising system is found in inventorypartnerdomain’s ads.txt file -> **Authorized inventory**| 
 
*Note: If bid request is site, instead of app, same logic applies but look for $.site.inventorypartnerdomain*

## Implementation Guidelines for CTV/OTT 

### CTV App Store Guidance 

**Required:**

1.	To ensure the app-ads.txt information is verifiable across ad tech platforms, it is important to make the app store website publicly available on the web. 
 
2.	CTV app stores are required to support the [OTT/CTV Store Assigned App Identification Guidelines](https://iabtechlab.com/wp-content/uploads/2020/08/IAB-Tech-Lab-OTT-store-assigned-App-Identification-Guidelines-2020.pdf) by ensuring their store assigned IDs are publicly accessible from their store.  

3.	CTV app stores are required to follow the [app-ads.txt standard](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/app-ads.txt.md) to add meta tags into the HTML page to publish the developer website URL, bundle id, and store id. The IAB Tech Lab’s [demystifying app-ads.txt](https://iabtechlab.com/blog/demystifying-app-ads-txt/) guidance also defines other methods to publish a publisher’s website URL, bundle id, and store id.   

### Publisher Guidance 

**Required:**

1.	Before publishers can adopt app-ads.txt for CTV inventory, they need to adopt the [OTT/CTV Store Assigned App Identification Guidelines](https://iabtechlab.com/wp-content/uploads/2020/08/IAB-Tech-Lab-OTT-store-assigned-App-Identification-Guidelines-2020.pdf).  Per these guidelines, publishers are required to: 

  	a.	Pass CTV app store assigned IDs in the app.bundle field of OpenRTB 2.5 or the app.storeid field of OpenRTB 3.0/AdCOM 1.0. 

    b.	Pass the store URL of the originating app in app.storeurl field of OpenRTB 2.5 and OpenRTB 3.0/AdCOM 1.0. 

2.	**App owners** should publish their app-ads.txt file on their developer web site, following the [app-ads.txt standard](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/app-ads.txt.md).  If publishers have already published the app-ads.txt for mobile app inventory, and there are different authorized seller IDs for their CTV app, they should publish a CTV specific app-ads.txt file at a new domain specific for CTV app inventory. 

3.	In addition, **App Owners** should declare within their app-ads.txt file the domain of **Inventory Partners** who own inventory within the **App Owner’s** app using the *inventorypartnerdomain* directive. This should be the domain where the **Inventory Partner** hosts their ads.txt or appads.txt file. 

**Note: If an app owner would prefer to list inventory partners seller & reseller IDs directly within the app-ads.txt file, rather than leveraging the inventorypartnerdomain directive, this is also supported.* 
 
**Guidance for app publishers passing additional information in bundle fields**

It has been observed that many CTV app publishers are passing additional information in the bundle ID that may be “lost” as part of this transition. Below is guidance on where this information is more appropriately passed: 

a.	**Channel or Network within an app**: content.producer.name  

b.	**VOD vs. Livestream**: pass in content.livestream 

c.	**Device make/model**: pass in device.make & device.model 

d.	**App store**: pass in app.storeurl - (*Note: this is already required per the app-ads.txt standard*) 
 
Also see: [OTT/CTV User Agent Guidelines](https://iabtechlab.com/wp-content/uploads/2019/12/OTT_CTV_User_Agent_Preliminary_Guidelines_IABTechLab_2019-12.pdf) 
 
### SSP/Exchange Guidance 

**Required:**

1.	SSPs/Exchanges are required to implement the *app.inventorypartnerdomain* & *site.inventorypartnerdomain* fields from the site and app objects to support the passing of inventory partner domains for pointers to partner ads.txt files, where an inventory partner exists. 

2.	SSPs/Exchanges should support publishers in providing CTV App IDs according to the [OTT/CTV Store Assigned App Identification Guidelines](https://iabtechlab.com/wp-content/uploads/2019/12/OTT_Store_Assigned_App_Identification_Guidelines_IABTechLab_2019-12.pdf)* as well as assist them in passing additional contextual & environment signals (as noted in Publisher Guidance section) via the appropriate existing or extension OpenRTB fields. 

**Failure to comply with the guidelines will prevent the DSP from verifying the app-ads.txt information.*

### DSP Guidance 

**Required:**

1. DSPs should implement their app-ads.txt crawler according to standardized guidance from CTV app stores (or use a service that adheres to those guidelines). 
 
