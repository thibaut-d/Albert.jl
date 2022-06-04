# Albert.jl
Some ideas for a rich knowledge graph to extract structured information from scientific literature with NLP

## Example of information to structure

```
[X46Cr13 stainless steel]

<has> [name]:
  [AFNOR]: "Z40C13"
  [EU]: "X46Cr13"
  [EU num]: "1.4034"
  [AISI]: "420C"

<similar to>:
  [420HC]

<described by>: "stainless steel widely used in cuttellery"

<subclass of>: [stainless steel]

<used by>
  [Cutellery]
  [Bearing]

<is>
    [Food contact compatible]
  
<contains> [chemical element]:
  [Carbon]:	0.46 %
  [Chromium]:	14 %
  [Manganese]:	0.35 %
  [Silicium]:	0.3 %
  > Reference: [EN10088]

<has subclass>:
  >>> [Vaccum Quenched X46Cr13 with cryogenic]:
    <Process>:
      [Heat]: 1050 °C
      [Vaccum quenching]
      [Cryogenics]: 2 H
    [Hardness]: 57 HRC > Reference: http://datasheetURL
    > Reference: [EN10088]
      
<made by> [manufacturer]:
  ... 
  
<can be found at> [distributor]:
  [Eurotechni]
    <where> [Thiers]
  ...
  
<described by> [datasheet]:
  http://datasheetURL
  http://datasheetURL
    
<described by> [Wikipedia]:
  https://fr.wikipedia.org/wiki/X46Cr13  
    <language> [French]
```
      
## Structuration

### Possible
      
```     
_propertyID_ _parent_propertyID_ [Subject] <property> [PropertyQualifierObject] [Object] string bool int float [unit]
      
Joint to > SubProperties:
  _sub_propertyID_

Joint to or list > References:
  _referenceID_
```
      
### Ex:

```
_1234_ _NULL_ [X46Cr13] <contains> [Chromium] 13 [percentage]
> References:
      _4567_ (>>> [EN10088])
 
 _112213_ _NULL_ [Vaccum Quenched X46Cr13 with cryogenics] <has physical property> [Hardness] 47 [HRC]
> References:
      _4567_ (>>> [EN10088])

_1369_ _NULL_ X46Cr13: <described in> [Wikipedia] https://fr.wikipedia.org/wiki/X46Cr13 URL
> SubProperties:
      _9911_ (>>> _9911_ _1369_ <use> [French])
```  

### compatibility with semantic web RDF

- property ID is the ID of the triple
- parent property ID can be a sub graph id
- The subject is the RDF subject 
- Together the property name and the property qualifier object from the RDF predicate. This permits to keep a limited amount of properties with a wide vocabulary, what is often an issue in ontologies.
- The object/numerical/etc. value with unit is the RDF object 
