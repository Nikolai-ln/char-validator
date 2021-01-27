# char-validator
A char validator for Yii2 that validates string by chosen conditions.
Inspired by nickcv - https://www.yiiframework.com/user/8296 and his extension for Yii 1.1 - https://www.yiiframework.com/extension/alpha!

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://doge.mit-license.org)

## Requirements

* Yii2 >= 2.0
* Composer for installation

#### Installation

```
composer require nikolai/char-validator
```

#### Usage

To use char-validator, install it via Composer, add the new class in the model and then use it in the rules. There are additional parameters that can be used in validation.
An example of using with some parameters, also usage of "extra".

``` php
use nln\chars\CharValidator;
...
public function rules() {
        return [
            [['name'], CharValidator::className(), 'allAccentedLetters' => true, 'allowSpaces'=> true],
            [['differentname'], CharValidator::className(), 'allAccentedLetters' => true, 'allowSpaces'=> true, 'extra' => array('.', '-', '(', ')', '\'')],
        ];
    }
```

* `allowNumbers` is a boolean, and defaults to false. Allow the use of numbers into the string.
* `allowSpaces` is a boolean and defaults to false. the name is pretty self explanatory.
* `minChars` is an integer and defaults to 1.
* `maxChars` is still an integer and defaults to NULL. If you don't want the validated string to have more then x characters use this parameter.
* `accentedLetters` is another boolean. Enables the use of basic accented vowels into the string. See the list below.
* `allAccentedLetters` still a boolean. Enable the use of every accented letter existing in the latin-derived languages. See the list below.
* `extra` this is an array. If you want to allow some other characters (like -) this is the parameter you want to use.
* `message` just like any other validator you can use this to change the error message. You can use {attribute} in this string as a wild card if you want to.
### accentedLetters list
ÀÁÂÃÄĀĂÈÉÊËĚĔĒÌÍÎÏĪĨĬÒÓÔÕÖŌÙÚÛÜŪŬŨàáâãäāăèéêëēěĕ
ìíîïīĩĭòóôõöōŏùúûüūŭũ

### allAccentedLetters list
ÀÁÂÃÄÅĀĄĂÆÇĆČĈĊĎĐÈÉÊËĒĘĚĔĖĜĞĠĢĤĦÌÍÎÏĪĨĬĮİĲĴĶŁĽĹĻ
ĿÑŃŇŅŊÒÓÔÕÖØŌŐŎŒŔŘŖŚŠŞŜȘŤŢŦȚÙÚÛÜŪŮŰŬŨŲŴÝŶŸŹŽŻàá
âãäåāąăæçćčĉċďđèéêëēęěĕėƒĝğġģĥħìíîïīĩĭįıĳĵķĸłľĺ
ļŀñńňņŉŋòóôõöøōőŏœŕřŗśšşŝșťţŧțùúûüūůűŭũųŵýÿŷžżź
ÞþßſÐð

### Disclaimer

Keep in mind that this validation rule is not doing any conversion of the string (no htmlspecialchars, no htmlentities). Be always careful about how to save strings containing accented letters into your database.
