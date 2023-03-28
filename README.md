# GreenLight_Extensions
Extensions for
# GreenLight_Extensions Repository
This repository contains extensions for the  [GreenLight - A model for greenhouses with supplemental lighting](#https://github.com/davkat1/GreenLight) , including `setXParam` and `glObjToJson`.

## Table of Contents 
- [Installation](#installation) 
- [Usage](#usage) 
- [Functions](#functions) 
- [License](#license)

## Installation
Download the repository to your local machine.
```bash
git clone https://github.com/greenpeer/GreenLight_Extensions.git
```

## Usage

`gl` is an instance of the GreenLight model, To generate a `gl` instance using `GreenLight`, you can run the `runGreenLight.m` file located in the `runScenarios` folder of the [`GreenLight`](https://github.com/davkat1/GreenLight/blob/master/Code/runScenarios/runGreenLight.m)repository.
```MATLAB
json_str = glObjToJson(gl)
```

The setXParam function changes the value of a parameter in a DynamicModel object. `cFruit` is a parameter name used in gl objects. It is located under the gl object.x namespace.
```MATLAB
setXParam(gl, "cFruit", 2.8e5)
```


## Functions

1. [`encodeNestedObj(obj)`](#encodenestedobj): Encodes a nested MATLAB object into a new object, coverts its function handles to string. 
2. [`encodeFieldValue(fieldName, fieldValue)`](#encodefieldvalue): Encodes a field value based on its name and type. It handles various data types such as function handles, empty values, structures, and instances of the `DynamicElement` class. 
3. [`glObjToJson(gl)`](#globjtojson): The main function that converts a custom MATLAB object `gl` to a JSON string.
4. The [`setXParam`](#setxparam) function changes the value of a parameter in a `DynamicModel` object. It throws an error if the `DynamicElement` of `dm.x.<name>` doesn't exist.

___
### glObjToJson

```matlab
json_str = glObjToJson(gl);
```
Convert a custom MATLAB object "gl" to a JSON string.
#### Inputs: 
- `gl`: A MATLAB GreenLight model object that may have nested structures, instances of the DynamicModel or DynamicElement class, function handles, or other field types.
#### Outputs: 
- `json_str`: A JSON string representation of the input object `gl`, with all function handles in `gl` converted to strings.
___
### encodeNestedObj

```matlab
encodedObj = encodeNestedObj(obj);
```

Encode a nested MATLAB object into a new object.
#### Inputs: 
- `obj`: A MATLAB object that may have nested structures, instances of the DynamicModel or DynamicElement class, function handles, or other field types.
#### Outputs: 
- `encodedObj`: An encoded representation of the input object "obj".
___
### encodeFieldValue

```matlab
encodedValue = encodeFieldValue(fieldName, fieldValue);
```
Encode a field value based on its name and type.
#### Inputs: 
- `fieldName`: The name of the field to be encoded. 
- `fieldValue`: The value of the field to be encoded.
#### Outputs: 
- `encodedValue`: The encoded value of the input field value.
___
### setXParam
```matlab
setXParam(dm, name, val)
```

#### Inputs: 
- `dm`: A DynamicModel object. 
- `name`: A string specifying the name of the parameter to be changed. 
- `val`: A numeric value that will replace the current value of the specified parameter.
#### Outputs: 
- None
___

## Limitations 
- The `glObjToJson` function is designed to work with GreenLight model MATLAB objects that have nested structures, instances of the `DynamicModel` or `DynamicElement` class, function handles, and other field types. However, it may not handle other possible MATLAB data types or custom classes. 
- The function currently assumes that function handles are only present in fields named 'def'. If you have function handles with different field names, you may need to modify the `encodeFieldValue` function accordingly.
- The function may not handle very large or complex objects efficiently.


## License

This project is licensed under the [MIT License](https://choosealicense.com/licenses/mit/) .



