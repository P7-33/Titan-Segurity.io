---
title: 'ATTACKdatamap'
date: 2019-10-28T13:53:00+01:00
draft: false
---

**Kang Asu**

![](https://1.bp.blogspot.com/-_eZl42q-80c/XbA_43IJjyI/AAAAAAAAQpo/ul7KWgttiCo6pWDV0yG8cmN9Iz6rkp4XgCNcBGAsYHQ/s640/ATTACKdatamap.png)

**ATTACKdatamap - A Datasource Assessment On An Event Level To Show Potential Coverage Or The MITRE ATT&CK Framework**

A datasource assessment on an event level to show potential coverage of the "MITRE ATT&CK" framework.  
This tool is developed by me and has no affiliation with "MITRE" nor with its great "ATT&CK" team, it is developed with the intention to ease the mapping of data sources to assess one's potential coverate.  
More details in a blogpost [here](https://medium.com/@olafhartong/assess-your-data-potential-with-att-ck-datamap-f44884cfed11 "here")

[](https://www.blogger.com/u/1/null)  
**Start**  
This tool requires module ImportExcel, Install it like this `PS C:\> Install-Module ImportExcel`  
Import the module with `Import-Module .\ATTACKdatamap.psd1`  
  
**Request-ATTACKjson**  
Generates a [JSON](https://www.kitploit.com/search/label/JSON "JSON") file to be imported into the ATT&CK Navigator. The mitre\_data\_assessment.xlsx file contains all Techniques, which can be updated via Invoke-ATTACK-UpdateExcel.  
Each technique contains DataSources, which are individually scored by me with a weight. The DataSourceEventTypes need to be scored per environment.  
This script multiplies the respective DataSource scores and adds them to a total technique score. The generation date is added to the description.  
EXAMPLE  
`PS C:\> Request-ATTACKjson -Excelfile .\mitre_data_assessment.xlsx -Template .\template.json -Output 2019-03-23-ATTACKcoverage.json`  
This is all gathered into a JSON file which can be opened here; [MITRE ATT&CK Navigator/enterprise/](https://mitre-attack.github.io/attack-navigator/enterprise/ "MITRE ATT&CK Navigator/enterprise/")  
  
**Invoke-ATTACK-UpdateExcel**  
This generates all MITRE ATT&CK relevant fields into a table and creates or updates the REF-DataSources worksheet in an Excel sheet  
EXAMPLE  
`PS C:\> Invoke-ATTACK-UpdateExcel -AttackPath .\enterprise-attack.json -Excelfile .\mitre_data_assessment.xlsx`  
The -AttackPath and -Excelfile parameters are optional  
  
**Get-ATTACKdata**  
This downloads the MITRE ATT&CK Enterprise JSON file  
EXAMPLE  
`PS C:\> Get-ATTACKdata -AttackPath ./enterprise-attack.json`  
The -AttackPath parameter is optional  
  

**[Download ATTACKdatamap](http://eunsetee.com/eJN6 "Download ATTACKdatamap")**

**Regards**

**Kang Asu**