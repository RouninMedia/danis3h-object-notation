# danis3h Object Notation
**danis³h Object Notation** (or **dON**) is an alternative to **JSON**, optimised for use in HTML attribute values.

The only difference is that instead of using double quotes(`""`), **dON** uses the double angle quotes (or _guillemets_) which are common in written French.

This straightforwardly enables **dON** to be used to represent values in HTML attributes.

________

### Example of JSON

```json
[{"This": "is"}, "an", {"example": ["of", "JSON"]}]
```

### The same example in dON
```
[{«This»: «is»}, «an», {«example»: [«of», «dON»]}]
```
________

There are two functions to handle the bi-directional conversion of **JSON** to **dON** and from **dON** back to **JSON** again:

## Converting from JSON to dON

```js
const convertJSONtoDON = (JSON) => {
  
  let don = JSON;
  
  don = don.replaceAll('{"', '{«');
  don = don.replaceAll('["', '[«');
  don = don.replaceAll(':"', ': «');
  don = don.replaceAll(':{', ': {');
  don = don.replaceAll(':[', ': [');
  don = don.replaceAll(',"', ', «');
  don = don.replaceAll(',{', ', {');
  don = don.replaceAll(',[', ', [');
  don = don.replaceAll('":', '»:');
  don = don.replaceAll('",', '»,');
  don = don.replaceAll('"]', '»]');
  don = don.replaceAll('"}', '»}');

  return don;
};
```

## Converting from dON back to JSON

```js
const convertDONtoJSON = (don) => {
  
  let JSON = don.replace(/«|»/g, '"');

  return JSON;
};
```
