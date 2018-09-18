Localisation Library for Countries, Languages and Currencies
============================================================

This library contains packaged publicly available data taken from an older version of [Umpirsky's Country
List](https://github.com/umpirsky/country-list) before it specialised just in country localisations.


Prerequisites
-------------

- A working PW3.0.98+ installation.



Installation
------------

### Via Modules Page In Admin

- Install using module class name of "LibLocalisation"



Usage Examples
--------------

To create a localisation for a particular locale, first create a new instance and define the locale...

    $de_DE = wire('modules')->get('LibLocalisation')->setLocale('de_DE');

You can now use your locale to get information about countries, currencies and languages as they are used in that
locale. For example, to ouptut the names of various countries you use the _country()_ method, passing in an ISO3166
country code...

    echo $de_DE->country('CH'); // Outputs "Schweiz" - the German for Switzerland.
    echo $de_DE->country('AU'); // Outputs "Australien" - the German for Australia.
    echo $de_DE->country('US'); // Outputs "Vereinigte Staaten" - ditto for the United States of America.

You can create as many instances of the module as you need and set them all up for the same, or different, locales.

To access currency data, you call the _currency()_ method, passing in the currency code you are interested in.

    echo $de_DE->currency('GBP');

This returns an array of data about GBP - localised in German...

   [ digits => 2,
     number => "826",
     symbol => "£",
     name => "Britisches Pfund Sterling" ]

Finally, you can output localised language names by calling the _language()_ method and giving it a language code.

    echo $de_DE->language('fr'); // Outputs "Französisch" - the German for French.



File structure for localisation data
------------------------------------

The data is housed under the data/ subdirectory and is arranged by major language code. Sub locales hold specialisations
of the parent language entries, and this structure prevents much repetition in the data set.

    data/
      |-- ar  << 2 letter folders hold files containing localisations
      .         for the base language they represent.
      .
      .
      |-- common             - This folder holds various data common to all areas.
      .
      .
      .
      |-- en                 - This folder holds general English localisations.
      |    |-- currency.php
      |    |-- language.php
      |    \-- country.php   - This file has the country name mappings in English.
      |
      |-- en_GB
      |     \-- country.php  - This file holds the just the diffs from en/country.php country name mappings.
      |
      |-- fr                 - This folder has the French localisations.
      |    |-- currency.php
      |    |-- language.php
      |    \-- country.php
      |
      |-- fr_FR
      |     |-- language.php
      |     \-- country.php
      .
      .
      .


License(s)
----------

Umpirsky's Country List data was used as the source for the files under the data/ directory and that project uses a MIT License.
My module is also issued under a MIT license (See LICENSE.txt.)
