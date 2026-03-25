# Ads.txt Implementation Guidance

## TABLE OF CONTENTS  
 
1. [BACKGROUND](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/Implementation%20Guidance.md#1-background)	
2. [SCOPE](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/Implementation%20Guidance.md#2-scope)
3. [UPDATES TO ADS.TXT & APP-ADS.TXT STANDARD](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/Implementation%20Guidance.md#3-updates-to-adstxt--app-adstxt-standard)	 
4. [EXAMPLE USE CASES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/Implementation%20Guidance.md#4-example-use-cases)	
5. [IMPLEMENTATION GUIDELINES](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/Implementation%20Guidance.md#5-implementation-guidelines)
  
## 1. Background 

Since its introduction in 2017, Authorized Digital Sellers (Ads.txt) has been a successful tool in helping the programmatic ecosystem reduce fraud, specifically misrepresentation (aka “domain spoofing”), and unauthorized sale of ad inventory. With the later creation of sellers.json and the SupplyChain Object, additional disclosure of sellers has furthered transparency throughout the supply chain. At near-full adoption of these specifications, the capability now exists for buyers to use ads.txt, sellers.json, and OpenRTB SupplyChain together to have a more comprehensive view of the supply chain.   

However, with different implementation needs and interpretations of the specifications for publishers, ad supply management companies, and SSPs/ad exchanges, challenges have emerged related to the representation of supply through ads.txt. This proposal is meant to evolve ads.txt to maintain its strength in fraud-reduction, increase transparency in seller relationships via sellers.json, and bridge the specification into the larger suite of supply chain transparency standards.  

Specifically, this update addresses the following challenges and opportunities for improvement: 

- **Representing seller relationships accurately**: Addressing the needs of Supply Path Optimization (SPO) by linking ads.txt/app-ads.txt directly to sellers.json, to ensure that ads.txt files DIRECT/RESELLER values are accurately described. 
- **Introducing the concept of primary or exclusive sellers of inventory**: Buyers have expressed an interest in minimizing the ‘number of hops’ to purchase a piece of inventory. In cases where a publisher outsources the majority of their monetization, the most direct route may be through a reseller. The updates develop a way, through MANAGERDOMAIN, for ad management firms and sale houses to be identified as primary, or exclusive representatives of a publisher’s inventory. 
- **Understanding ownership for domains/apps**: To better connect the sellers.domain listed in sellers.json and the ads.txt file, the updates develop a method to support identifying owned and operated domains and apps back to the entities that own the underlying domain or app. 
 
## 2. Scope 

### In Scope 

**Business relationships**: This solution covers **exclusive or primary monetization partnership** relationships, where a global or regional entity becomes the most direct route to purchase inventory from a site or app. This solution also covers a way to identify **owned** and operated domains and apps back to the entities that own the underlying domain or app. 

**Reducing potential abuse vectors**: These solutions are meant to help more closely tie validation between ads.txt and sellers.json. 

a.	Connecting the seller domain for PUBLISHER entries in sellers.json with the OWNERDOMAIN in ads.txt 

b.	Better representation of exclusive paths to inventory that contain more than one hop in the supply path. 

### Out of Scope 

**Business relationships**: This solution does not cover a way to represent that you are the exclusive monetization partner of a particular ad format type. This was deemed too complex to represent in the ads.txt specification. 
 
## 3. Updates to Ads.txt & App-Ads.txt Standard 

Please see the updates to the ads.txt standard [here ](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md)  
 
The below example use cases seek to help answer, what is the relationship between the “seller” and the underlying domain being sold? 
 
## 4. Example Use Cases 

#### Definitions: 

- **Manager** - ([see definition in spec for official definition](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/main/ads.txt%20v1.1.md)) When the owner of the site does not manage monetization , the external, designated monetization partner is deemed the manager.. These partnerships can be global in scope, can be limited to a particular geography, or for new manager testing purposes, can be limited to a particular subdomain.   
    - *A note on the use of MANAGERDOMAIN vs INVENTORYPARTNERDOMAIN: MANAGERDOMAIN is used to represent a primary or exclusive programmatic seller of a publisher’s inventory and signify when a manager is the most Direct path to a publisher's inventory. Managers are additional participants in the end-to-end transaction between a publisher and a buyer. These relationships are generally governed on a revenue sharing agreement where the manager is paid a percentage of sale of inventory they sell on behalf of the publisher. It is expected that managers are also represented in the schain object of a bid request as the terminal node. In contrast, INVENTORYPARTNERDOMAIN is used to represent a company that owns or has the rights to sell a portion of ads on the underlying app where they are listed. This is expected to be used when the company has an “inventory sharing” agreement in place with the underlying CTV/OTT app. In these transactions it is expected that the inventory partner is the final payee in a transaction and receives all proceeds from the ads sold. Additionally, inventory partner domain is expected to be used primarily for CTV/OTT inventory, where “inventory sharing” is common.* 
- **Proprietary Placement Provider** - Proprietary placements are ad units for which the publisher delegates monetization control to an intermediary. This intermediary might issue bid requests directly to DSPs, or it might issue bid requests via reselling exchanges. 
- **GEO** - Geographical region, in the use cases below GEO is representative of a country. This is to support the MANAGERDOMAIN specification definition that allows for a manager per country declaration. 
 
### CASE A: Publisher inhouse monetization 

**Business scenario**:   The publisher monetizes their inventory internally. They operate the seats on the exchanges: Publisher.com is the business entity that owns site.com 

**Publisher -> Exchange -> DSP** 
 
![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/e8f7de606460c9c32ab3c5442ffa98dc611a6a5e/assets/publisher%3Eexchange%3EDSP.png)  


<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placecment
on site.com sold by exchange.com (sid 1234)

  "site.domain" : 
"site.com" 
"publisher.id"  : "1234" 
"schain" : { 
 	"nodes":  [ 
 	{ 
     	"sid" : "1234",      	"asi" : 
"exchange.com" 
 	} 
] 
} 
```

  </td>
<td>
  
```json
site.com/ads.txt

OWNERDOMAIN = publisher.com

exchange.com, 1234, DIRECT
```
  
</td>
<td>

  ```json
exchange.com/sellers.json 
 
{ 
 	"seller_id" : 
"1234", 
 	"name" : 
"Publisher", 
 	"domain" : 
"publisher.com", 
 	"seller_type" : 
"Publisher" 
}
```

</td>
<td>

  ```json
 IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN + GEO 
THEN seller is manager of publisher.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller of inventory
```

</td>
<td>Seller 1234 is owner of site.com and DIRECT path of inventory</td>
  </tr>
</table>

### CASE B: Publisher managed monetization 

**Business scenario**:  This case represents the publisher monetizing their inventory through an exclusive monetization partner. While the supply path includes multiple hops, it is still the most direct route from a Supply Path Optimization perspective to purchase the inventory. 

**Publisher -> Manager -> Exchange -> DSP**

![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/19b8f21354128ac08ccd85c8ad2e52199d43aef8/assets/publisher%3Emanager%3Eexchange%3EDSP.png)
 
See request/response table on the next page. 
 	 
<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placement on site.com
sold by manager.com (sid 5678) through exchange.com (sid 1235)

"site.domain" : "site.com" "publisher.id" : "1235" "schain" : {
"nodes": [ {
"sid" :
"5678",
"asi" :
"manager.com" },
{
"sid" : "1235",
"asi" : "ecxhange.com"
} ]
}
```

  </td>
<td>
  
```json
site.com/ads.txt

OWNERDOMAIN = publisher.com MANAGERDOMAIN = manager.com

manager.com, 5678, DIRECT exchange.com, 1235, RESELLER
```
  
</td>
<td>

  ```json
manager.com/sellers.json 
 
{ 
 	"seller_id" : 
"5678", 
 	"name" : 
"Publisher", 
 	"domain" : 
"publisher.com", 
 	"seller_type" : 
"Publisher" 
} 
 
 
exchange.com/sellers.jso n 
 
{ 
 	"seller_id" : 
"1235", 
 	"name" : 
"Manager", 
 	"domain" : 
"manager.com", 
 	"seller_type" : 
"Intermediary" 
} 
```

</td>
<td>

  ```json
IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN + 
GEO 
THEN seller is manager of publisher.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller of inventory
```

</td>
<td>Seller 1235 is the monetization Mapager of site.com and is the most DIRECT path to inventory. Seller 5678 is the owner of site.com which has a DIRECT relationship with Manager</td>
  </tr>
</table>


### CASE C: Publisher managed monetization; country specific 

**Business scenario**:  This case represents the publisher monetizing their inventory through an exclusive monetization partner in a specific country. While the supply path includes multiple hops, it is still the most direct route from a Supply Path Optimization perspective to purchase the inventory.  

**Publisher -> Manager + GEO  -> Exchange -> DSP** 
 
![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/4f512ae34235b87ec48e9bcaee4ad1809551820b/assets/publisher%3Emanager%20%2B%20GEO%3Eexchange%3EDSP.png)

See request/response table on the next page. 
 	 
<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placement
on site.com sold by saleshouseDE.com (sid 9876)
through exchange.com (sid 1236) 
 
"site.domain" : 
"site.com" 
"publisher.id"  : 
"1236" 
"schain" : { 
 	"nodes":  [ 
 	{ 
     	"sid" : 
"9876", 
     	"asi" : 
"saleshouseDE.com" 
 	}, 
 	{ 
     	"sid" : 
"1236", 
     	"asi" : 
"ecxhange.com" 
 	} 
] 
}
```

  </td>
<td>
  
```json
site.com/ads.txt 
 
OWNERDOMAIN = 
publisher.com 
MANAGERDOMAIN = saleshouseDE.com, 
DE 
 
 
salehouseDE.com, 9876, DIRECT exchange.com, 1236, 
RESELLER 
```
  
</td>
<td>

  ```json
saleshouseDE.com/sellers.json 
 
{ 
 	"seller_id" : 
"9876", 
 	"name" : 
"Publisher", 
 	"domain" : 
"publisher.com", 
 	"seller_type
" : "Publisher" 
} 
 
 
exchange.com/seller s.json 
 
{ 
 	"seller_id" : 
"1236", 
 	"name" : 
"Salehouse DE", 
 	"domain" : 
"saleshouseDE.com"
, 
 	"seller_type
" : "Intermediary" 
} 
```

</td>
<td>

  ```json
IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN + GEO 
THEN seller is manager of publisher.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller of inventory 	
```

</td>
<td>Seller 1236 is the monetization manager of site.com for DE only and is the most DIRECT path to inventory. Seller 9786 is the owner of site.com which has a DIRECT relationship with Saleshouse DE</td>
  </tr>
</table>

 
### CASE D: Publisher inhouse monetization for proprietary placement type 

**Business scenario**:  The publisher monetizes their inventory internally. They operate the seat with the proprietary placement type directly. Publisher -> Proprietary Placement  ->  DSP 
 
**See request/response table on the next page.**

![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/ac91b381156ac007f74027404b93887e51dbe4c6/assets/publisher%3Eproprietary%20placement%3EDSP.png)
 	 
<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placement on
site.com sold by proprietaryplacement.com (sid 45678) 
 
"site.domain" : 
"site.com" 
"publisher.id"  : 
"45678" 
"schain" : { 
 	"nodes":  [ 
 	{ 
     	"sid" : 
"45678", 
     	"asi" : "proprietaryplacemen t.com" 
 	} 
] 
} 
```

  </td>
<td>
  
```json
site.com/ads.txt 
 
OWNERDOMAIN = 
publisher.com 
MANAGERDOMAIN = manager.com 
 
 
manager.com, 5678, DIRECT 
exchange.com, 1235, RESELLER proprietaryplacement. com, 45678, DIRECT 
```
  
</td>
<td>

  ```json
proprietaryplacement.com/sellers.json 
 
{ 
 	"seller_id" : 
"45678", 
 	"name" : 
"Publisher", 
 	"domain" : 
"publisher.com", 
 	"seller_type
" : "Publisher" 
} 	
```

</td>
<td>

  ```json
IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of site.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of site.com 
 
IF sellers.domain = 
MANAGERDOMAIN + GEO 
THEN seller is manager of site.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller of inventory
```

</td>
<td>Seller 45678 is the owner of site.com and DIRECT path to proprietary placement inventory. </td>
  </tr>
</table>

### CASE E: Resale of publisher inhouse monetization for proprietary placement type 

**Business scenario**:  The publisher monetizes their inventory internally. They operate the seat with the proprietary placement type directly. The proprietary placement vendor then sells the inventory on an exchange. 

**Publisher -> Proprietary Placement  -> Exchange -> DSP** 
 
![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/dac77eccb2e4d21067cd22e4dcef7a226acba5f0/assets/publisher%3Eproprietary%20placement%3Eexchange%3EDSP.png)

See request/response table on the next page. 
 	 
<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placement on site.com sold
by proprietaryplacement.c om (sid 45678) through exchange.com (sid 1238)

"site.domain" : 
"site.com" 
"publisher.id"  : 
"1238" 
"schain" : { 
"nodes":  [ 
{ 
"sid" : "45678", 
"asi" : 
"proprietarypla cement.com" 
}, 
{ 
"sid" : "1238", 
"asi" : 
"exchange.com
" 
} 
] 
} 	
```

  </td>
<td>
  
```json
site.com/ads.txt 
 
OWNERDOMAIN = 
publisher.com 
MANAGERDOMAIN 
= manager.com 
 
 
manager.com, 5678, DIRECT 
exchange.com, 1235, RESELLER 
proprietaryplacement.com, 45678, DIRECT 
exchange.com, 1238, RESELLER 	

```
  
</td>
<td>

  ```json
proprietaryplacement.com/sellers.json 
 
{ 
	 	"seller_id" : 
"45678", 
	 	"name" : 
"Publisher", 
	 	"domain" : 
"publisher.com", 
	 	"seller_type" : 
"Publisher" 
} 
 
exchange.com/sellers.json 
{ 
	 	"seller_id" : "1238", 
	 	"name" : 
"Proprietary Placement", 
	 	"domain" : 
"proprietaryplacem ent.com", 
	 	"seller_type" : 
"Intermediary" 
} 
```

</td>
<td>

  ```json
IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of site.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of site.com 
 
IF sellers.domain = 
MANAGERDOMAIN + GEO 
THEN seller is manager of site.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller 
of inventory 	
```

</td>
<td>Seller 1238 is not the owner or manager of site.com and is a reseller path to underlying inventory. Seller 45678 is the owner of site.com and Proprietary Placement is a DIRECT path to the underlying inventory.</td>
  </tr>
</table>

### CASE F: owned inventory from Media Owner + Monetization Manager that has BOTH owned and resold inventory 

**Business scenario**: The entity selling the inventory is both a media owner and a monetization manager for different pieces of inventory. The below illustrates what would be expected for a piece of inventory that is owned by the entity. 

**Publisher -> Exchange -> DSP** 

![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/08f374a6659e268654b081e4ad0c6857f5d5e1f3/assets/CASE%20F.png)

See request/response table on the next page. 
 	 
<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placement on
site.com sold by exchange.com (sid 1240)

"site.domain" : 
"site.com" 
"publisher.id"  : "1240" 
"schain" : { 
"nodes":  [ 
	 	{ 
     "sid" : 
"1240", 
     "asi" : 
"ecxhange.co m" 
	 	} 
] 
} 	
```

  </td>
<td>
  
```json
site.com/ads.txt 
 
OWNERDOMAIN = xyzmedia.com 
 
exchange.com, 1240, 
DIRECT 	
```
  
</td>
<td>

  ```json
exchange.com/sellers.json 
{ 
"seller_id" 
"1240", 
	 	"name" : 
"XYZ 
Media", 
 	"domain" : "xyzmedia.c om", 
	 	"seller_type
" : "Both" 
} 	
```

</td>
<td>

  ```json
IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of publisher.com 
IF sellers.domain = 
MANAGERDOMAIN + GEO 
THEN seller is manager of publisher.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller of inventory	
```

</td>
<td>Seller 1240 is owner of site.com and DIRECT path to inventory</td>
  </tr>
</table>
 
### CASE G: Resold inventory from Media Owner + Monetization Manager that has BOTH owned and resold inventory 

**Business scenario**: The entity selling the inventory is both a media owner and a monetization manager for different pieces of inventory. The below illustrates what would be expected for a piece of inventory that is being sold by the entity on behalf of another publisher. 

**Publisher -> Manager -> Exchange -> DSP** 

![](https://github.com/InteractiveAdvertisingBureau/ads.txt-app-ads.txt/blob/ccd6f3a9c4262bd6eaeed5d8f7f616e800674483/assets/CASE%20G.png)
 
See request/response table on the next page. 
 	 
<table>
  <tr>
  <td>Bid Request</td><td>Publisher's Authorized Sellers (Ads.txt)</td><td>Sellers.json</td><td>Validation</td><td>Answer</td> 
  </tr>
  <tr>
  <td>
    
  ```json
DSP receives a bid request for a placement on
site.com sold by xyzmedia.com (sid xyz) through 
exchange.com (sid 1240)

"site.domain" : 
"site.com" 
"publisher.id"  : "1240" 
"schain" : { 
"nodes":  [ 
{ 
"sid" : 
"123xyz", 
"asi" : 
"ecxhange.co m" 
}, 
{
"sid" : "1240", 
"asi" : 
"ecxhange.com" 
} 	
]
}
```

  </td>
<td>
  
```json
site.com/ads.txt 
 
OWNERDOMAIN = 
publisher.com 
 
 
xyzmedia.com, 123xyz, DIRECT 
exchange.com, 1240, RESELLER 	
```
  
</td>
<td>

  ```json
xyzmedia.com/sellers.json

{
"seller_id" : "123xyz",
"name" : "Publisher",
"domain" : "publisher.com",
"seller_type" : "Publisher"
}

exchange.com/sellers .json

{
"seller_id" :
"1240",
"name" : "XYZ
Media",
"domain" :
"xyzmedia.com",
"seller_type" :
"Both"
}	
```

</td>
<td>

  ```json
IF sellers.domain = 
OWNERDOMAIN 
THEN seller is owner of publisher.com 
 
IF sellers.domain = 
MANAGERDOMAIN 
THEN seller is manager of publisher.com 
IF sellers.domain = 
MANAGERDOMAIN + GEO 
THEN seller is manager of publisher.com for GEO 
 
IF sellers.domain != 
OWNERDOMAIN or 
MANAGERDOMAIN 
THEN seller is reseller of inventory 	
```

</td>
<td>Seller 1240 is not the owner or manager of site.com and is a RESELLER path to underlying inventory. Seller 123xyz is the owner of site.com and ZYZ Media is a DIRECT path to the underlying inventory. </td>
  </tr>
</table>

## 5. Implementation Guidelines 

### Publisher Guidance 

- It is recommended that you publish OWNERDOMAIN= even if your website domain and owner domain are the same 
    - Specifically for sellers that are both owners and sellers it is highly recommended that they publish OWNERDOMAIN so that buyers can tell the difference between owned inventory and resold inventory. Another recommendation when possible is to separate their selling seats to more clearly represent each type of supply path. 
- It is recommended that you only use MANAGERDOMAIN if a majority of your inventory is managed by a single entity. The exact interpretation of MANAGERDOMAIN is at the discretion of Ads.txt consumers (e.g. validators, measurement and anti-fraud solutions, buying platforms, etc), and may have SPO implications. For example, if the same inventory is available through multiple sellers, and you still use MANAGERDOMAIN, buyers will likely treat the other nonmanager accounts as RESELLER entries. 
- Conflicting MANAGERDOMAIN entries (e.g., multiple MANAGERDOMAIN for the same country) should not be used and will likely be ignored by the consumers of the information. 
- This work is being done in part to help clean up the accuracy of ads.txt files. Please take this opportunity to validate that all DIRECT entries in your file are references to seller accounts that you have direct account control of. 
- All accounts authorized in your ads.txt that are PUBLISHER in the corresponding sellers.json file should also have a sellers.domain in sellers.json that matches the OWNERDOMAIN in your ads.txt. 

### SSP/Exchange Guidance 

- These validations of OWNERDOMAIN and MANAGERDOMAIN require a check against ads.txt AND sellers.json.
- Ensure that the sellers.domain in sellers.json matches the OWNERDOMAIN and MANAGERDOMAIN for selling accounts respectively. 
- Consider more strictly validating ads.txt entries to ensure that they contain the correct field 3 value. SSPs/exchanges know what relationship they have with their publishers, and therefore can easily check if their publishers are correctly declaring field 3 in their ads.txt files. 
 
### DSP Guidance 

- These validations of OWNERDOMAIN and MANAGERDOMAIN require a check against ads.txt AND sellers.json. It is recommended that DSPs consume and action against this data for risk mitigation benefits and SPO. 
- The exact interpretation of MANAGERDOMAIN is at the discretion of each DSP, and may have significant SPO implications. It is recommended that if the DSP differs from the below guidelines, publish clear guidelines to publishers, SSPs, and partners before enforcement of any policies regarding MANAGERDOMAIN. 
- The recommendations for DSPS are: 
    - If you see a MANAGERDOMAIN declared, but still see significant inventory available through other sources, indicating that the MANAGERDOMAIN is not exclusive, you may treat the other traffic sources as RESELLERs of inventory, but be aware that there are non-abusive use cases that are not exclusive. Additional verification is recommended.
    - If the same inventory is available both from OWNERDOMAIN sellers and MANAGERDOMAIN sellers, the MANAGERDOMAIN entry is likely mis-marked (since selling inventory directly and via a manager implies the publisher is not outsourcing their yield management to an external entity like a sales house).  
    - It is recommended that if there is more than one MANAGERDOMAIN for the same country that consumers treat it as if there is no MANAGERDOMAIN declared for that country (ie, that declaration is invalid). 
    - It is expected that ad opportunities monetized by the manager, the domain listed in MANAGERDOMAIN is also that of the node representing the originating publisher in a complete supply chain object. 
  
