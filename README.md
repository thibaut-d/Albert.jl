# Albert.jl
Some ideas for a rich knowledge graph to extract structured information from scientific literature with NLP

## Example of information to structure

```
<Names>:
  [AFNOR]: "Z40C13"
  [EU]: "X46Cr13"
  [EU num]: "1.4034"
  [AISI]: "420C"

<Similar to>:
  [420HC]

<Description>: "stainless steel widely used in cuttellery"

<Subclass of>: [stainless steel]

<used by>
  [Cutellery]
  [Bearing]

<is>
    [Food contact compatible]
  
<Contains>:
  [Carbon]:	0.46 %
  [Chromium]:	14 %
  [Manganese]:	0.35 %
  [Silicium]:	0.3 %
  > Reference: [EN10088]

<States>:
  >>> Vaccum Quenched X46Cr13 with cryogenics:
    <Process>:
      [Heat]: 1050 °C
      [Vaccum quenching]
      [Cryogenics]: 2 H
    [Hardness]: 57 HRC > Reference: http://datasheetURL
    > Reference: [EN10088]
      
<Produced by>:
  
  
<Distributed by>:
  [Eurotechni] <where> [Thiers]
  ...
  
<described in> [Datasheet]:
  http://datasheetURL
  http://datasheetURL
    
<described in> [Wikipedia page]: 
    <language> [French]: https://fr.wikipedia.org/wiki/X46Cr13
```
      
## Structuration

### Possible
      
```     
_propertyID_ _parent_propertyID_ Object <property> [PropertyQualifierObject] [ObjectAsValue] fixed_value [unit]
      
> SubProperties:
  _sub_propertyID_

> References:
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
