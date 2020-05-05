---
title: Csfd Unofficial Api

language_tabs: # must be one of https://git.io/vQNgJ
- php

search: true
---
# Introduction

Welcome to the Csfd Unofficial API! You can use our API to access Csfd.cz content.
In examples we are using Symfony component called [The HttpClient Component](https://symfony.com/doc/current/components/http_client.html).

# Authentication

> Pass your API-key in all API requests as a header. To authorize, use this code:

> Request:

```php
<?php
$api_key = YOURAPIKEY;
$query_parameters = QUERYPARAMETERS;

$httpClient = HttpClient::create([
    'headers' => ['X-AUTH-API' => $api_key],
]);

$response = $httpClient->request('GET', 'https://affwebgen.com/api', ['query' => $query_parameters,]);

?>
```


> Make sure to replace `YOURAPIKEY` with your API key and replace `QUERYPARAMETERS` with parameters as it is defined in API.

Each project has different API key. Before making any request with your api key please be sure you configured allowed titles in [admin](https://affwebgen.com).

To make any request use api url: <code>https://affwebgen.com/api</code> and send us <code>GET</code> request.

<aside class="notice">
    You must replace <code>YOURAPIKEY</code> with your API key from your project in [admin](https://affwebgen.com).
</aside>

# Query Parameters
Query parameters are used to generated specific response. You can combine it in any way you want. Every response is JSON formated.
## Extra
> Request:

```php
<?php
$query_parameters = [
    'extra' => [
        ['function' => 'popularTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
        ['function' => 'latestTitles', 'parameters' => ['limit' => 2], 'properties' => ['imagePath']],
    ],
];

?>
```


> Response:

```json
{
   "extra":{
      "popularTitles":[
         {
            "id":4969,
            "name":"Nekonečný",
            "imagePath":null,
            "slug":"nekonecny"
         }
      ],
      "latestTitles":[
         {
            "id":5038,
            "name":"Socket",
            "imagePath":null,
            "slug":"socket"
         },
         {
            "id":5037,
            "name":"Pool Party",
            "imagePath":null,
            "slug":"pool-party"
         }
      ]
   }
}

```


    Required: false
    <table class="table table-responsive">
        <tr>
            <th>Function</th>
            <th>Parameters</th>
            <th>Properties</th>
            <th>Description</th>
        </tr>
                    <tr>
                <td>popularTitles</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>15</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, imagePath, slug</div>
    <div><span>**Valid Options:** </span>id, name, skName, czName, orgName, year, duration, description, imagePath, imagePathLarge, rating, premiereAt, local, slug, category</div>

                                    </td>
                <td>
                    list of popular titles
                </td>
            </tr>
                    <tr>
                <td>latestTitles</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>15</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, imagePath, slug</div>
    <div><span>**Valid Options:** </span>id, name, skName, czName, orgName, year, duration, description, imagePath, imagePathLarge, rating, premiereAt, local, slug, category</div>

                                    </td>
                <td>
                    list of latest titles
                </td>
            </tr>
            </table>







## Item (title)
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 9281,
        'entity' => 'Title',
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 9281,
    "name": "Avengers",
    "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
    "slug": "avengers"
  }
}

```


    Required: false

    <table class="table table-responsive">
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Allowed Values</th>
            <th>Format</th>
            <th>Description</th>
        </tr>
                    <tr>
                <td>entity</td>
                <td>                        yes
                                    </td>
                <td>
                                            Title
                                    </td>
                <td>
                    string
                </td>
                <td>static text, identify collection</td>
            </tr>
                    <tr>
                <td>id</td>
                <td>                        yes
                                    </td>
                <td>
                                                        </td>
                <td>
                    integer
                </td>
                <td>the ID of major title</td>
            </tr>
                    <tr>
                <td>properties</td>
                <td>                        no
                                    </td>
                <td>
                                                                        <a href="#properties">properties</a>
                                                            </td>
                <td>
                    array
                </td>
                <td>array of properties</td>
            </tr>
                    <tr>
                <td>relations</td>
                <td>                        no
                                    </td>
                <td>
                                                                        <a href="#relations">relations</a>
                                                            </td>
                <td>
                    array
                </td>
                <td>array of relations</td>
            </tr>
                    <tr>
                <td>methods</td>
                <td>                        no
                                    </td>
                <td>
                                                                        <a href="#methods">methods</a>
                                                            </td>
                <td>
                    array
                </td>
                <td>array of methods</td>
            </tr>
            </table>



### Properties
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 9281,
        'entity' => 'Title',
        'properties' => [
                'name', 'skName', 'czName', 'orgName', 'year', 'duration', 'description', 'imagePath', 'imagePathLarge', 'rating', 'premiereAt', 'local', 'slug'
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 9281,
    "name": "Avengers",
    "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
    "slug": "avengers",
    "skName": "Avengers: Pomstitelia",
    "czName": null,
    "orgName": "The Avengers",
    "year": 2012,
    "duration": 143,
    "description": "Marvel Studios uvádí super hrdinský tým všech dob Avengers, ve kterém se přestaví ikoničtí super hrdinové – Iron Man, Neuvěřitelný Hulk, Thor, Captain America, Hawkeye a Black Widow. Když se objeví nečekaný nepřítel, který ohrožuje světovou bezpečnost, Nick Fury, ředitel mezinárodní mírové agentury, známé také jako S.H.I.E.L.D., zjistí, že potřebuje tým, aby odvrátil světovou katastrofu. Začíná provádět nábor po celém světě.",
    "imagePathLarge": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h480",
    "rating": {
      "value": 83,
      "weight": 63921,
      "scale": 100
    },
    "premiereAt": "2012-05-03",
    "local": false
  }
}

```


    <table>
        <thead>
            <tr>
                <th>Default</th>
                <th>Valid Options</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>id, name, imagePath, slug</td>
                <td>id, name, skName, czName, orgName, year, duration, description, imagePath, imagePathLarge, rating, premiereAt, local, slug, category</td>
            </tr>
        </tbody>
    </table>




### Relations
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 9281,
        'entity' => 'Title',
        'relations' => [
            'cast' =>  ['parameters' => ['limit' => 1]],
            'countries' =>  ['parameters' => ['limit' => 2],],
            'genres' =>  ['parameters' => ['limit' => 1]],
            'titleNames' =>  ['parameters' => ['limit' => 1]],
            'titleSeries' =>  ['parameters' => ['limit' => 1]],
            'titleTags' =>  ['parameters' => ['limit' => 1]],
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 9281,
    "name": "Avengers",
    "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
    "slug": "avengers",
    "cast": [
      {
        "role": "2",
        "listOrder": 0,
        "person": {
          "id": 14417,
          "name": "Joss Whedon",
          "imagePath": null
        }
      }
    ],
    "countries": [
      {
        "id": 165,
        "name": "USA",
        "code": "us"
      }
    ],
    "genres": [
      {
        "id": 3,
        "name": "Akční"
      }
    ],
    "titleNames": [
      {
        "id": 1,
        "name": "The Avengers"
      }
    ],
    "titleSeries": [],
    "titleTags": [
      {
        "id": 5,
        "name": "vědci"
      }
    ]
  }
}

```


    <table class="table table-responsive">
        <tr>
            <th>Function</th>
            <th>Parameters</th>
            <th>Properties</th>
            <th>Description</th>
        </tr>
                    <tr>
                <td>cast</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>20</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>role, listOrder, person</div>
    <div><span>**Valid Options:** </span>role, listOrder, person</div>

                                    </td>
                <td>
                    list of cast
                </td>
            </tr>
                    <tr>
                <td>countries</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, code</div>
    <div><span>**Valid Options:** </span>id, name, code</div>

                                    </td>
                <td>
                    list of countries
                </td>
            </tr>
                    <tr>
                <td>genres</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name</div>
    <div><span>**Valid Options:** </span>id, name</div>

                                    </td>
                <td>
                    list of genres
                </td>
            </tr>
                    <tr>
                <td>titleNames</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name</div>
    <div><span>**Valid Options:** </span>id, name</div>

                                    </td>
                <td>
                    list of title names
                </td>
            </tr>
                    <tr>
                <td>titleSeries</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, numberOfSeries, numberOfEpisodes</div>
    <div><span>**Valid Options:** </span>id, numberOfSeries, numberOfEpisodes</div>

                                    </td>
                <td>
                    list of title series
                </td>
            </tr>
                    <tr>
                <td>titleTags</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name</div>
    <div><span>**Valid Options:** </span>id, name</div>

                                    </td>
                <td>
                    list of title tags
                </td>
            </tr>
            </table>






### Methods
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 9281,
        'entity' => 'Title',
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 9281,
    "name": "Avengers",
    "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
    "slug": "avengers",
    "otherTitles": [
      {
        "id": 1,
        "name": "Především nikomu neublížím",
        "imagePath": "https://img.csfd.cz/files/images/film/posters/000/384/384223_da0c9a.jpg?h180",
        "slug": "predevsim-nikomu-neublizim"
      }
    ]
  }
}

```


    <table class="table table-responsive">
        <tr>
            <th>Function</th>
            <th>Parameters</th>
            <th>Properties</th>
            <th>Description</th>
        </tr>
                    <tr>
                <td>otherTitles</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>10</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, imagePath, slug</div>
    <div><span>**Valid Options:** </span>id, name, skName, czName, orgName, year, duration, description, imagePath, imagePathLarge, rating, premiereAt, local, slug, category</div>

                                    </td>
                <td>
                    other titles based on major title
                </td>
            </tr>
            </table>





### Full Example (title)
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 9281,
        'entity' => 'Title',
        'properties' => [
            'name', 'skName', 'czName', 'orgName', 'year', 'duration', 'description', 'imagePath', 'imagePathLarge', 'rating', 'premiereAt', 'local'
        ],
        'relations' => [
            'cast' =>  ['parameters' => ['limit' => 1]],
            'countries' =>  ['parameters' => ['limit' => 2],],
            'genres' =>  ['parameters' => ['limit' => 1]],
            'titleNames' =>  ['parameters' => ['limit' => 1]],
            'titleSeries' =>  ['parameters' => ['limit' => 1]],
            'titleTags' =>  ['parameters' => ['limit' => 1]],
        ],
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
        ],
    ],
    'extra' => [
        ['function' => 'popularTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
        ['function' => 'latestTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
    ],
];
$api_key = YOURAPIKEY;

$httpClient = HttpClient::create([
    'headers' => ['X-AUTH-API' => $api_key],
]);

$response = $httpClient->request('GET', 'https://affwebgen.com/api', ['query' => $query_parameters,]);

?>
```


> Response:

```json
{
  "item": {
    "id": 9281,
    "name": "Avengers",
    "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
    "slug": "avengers",
    "skName": "Avengers: Pomstitelia",
    "czName": null,
    "orgName": "The Avengers",
    "year": 2012,
    "duration": 143,
    "description": "Marvel Studios uvádí super hrdinský tým všech dob Avengers, ve kterém se přestaví ikoničtí super hrdinové – Iron Man, Neuvěřitelný Hulk, Thor, Captain America, Hawkeye a Black Widow. Když se objeví nečekaný nepřítel, který ohrožuje světovou bezpečnost, Nick Fury, ředitel mezinárodní mírové agentury, známé také jako S.H.I.E.L.D., zjistí, že potřebuje tým, aby odvrátil světovou katastrofu. Začíná provádět nábor po celém světě.",
    "imagePathLarge": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h480",
    "rating": {
      "value": 83,
      "weight": 63921,
      "scale": 100
    },
    "premiereAt": "2012-05-03",
    "local": false,
    "cast": [
      {
        "role": "2",
        "listOrder": 0,
        "person": {
          "id": 14417,
          "name": "Joss Whedon",
          "imagePath": null
        }
      }
    ],
    "countries": [
      {
        "id": 165,
        "name": "USA",
        "code": "us"
      }
    ],
    "genres": [
      {
        "id": 3,
        "name": "Akční"
      }
    ],
    "titleNames": [
      {
        "id": 1,
        "name": "The Avengers"
      }
    ],
    "titleSeries": [],
    "titleTags": [
      {
        "id": 5,
        "name": "vědci"
      }
    ],
    "otherTitles": [
      {
        "id": 1,
        "name": "Především nikomu neublížím",
        "imagePath": "https://img.csfd.cz/files/images/film/posters/000/384/384223_da0c9a.jpg?h180",
        "slug": "predevsim-nikomu-neublizim"
      }
    ]
  },
  "extra": {
    "popularTitles": [
      {
        "id": 9281,
        "name": "Avengers",
        "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
        "slug": "avengers"
      }
    ],
    "latestTitles": [
      {
        "id": 9281,
        "name": "Avengers",
        "imagePath": "https://img.csfd.cz/files/images/film/posters/000/486/486686_69f4e4.jpg?h180",
        "slug": "avengers"
      }
    ]
  }
}

```

Working example with full configuration for title
## Item (person)
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 1,
        'entity' => 'Person',
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 1,
    "name": "Jerry Zucker",
    "imagePath": "https://img.csfd.cz/files/images/creator/photos/000/269/269781_2d796d.jpg?w100h132crop"
  }
}

```


    Required: false

    <table class="table table-responsive">
        <tr>
            <th>Parameter</th>
            <th>Required</th>
            <th>Allowed Values</th>
            <th>Format</th>
            <th>Description</th>
        </tr>
                    <tr>
                <td>entity</td>
                <td>                        yes
                                    </td>
                <td>
                                            Person
                                    </td>
                <td>
                    string
                </td>
                <td>static text, identify collection</td>
            </tr>
                    <tr>
                <td>id</td>
                <td>                        yes
                                    </td>
                <td>
                                                        </td>
                <td>
                    integer
                </td>
                <td>the ID of major person</td>
            </tr>
                    <tr>
                <td>properties</td>
                <td>                        no
                                    </td>
                <td>
                                                                        <a href="#properties-2">properties</a>
                                                            </td>
                <td>
                    array
                </td>
                <td>array of properties</td>
            </tr>
                    <tr>
                <td>methods</td>
                <td>                        no
                                    </td>
                <td>
                                                                        <a href="#methods-2">methods</a>
                                                            </td>
                <td>
                    array
                </td>
                <td>array of methods</td>
            </tr>
            </table>



### Properties
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 1,
        'entity' => 'Person',
        'properties' => [
                'name', 'lastname', 'imagePath', 'imagePathLarge', 'description', 'birthDt', 'birthPlace', 'deathDt', 'deathPlace', 'local', 'popularity'
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 1,
    "name": "Jerry Zucker",
    "imagePath": "https://img.csfd.cz/files/images/creator/photos/000/269/269781_2d796d.jpg?w100h132crop",
    "lastname": "Zucker",
    "imagePathLarge": "https://img.csfd.cz/files/images/creator/photos/000/269/269781_2d796d.jpg?h480",
    "description": "Je nejmladším členem proslulé trojice ZAZ (do níž náleží jeho starší bratr David a Jim Abrahams), která je považována za nejvýznamnější tvůrce americké filmové parodie. Jejich práce se po většinu kariéry prolínala a proto jsou jejich životopisy velmi podobné. Často spolupracují ještě se scenáristou Patem Proftem. První společný projekt, na kterém se ZAZ podíleli byla komedie KENTUCKY FRIED MOVIE z roku 1977. Jerry posléze spolupracoval na režii komediálního muzikálu ROCK´N´ROLL HIGH SCHOOL, se slavnou americkou punkovou kapelou Ramones v hlavních rolích. V roce 1980 přichází první společný režijní počin ZAZ - snímek PŘIPOUTEJTE SE, PROSÍM!, jež se dočkal mnoha ocenění a odstartoval sérii ztřeštěných parodií zmiňované trojice. Jerry se na mnoha těchto filmech střídavě podílel jako režisér, scenárista i producent. Za zmínku stojí například seriál POLICE SQUAD! parodující televizní krimi-série, jenž se dočkal převedení i do filmové podoby jako BLÁZNIVÁ STŘELA (Jerry napsal scénář ke všem třem filmovým dílům).<br><br>V 90. letech se členové ZAZ vydali každý svojí cestou. Mladší z bratrů Zuckerových překvapil v roce 1990 režií lehce komediálního melodramatu s Patrickem Swayzem a Whoopi Goldberg DUCH. Jednalo se o Jerryho první samostatný projekt a hned se dočkal nominace na pět Oscarů, včetně toho za nejlepší film. Dvě sošky (za nejlepší scénář a ženský herecký výkon ve vedlejší roli) nakonec skutečně získal.<br><br>V roce 1995 Jerry převzal po zesnulém režisérovi Terenci Youngovi režii netradiční adaptace legendy o králi Artušovi PRVNÍ RYTÍŘ s Seanem Connerym a Richardem Gerem. Snímek ovšem příliš nezabodoval. Naposledy se oblíbený tvůrce vrátil na režisérskou stoličku v roce 2001, kdy natočil dobrodružnou crazy komedii s hvězdným obsazením MILIÓNOVÝ ZÁVOD. Od té doby si dal od filmování delší pauzu a v současné době se věnuje výhradně filmové produkci.<br><br>Stejně jako jeho bratr David a Jim Abrahams i Jerry rád obsazuje do miniaturních úloh členy své rodiny a sem tam si sám rovněž zahraje nějakou tu cameo roli.",
    "birthDt": "1950-03-11",
    "birthPlace": "Milwaukee, Wisconsin, USA",
    "deathDt": null,
    "deathPlace": null,
    "local": false,
    "popularity": 0
  }
}

```


    <table>
        <thead>
            <tr>
                <th>Default</th>
                <th>Valid Options</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>id, name, imagePath</td>
                <td>id, name, lastname, imagePath, imagePathLarge, description, birthDt, birthPlace, deathDt, deathPlace, local, popularity</td>
            </tr>
        </tbody>
    </table>





### Methods
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 1,
        'entity' => 'Person',
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 1,
    "name": "Jerry Zucker",
    "imagePath": "https://img.csfd.cz/files/images/creator/photos/000/269/269781_2d796d.jpg?w100h132crop",
    "otherTitles": [
      {
        "id": 2,
        "name": "Připoutejte se, prosím!",
        "imagePath": "https://img.csfd.cz/files/images/film/posters/158/494/158494389_fd1b24.jpg?h180",
        "slug": "pripoutejte-se-prosim"
      }
    ]
  }
}

```


    <table class="table table-responsive">
        <tr>
            <th>Function</th>
            <th>Parameters</th>
            <th>Properties</th>
            <th>Description</th>
        </tr>
                    <tr>
                <td>otherTitles</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>30</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, imagePath, slug</div>
    <div><span>**Valid Options:** </span>id, name, skName, czName, orgName, year, duration, description, imagePath, imagePathLarge, rating, premiereAt, local, slug, category</div>

                                    </td>
                <td>
                    titles from major person
                </td>
            </tr>
            </table>





### Full Example (person)
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 1,
        'entity' => 'Person',
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imagePath']],
        ],
        'properties' => [
            'name', 'lastname', 'imagePath', 'imagePathLarge', 'description', 'birthDt', 'birthPlace', 'deathDt', 'deathPlace', 'local', 'popularity'
        ],
    ],
];
$api_key = YOURAPIKEY;

$httpClient = HttpClient::create([
    'headers' => ['X-AUTH-API' => $api_key],
]);

$response = $httpClient->request('GET', 'https://affwebgen.com/api', ['query' => $query_parameters,]);

?>
```


> Response:

```json
{
  "item": {
    "id": 1,
    "name": "Jerry Zucker",
    "imagePath": "https://img.csfd.cz/files/images/creator/photos/000/269/269781_2d796d.jpg?w100h132crop",
    "lastname": "Zucker",
    "imagePathLarge": "https://img.csfd.cz/files/images/creator/photos/000/269/269781_2d796d.jpg?h480",
    "description": "Je nejmladším členem proslulé trojice ZAZ (do níž náleží jeho starší bratr David a Jim Abrahams), která je považována za nejvýznamnější tvůrce americké filmové parodie. Jejich práce se po většinu kariéry prolínala a proto jsou jejich životopisy velmi podobné. Často spolupracují ještě se scenáristou Patem Proftem. První společný projekt, na kterém se ZAZ podíleli byla komedie KENTUCKY FRIED MOVIE z roku 1977. Jerry posléze spolupracoval na režii komediálního muzikálu ROCK´N´ROLL HIGH SCHOOL, se slavnou americkou punkovou kapelou Ramones v hlavních rolích. V roce 1980 přichází první společný režijní počin ZAZ - snímek PŘIPOUTEJTE SE, PROSÍM!, jež se dočkal mnoha ocenění a odstartoval sérii ztřeštěných parodií zmiňované trojice. Jerry se na mnoha těchto filmech střídavě podílel jako režisér, scenárista i producent. Za zmínku stojí například seriál POLICE SQUAD! parodující televizní krimi-série, jenž se dočkal převedení i do filmové podoby jako BLÁZNIVÁ STŘELA (Jerry napsal scénář ke všem třem filmovým dílům).<br><br>V 90. letech se členové ZAZ vydali každý svojí cestou. Mladší z bratrů Zuckerových překvapil v roce 1990 režií lehce komediálního melodramatu s Patrickem Swayzem a Whoopi Goldberg DUCH. Jednalo se o Jerryho první samostatný projekt a hned se dočkal nominace na pět Oscarů, včetně toho za nejlepší film. Dvě sošky (za nejlepší scénář a ženský herecký výkon ve vedlejší roli) nakonec skutečně získal.<br><br>V roce 1995 Jerry převzal po zesnulém režisérovi Terenci Youngovi režii netradiční adaptace legendy o králi Artušovi PRVNÍ RYTÍŘ s Seanem Connerym a Richardem Gerem. Snímek ovšem příliš nezabodoval. Naposledy se oblíbený tvůrce vrátil na režisérskou stoličku v roce 2001, kdy natočil dobrodružnou crazy komedii s hvězdným obsazením MILIÓNOVÝ ZÁVOD. Od té doby si dal od filmování delší pauzu a v současné době se věnuje výhradně filmové produkci.<br><br>Stejně jako jeho bratr David a Jim Abrahams i Jerry rád obsazuje do miniaturních úloh členy své rodiny a sem tam si sám rovněž zahraje nějakou tu cameo roli.",
    "birthDt": "1950-03-11",
    "birthPlace": "Milwaukee, Wisconsin, USA",
    "deathDt": null,
    "deathPlace": null,
    "local": false,
    "popularity": 0,
    "otherTitles": [
      {
        "id": 2,
        "name": "Připoutejte se, prosím!",
        "imagePath": "https://img.csfd.cz/files/images/film/posters/158/494/158494389_fd1b24.jpg?h180",
        "slug": "pripoutejte-se-prosim"
      }
    ]
  }
}

```

Working example with full configuration for person


