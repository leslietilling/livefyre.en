---
description: Sets SSL for API calls to be on or off.
seo-description: Sets SSL for API calls to be on or off.
seo-title: setSSL Network Method
solution: Experience Manager
title: setSSL Network Method
uuid: 1ceb05b5-3501-4fa5-ab7d-469c2ff84759
index: y
internal: n
snippet: y
translate: y
---

# setSSL Network Method


<table id="properties_gq4_jyf_5y" class="simpletable properties" cellpadding="4" cellspacing="0"> 
 <thead class="prophead sthead"> 
  <th class="proptypehd"> Variable </th> 
  <th class="propvaluehd"> Type </th> 
  <th class="propdeschd"> Description </th> 
 </thead> 
 <tr class="property strow"> 
  <td class="proptype stentry"> <span class="varname"> ssl </span> </td> 
  <td class="propvalue stentry"> Boolean </td> 
  <td class="propdesc stentry"> <p>Default is true. if you want SSL on, false otherwise. 
    <ul id="ul_gdz_5cs_rz"> 
     <li>True - SSL on</li> 
     <li>False - SSL off</li> 
    </ul></p> </td> 
 </tr> 
</table>


## Java Example {#section_nyl_ycs_rz}


```
network.setSsl(ssl); 

```

## NodeJS Example {#section_xkd_gds_rz}


```
network.ssl = false; 

```

## PHP Example {#section_ghf_gds_rz}


```
$network->setSsl(false); 

```

## Python Example {#section_dwg_gds_rz}


```
network.ssl = False 

```

## Ruby Example {#section_enh_gds_rz}


```
network.ssl = false 

```