# Options
  
The `createEncryption ( key , `*`options`*` )` and `createEncryptedForm ( form, key, `*`options`*` )` methods both have a `options` argument, which is a  a JavaScript object with (a selection of) the following fields:
  
* **string `[name = 'adyen-encrypted-data'] `**
  
  The field name of the field that should contain the adyen encrypted data block.

* **string `[fieldNameAttribute = 'data-encrypted-name']`** - *since version: 0_1_10*

  Configure the attribute to identify fields to be encrypted. Useful when you have multiple payment options within the same form, and want to bind each set to it's own CSE handler.
  
* **boolean `[enableValidations = true] `**  
  
  Enable basic field validations. Disable the submit button when the form is not valid 
  
* **boolean `[submitButtonAlwaysEnabled = false]`**

  Force the submit button to be enabled, even when the front-end validation fails.

* **boolean `[disabledValidClass = false]`** - *since version: 0_1_13*
 
  The validation will add a `valid` class for valid fields, next to the `invalid` css class. 
  
  This flag can be used to disable the addition of the `valid` class to the input elements  

* **boolean `[numberIgnoreNonNumeric = true]`**

  When validating the credit card number, ignore non numeric characters like spaces
  
* **function `[onsubmit]`**

  Custom handler to be called on submit of the form.
  
  The callback function will be executed after encryption has taken place, and will receive the original submit event as it's first argument.
  
* **HTMLElement `[cardTypeElement]`**

  Placeholder element to place card type detection results on, when the card type detection addon is enabled.
  
* **string `[cvcIgnoreBins = '']`** - *since version: 0_1_11*
   
  A comma separated string of bins for which the CVC code validation should be ignored.
  
  For example `cvcIgnoreBins = '6703'`) to ignore CVC validation for BCMC.

## Option in createEncryptedForm()
Supported fields: `enabledValidations`, `numberIgnoreNonNumeric`, `cvcIgnoreBins`, `submitButtonsAlwaysEnabled`, `fieldNameAttribute`, `onsubmit`

*Example:*
```Javascript
var cseForm = createEncryptedForm ( form, key , {
    "name" : "my-custom-name",
    "enableValidations" : true,
    "submitButonAlwaysEnabled": false,
    "numberIgnoreNonNumeric" : true,
    "fieldNameAttribute" : "data-encrypted-name",
    "cvcIgnoreBins" = "6703"
} );
```

When the card type detection addon is being enabled, the `cardTypeElement` option is also supported.

## Option in createEncryption()
Currently  `enabledValidations`, `numberIgnoreNonNumeric` and `cvcIgnoreBins` are supported.

```Javascript
var cse = createEncryption ( key , {
    "enableValidations" : true,
    "numberIgnoreNonNumeric" : true,
    "cvcIgnoreBins" = "6703"
} );
```
