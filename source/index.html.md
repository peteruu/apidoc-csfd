---
title: Csfd Unofficial Api

language_tabs: # must be one of https://git.io/vQNgJ
- php

search: true
---
# Introduction

Welcome to the Csfd Unofficial API! You can use our API to access Imdb content.
In examples we are using Symfony component called [The HttpClient Component](https://symfony.com/doc/current/components/http_client.html).

# Authentication

> Pass your API-key in all API requests as a header. To authorize, use this code:

> Request:

```php
<?php
$api_key = YOURAPIKEY;
$query_parameters = QUERYPARAMETERS;
$host = YOURDOMAIN;

$httpClient = HttpClient::create([
    'headers' => ['X-AUTH-API' => $api_key, 'Referer' => $host],
]);

$response = $httpClient->request('GET', 'https://affwebgen.com/api', ['query' => $query_parameters,]);

?>
```


> Make sure to replace `YOURAPIKEY` with your API key,  `QUERYPARAMETERS` with parameters as it is defined in API and YOURDOMAIN with domainname from which you will make requests for example asdf.com.

Each project has different API key. Before making any request with your api key please be sure you configured allowed titles in [admin](https://affwebgen.com).

To make any request use api url: <code>https://affwebgen.com/api</code> and send us <code>GET</code> request.

<aside class="notice">
    You must replace <code>YOURAPIKEY</code> with your API key  and <code>YOURDOMAIN</code> with your domain name from your project in admin.
</aside>

# Query Parameters
Query parameters are used to generated specific response. You can combine it in any way you want. Every response is JSON formated.
## Extra
> Request:

```php
<?php
$query_parameters = [
    'extra' => [
        ['function' => 'popularTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
        ['function' => 'latestTitles', 'parameters' => ['limit' => 2], 'properties' => ['imageSrc']],
        ['function' => 'latestEpisodes', 'parameters' => ['limit' => 1], 'properties' => ['episodeParent']],
    ],
];

?>
```


> Response:

```json
{
  "extra": {
    "popularTitles": [
      {
        "id": 587,
        "name": "Entertainers with Byron Allen",
        "slug": "entertainers-with-byron-allen",
        "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg"
      }
    ],
    "latestTitles": [
      {
        "id": 4871906,
        "name": "Ilox",
        "slug": "ilox",
        "imageSrc": null
      },
      {
        "id": 4866166,
        "name": "Shangoul & Mangoul",
        "slug": "shangoul-mangoul",
        "imageSrc": null
      }
    ],
    "latestEpisodes": [
      {
        "id": 4894909,
        "name": "Episode dated 25 May 2005",
        "slug": "episode-dated-25-may-2005",
        "imageSrc": null,
        "episodeParent": {
          "id": 1066875,
          "name": "El mundo en 24 horas",
          "slug": "el-mundo-en-24-horas",
          "imageSrc": null
        }
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
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

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
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

                                    </td>
                <td>
                    list of latest titles
                </td>
            </tr>
                    <tr>
                <td>latestEpisodes</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>15</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

                                    </td>
                <td>
                    list of latest episodes
                </td>
            </tr>
            </table>







## Item (title)
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 587,
        'entity' => 'Title',
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 587,
    "name": "Entertainers with Byron Allen",
    "slug": "entertainers-with-byron-allen",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg"
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
        'id' => 587,
        'entity' => 'Title',
        'properties' => [
            'description', 'imageSrc', 'season', 'episode', 'duration', 'contentRating', 'metascore',
            'locations','keywords', 'awards', 'rating', 'releasedYear', 'releasedMonth', 'releasedDay','category',
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 587,
    "name": "Entertainers with Byron Allen",
    "slug": "entertainers-with-byron-allen",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg",
    "description": null,
    "season": null,
    "episode": null,
    "duration": null,
    "contentRating": null,
    "metascore": null,
    "locations": [],
    "keywords": [],
    "awards": [],
    "rating": {
      "value": "2.800",
      "weight": 36,
      "scale": 10
    },
    "releasedYear": 2000,
    "releasedMonth": null,
    "releasedDay": null,
    "category": "TV Series"
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
                <td>id, name, slug, imageSrc</td>
                <td>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</td>
            </tr>
        </tbody>
    </table>




### Relations
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 587,
        'entity' => 'Title',
        'relations' => [
            'cast' =>  ['parameters' => ['limit' => 1]],
            'companies' => ['parameters' => ['limit' => 1]],
            'countries' =>  ['parameters' => ['limit' => 2],],
            'languages' =>  ['parameters' => ['limit' => 1],],
            'externalSites' =>  ['parameters' => ['limit' => 1]],
            'genres' =>  ['parameters' => ['limit' => 1]],
            'photos' =>  ['parameters' => ['limit' => 1]],
            'reviews' =>  ['parameters' => ['limit' => 1]],
            'plotSummaries' =>  ['parameters' => ['limit' => 1]],
            'trivia' =>  ['parameters' => ['limit' => 1]],
            'videos' =>  ['parameters' => ['limit' => 1]],
            'trailer' =>  ['parameters' => ['limit' => 1]],
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 587,
    "name": "Entertainers with Byron Allen",
    "slug": "entertainers-with-byron-allen",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg",
    "cast": [
      {
        "role": "star",
        "characterName": null,
        "person": {
          "id": 1756,
          "name": "Emily Blunt"
        }
      }
    ],
    "companies": [],
    "countries": [
      {
        "id": 1,
        "name": "USA",
        "code": "US"
      }
    ],
    "languages": [
      {
        "id": 74,
        "name": "English",
        "code": "en"
      }
    ],
    "externalSites": [],
    "genres": [
      {
        "id": 14,
        "name": "Documentary"
      }
    ],
    "photos": [
      {
        "id": 1462,
        "name": "Entertainers with Byron Allen (2000)",
        "imageSrc": "https://m.media-amazon.com/images/M/MV5BNzdlM2RlNTQtZDA5OC00NDRjLWIwMTYtY2M5MTliMmVmMGNlXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY99_CR25,0,99,99_AL_.jpg"
      }
    ],
    "reviews": [
      {
        "id": 8795,
        "name": "It's 3am ...",
        "content": "I can't sleep, so I'm flipping the dial and see this dude that looks a lot like Byron Allen but the guy's head is shaved and the show is called \"Entertainment Studios.com\". HUH?? Was I having a nightmare or was this dreck actually being broadcast?The show's entire content is made up of promo interviews provided by the studios, along with movie trailers, bad comics, and music videos. Between the cheesy music, the obsolete graphics, Allen as host, his wife(?)as producer, and the aforementioned filler, what's the budget...about $47.26 an episode?I somehow stumbled through the entire program and SWEAR that Allen said \"Comin' up neeeeext\" prior to every commercial break. Wasn't this guy a comedian at one point in his career? How about some original material, fella?? Anyway, if you want a belly laugh, stay with the show until the end credits and you will be rewarded with a can't miss REALLY bad edit as the music loop runs out. Maybe Byron does the sound editing as well to save a few more bucks?? This really IS syndicated programming at its worst. I'd prefer watching \"Conversation with Fred Lewis\" a 1980's infomercial for New Generation hair growth shampoo...",
        "category": "reviews",
        "rating": {
          "value": "0.727",
          "weight": 22,
          "scale": 1
        },
        "titleRating": {
          "value": "1.000",
          "weight": 1,
          "scale": 10
        }
      }
    ],
    "plotSummaries": [],
    "trivia": [],
    "videos": [],
    "trailer": []
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
                                                <div><span>**Default:** </span>role, characterName, person</div>
    <div><span>**Valid Options:** </span>role, characterName, person</div>

                                    </td>
                <td>
                    list of cast
                </td>
            </tr>
                    <tr>
                <td>companies</td>
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
                    list of companies
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
                <td>languages</td>
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
                    list of languages
                </td>
            </tr>
                    <tr>
                <td>externalSites</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, cloakedUrl</div>
    <div><span>**Valid Options:** </span>id, name, cloakedUrl</div>

                                    </td>
                <td>
                    list of external sites
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
                <td>photos</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, imageSrc</div>

                                    </td>
                <td>
                    list of photos
                </td>
            </tr>
                    <tr>
                <td>reviews</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, content, category, rating, titleRating</div>
    <div><span>**Valid Options:** </span>id, name, content, category, rating, titleRating</div>

                                    </td>
                <td>
                    list of reviews
                </td>
            </tr>
                    <tr>
                <td>videos</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, externalId, name, category, duration, imageSrc</div>
    <div><span>**Valid Options:** </span>id, externalId, name, category, duration, imageSrc</div>

                                    </td>
                <td>
                    list of videos
                </td>
            </tr>
                    <tr>
                <td>trailer</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, externalId, name, category, duration, imageSrc</div>
    <div><span>**Valid Options:** </span>id, externalId, name, category, duration, imageSrc</div>

                                    </td>
                <td>
                    list of trailers
                </td>
            </tr>
                    <tr>
                <td>plotSummaries</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, content, category, rating, titleRating</div>
    <div><span>**Valid Options:** </span>id, name, content, category, rating, titleRating</div>

                                    </td>
                <td>
                    list of plot summaries
                </td>
            </tr>
                    <tr>
                <td>trivia</td>
                <td>
                                                                            <div><span>**Name:** </span>limit</div>
    <div><span>**Required:** </span> yes </div>
    <div><span>**Type:** </span>int</div>
    <div><span>**Max value:** </span>5</div>
    
                                                            </td>
                <td>
                                                <div><span>**Default:** </span>id, name, content, category, rating, titleRating</div>
    <div><span>**Valid Options:** </span>id, name, content, category, rating, titleRating</div>

                                    </td>
                <td>
                    list of trivia
                </td>
            </tr>
            </table>






### Methods
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 587,
        'entity' => 'Title',
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
            ['function' => 'randomDescription'],
            ['function' => 'listSeasons', ],
            ['function' => 'listSeasonsWithEpisodes', ],
            ['function' => 'nextEpisode', 'properties' => ['season', 'episode']],
            ['function' => 'previousEpisode', 'properties' => ['season', 'episode']],
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 587,
    "name": "Entertainers with Byron Allen",
    "slug": "entertainers-with-byron-allen",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg",
    "otherTitles": [
      {
        "id": 654,
        "name": "2000 Blockbuster Entertainment Awards",
        "slug": "2000-blockbuster-entertainment-awards",
        "imageSrc": null
      }
    ],
    "randomDescription": "I can't sleep, so I'm flipping the dial and see this dude that looks a lot like Byron Allen but the guy's head is shaved and the show is called \"Entertainment Studios.com\". HUH?? Was I having a nightmare or was this dreck actually being broadcast?The show's entire content is made up of promo interviews provided by the studios, along with movie trailers, bad comics, and music videos. Between the cheesy music, the obsolete graphics, Allen as host, his wife(?)as producer, and the aforementioned filler, what's the budget...about $47.26 an episode?I somehow stumbled through the entire program and SWEAR that Allen said \"Comin' up neeeeext\" prior to every commercial break. Wasn't this guy a comedian at one point in his career? How about some original material, fella?? Anyway, if you want a belly laugh, stay with the show until the end credits and you will be rewarded with a can't miss REALLY bad edit as the music loop runs out. Maybe Byron does the sound editing as well to save a few more bucks?? This really IS syndicated programming at its worst. I'd prefer watching \"Conversation with Fred Lewis\" a 1980's infomercial for New Generation hair growth shampoo...",
    "listSeasons": [
      "-1",
      "25"
    ],
    "listSeasonsWithEpisodes": {
      "25": [
        {
          "id": 98106,
          "name": "Episode #25.4",
          "slug": "episode-25-4",
          "imageSrc": null,
          "season": 25,
          "episode": 4
        }
      ],
      "-1": [
        {
          "id": 265482,
          "name": "Episode dated 31 March 2008",
          "slug": "episode-dated-31-march-2008",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 196155,
          "name": "Episode dated 6 October 2012",
          "slug": "episode-dated-6-october-2012",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 159863,
          "name": "Episode dated 29 January 2000",
          "slug": "episode-dated-29-january-2000",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 368517,
          "name": "Episode dated 7 November 2016",
          "slug": "episode-dated-7-november-2016",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 368518,
          "name": "Episode dated 31 October 2016",
          "slug": "episode-dated-31-october-2016",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 50342,
          "name": "Episode dated 11 March 2013",
          "slug": "episode-dated-11-march-2013",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 2874580,
          "name": "Episode dated 17 December 2011",
          "slug": "episode-dated-17-december-2011",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 2874583,
          "name": "Episode dated 12 November 2011",
          "slug": "episode-dated-12-november-2011",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 259040,
          "name": "Episode dated 18 February 2012",
          "slug": "episode-dated-18-february-2012",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 32762,
          "name": "Episode dated 11 June 2012",
          "slug": "episode-dated-11-june-2012",
          "imageSrc": null,
          "season": null,
          "episode": null
        }
      ]
    },
    "nextEpisode": null,
    "previousEpisode": null
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
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

                                    </td>
                <td>
                    other titles based on major title
                </td>
            </tr>
                    <tr>
                <td>randomDescription</td>
                <td>
                                            None.
                                    </td>
                <td>
                                            None.
                                    </td>
                <td>
                    generate random description
                </td>
            </tr>
                    <tr>
                <td>listSeasons</td>
                <td>
                                            None.
                                    </td>
                <td>
                                            None.
                                    </td>
                <td>
                    list of seasons if major entity is a tv show
                </td>
            </tr>
                    <tr>
                <td>listSeasonsWithEpisodes</td>
                <td>
                                            None.
                                    </td>
                <td>
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

                                    </td>
                <td>
                    list of seasons with episodes as objects
                </td>
            </tr>
                    <tr>
                <td>nextEpisode</td>
                <td>
                                            None.
                                    </td>
                <td>
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

                                    </td>
                <td>
                    next episode if major entity is episode
                </td>
            </tr>
                    <tr>
                <td>previousEpisode</td>
                <td>
                                            None.
                                    </td>
                <td>
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

                                    </td>
                <td>
                    previous episode if major entity is episode
                </td>
            </tr>
            </table>





### Full Example (title)
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 587,
        'entity' => 'Title',
        'properties' => [
            'description', 'imageSrc', 'season', 'episode', 'duration', 'contentRating', 'metascore',
            'locations','keywords', 'awards', 'rating', 'releasedYear', 'releasedMonth', 'releasedDay','category',
        ],
        'relations' => [
            'cast' =>  ['parameters' => ['limit' => 1]],
            'companies' => ['parameters' => ['limit' => 1]],
            'countries' =>  ['parameters' => ['limit' => 1],],
            'languages' =>  ['parameters' => ['limit' => 1],],
            'externalSites' =>  ['parameters' => ['limit' => 1]],
            'genres' =>  ['parameters' => ['limit' => 1]],
            'photos' =>  ['parameters' => ['limit' => 1]],
            'reviews' =>  ['parameters' => ['limit' => 1]],
            'plotSummaries' =>  ['parameters' => ['limit' => 1]],
            'trivia' =>  ['parameters' => ['limit' => 1]],
            'videos' =>  ['parameters' => ['limit' => 1]],
            'trailer' =>  ['parameters' => ['limit' => 1]],
        ],
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
            ['function' => 'randomDescription'],
            ['function' => 'listSeasons', ],
            ['function' => 'listSeasonsWithEpisodes', ],
            ['function' => 'nextEpisode', 'properties' => ['season', 'episode']],
            ['function' => 'previousEpisode', 'properties' => ['season', 'episode']],
        ],
    ],
    'extra' => [
        ['function' => 'popularTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
        ['function' => 'latestTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
        ['function' => 'latestEpisodes', 'parameters' => ['limit' => 1], 'properties' => ['episodeParent']],
    ],
];
$api_key = YOURAPIKEY;
$host = YOURDOMAIN;

$httpClient = HttpClient::create([
    'headers' => ['X-AUTH-API' => $api_key, 'Referer' => $host],
]);

$response = $httpClient->request('GET', 'https://affwebgen.com/api', ['query' => $query_parameters,]);

?>
```


> Response:

```json
{
  "item": {
    "id": 587,
    "name": "Entertainers with Byron Allen",
    "slug": "entertainers-with-byron-allen",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg",
    "description": null,
    "season": null,
    "episode": null,
    "duration": null,
    "contentRating": null,
    "metascore": null,
    "locations": [],
    "keywords": [],
    "awards": [],
    "rating": {
      "value": "2.800",
      "weight": 36,
      "scale": 10
    },
    "releasedYear": 2000,
    "releasedMonth": null,
    "releasedDay": null,
    "category": "TV Series",
    "cast": [
      {
        "role": "star",
        "characterName": null,
        "person": {
          "id": 1756,
          "name": "Emily Blunt"
        }
      }
    ],
    "companies": [],
    "countries": [
      {
        "id": 1,
        "name": "USA",
        "code": "US"
      }
    ],
    "languages": [
      {
        "id": 74,
        "name": "English",
        "code": "en"
      }
    ],
    "externalSites": [],
    "genres": [
      {
        "id": 14,
        "name": "Documentary"
      }
    ],
    "photos": [
      {
        "id": 1462,
        "name": "Entertainers with Byron Allen (2000)",
        "imageSrc": "https://m.media-amazon.com/images/M/MV5BNzdlM2RlNTQtZDA5OC00NDRjLWIwMTYtY2M5MTliMmVmMGNlXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY99_CR25,0,99,99_AL_.jpg"
      }
    ],
    "reviews": [
      {
        "id": 8795,
        "name": "It's 3am ...",
        "content": "I can't sleep, so I'm flipping the dial and see this dude that looks a lot like Byron Allen but the guy's head is shaved and the show is called \"Entertainment Studios.com\". HUH?? Was I having a nightmare or was this dreck actually being broadcast?The show's entire content is made up of promo interviews provided by the studios, along with movie trailers, bad comics, and music videos. Between the cheesy music, the obsolete graphics, Allen as host, his wife(?)as producer, and the aforementioned filler, what's the budget...about $47.26 an episode?I somehow stumbled through the entire program and SWEAR that Allen said \"Comin' up neeeeext\" prior to every commercial break. Wasn't this guy a comedian at one point in his career? How about some original material, fella?? Anyway, if you want a belly laugh, stay with the show until the end credits and you will be rewarded with a can't miss REALLY bad edit as the music loop runs out. Maybe Byron does the sound editing as well to save a few more bucks?? This really IS syndicated programming at its worst. I'd prefer watching \"Conversation with Fred Lewis\" a 1980's infomercial for New Generation hair growth shampoo...",
        "category": "reviews",
        "rating": {
          "value": "0.727",
          "weight": 22,
          "scale": 1
        },
        "titleRating": {
          "value": "1.000",
          "weight": 1,
          "scale": 10
        }
      }
    ],
    "plotSummaries": [],
    "trivia": [],
    "videos": [],
    "trailer": [],
    "otherTitles": [
      {
        "id": 654,
        "name": "2000 Blockbuster Entertainment Awards",
        "slug": "2000-blockbuster-entertainment-awards",
        "imageSrc": null
      }
    ],
    "randomDescription": "I can't sleep, so I'm flipping the dial and see this dude that looks a lot like Byron Allen but the guy's head is shaved and the show is called \"Entertainment Studios.com\". HUH?? Was I having a nightmare or was this dreck actually being broadcast?The show's entire content is made up of promo interviews provided by the studios, along with movie trailers, bad comics, and music videos. Between the cheesy music, the obsolete graphics, Allen as host, his wife(?)as producer, and the aforementioned filler, what's the budget...about $47.26 an episode?I somehow stumbled through the entire program and SWEAR that Allen said \"Comin' up neeeeext\" prior to every commercial break. Wasn't this guy a comedian at one point in his career? How about some original material, fella?? Anyway, if you want a belly laugh, stay with the show until the end credits and you will be rewarded with a can't miss REALLY bad edit as the music loop runs out. Maybe Byron does the sound editing as well to save a few more bucks?? This really IS syndicated programming at its worst. I'd prefer watching \"Conversation with Fred Lewis\" a 1980's infomercial for New Generation hair growth shampoo...",
    "listSeasons": [
      "-1",
      "25"
    ],
    "listSeasonsWithEpisodes": {
      "25": [
        {
          "id": 98106,
          "name": "Episode #25.4",
          "slug": "episode-25-4",
          "imageSrc": null,
          "season": 25,
          "episode": 4
        }
      ],
      "-1": [
        {
          "id": 265482,
          "name": "Episode dated 31 March 2008",
          "slug": "episode-dated-31-march-2008",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 196155,
          "name": "Episode dated 6 October 2012",
          "slug": "episode-dated-6-october-2012",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 159863,
          "name": "Episode dated 29 January 2000",
          "slug": "episode-dated-29-january-2000",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 368517,
          "name": "Episode dated 7 November 2016",
          "slug": "episode-dated-7-november-2016",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 368518,
          "name": "Episode dated 31 October 2016",
          "slug": "episode-dated-31-october-2016",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 50342,
          "name": "Episode dated 11 March 2013",
          "slug": "episode-dated-11-march-2013",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 2874580,
          "name": "Episode dated 17 December 2011",
          "slug": "episode-dated-17-december-2011",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 2874583,
          "name": "Episode dated 12 November 2011",
          "slug": "episode-dated-12-november-2011",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 259040,
          "name": "Episode dated 18 February 2012",
          "slug": "episode-dated-18-february-2012",
          "imageSrc": null,
          "season": null,
          "episode": null
        },
        {
          "id": 32762,
          "name": "Episode dated 11 June 2012",
          "slug": "episode-dated-11-june-2012",
          "imageSrc": null,
          "season": null,
          "episode": null
        }
      ]
    },
    "nextEpisode": null,
    "previousEpisode": null
  },
  "extra": {
    "popularTitles": [
      {
        "id": 587,
        "name": "Entertainers with Byron Allen",
        "slug": "entertainers-with-byron-allen",
        "imageSrc": "https://m.media-amazon.com/images/M/MV5BMWFlM2IwNmItZjRhMS00NDk2LTlhNzgtZjczNDFlN2MzYzEzXkEyXkFqcGdeQXVyMzk3NDAxMzk@._V1_UY268_CR12,0,182,268_AL_.jpg"
      }
    ],
    "latestTitles": [
      {
        "id": 4871906,
        "name": "Ilox",
        "slug": "ilox",
        "imageSrc": null
      }
    ],
    "latestEpisodes": [
      {
        "id": 4894909,
        "name": "Episode dated 25 May 2005",
        "slug": "episode-dated-25-may-2005",
        "imageSrc": null,
        "episodeParent": {
          "id": 1066875,
          "name": "El mundo en 24 horas",
          "slug": "el-mundo-en-24-horas",
          "imageSrc": null
        }
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
        'id' => 2433,
        'entity' => 'Person',
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 2433,
    "name": "Keanu Reeves"
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
        'id' => 2433,
        'entity' => 'Person',
        'properties' => [
            'id', 'name', 'imageSrc', 'description', 'birthYear', 'birthMonth', 'birthDay', 'birthPlace',
            'deathYear', 'deathMonth', 'deathDay', 'deathPlace'
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 2433,
    "name": "Keanu Reeves",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BNjUxNDcwMTg4Ml5BMl5BanBnXkFtZTcwMjU4NDYyOA@@._V1_UY317_CR15,0,214,317_AL_.jpg",
    "description": "Keanu Charles Reeves, whose first name means \"cool breeze over the mountains\" in Hawaiian, was born September 2, 1964 in Beirut, Lebanon. He is the son of Patricia Taylor, a showgirl and costume designer, and Samuel Nowlin Reeves, a geologist. Keanu's father was born in Hawaii, of British, Portuguese, Native Hawaiian, and Chinese ancestry, and ...",
    "birthYear": 1964,
    "birthMonth": 9,
    "birthDay": 2,
    "birthPlace": "Beirut, Lebanon",
    "deathYear": null,
    "deathMonth": null,
    "deathDay": null,
    "deathPlace": null
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
                <td>id, name</td>
                <td>id, name, imageSrc, description, birthYear, birthMonth, birthDay, birthPlace, deathYear, deathMonth, deathDay, deathPlace</td>
            </tr>
        </tbody>
    </table>





### Methods
> Request:

```php
<?php
$query_parameters = [
    'item' => [
        'id' => 2433,
        'entity' => 'Person',
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
        ],
    ],
];

?>
```


> Response:

```json
{
  "item": {
    "id": 2433,
    "name": "Keanu Reeves",
    "otherTitles": [
      {
        "id": 204430,
        "name": "Episode dated 2 September 2014",
        "slug": "episode-dated-2-september-2014",
        "imageSrc": null
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
                                                <div><span>**Default:** </span>id, name, slug, imageSrc</div>
    <div><span>**Valid Options:** </span>id, name, description, imageSrc, season, episode, duration, contentRating, metascore, locations, keywords, awards, rating, releasedYear, releasedMonth, releasedDay, episodeParent, slug, category</div>

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
        'id' => 2433,
        'entity' => 'Person',
        'methods' => [
            ['function' => 'otherTitles', 'parameters' => ['limit' => 1], 'properties' => ['imageSrc']],
        ],
        'properties' => [
            'id', 'name', 'imageSrc', 'description', 'birthYear', 'birthMonth', 'birthDay', 'birthPlace',
            'deathYear', 'deathMonth', 'deathDay', 'deathPlace'
        ],
    ],
];
$api_key = YOURAPIKEY;
$host = YOURDOMAIN;

$httpClient = HttpClient::create([
    'headers' => ['X-AUTH-API' => $api_key, 'Referer' => $host],
]);

$response = $httpClient->request('GET', 'https://affwebgen.com/api', ['query' => $query_parameters,]);

?>
```


> Response:

```json
{
  "item": {
    "id": 2433,
    "name": "Keanu Reeves",
    "imageSrc": "https://m.media-amazon.com/images/M/MV5BNjUxNDcwMTg4Ml5BMl5BanBnXkFtZTcwMjU4NDYyOA@@._V1_UY317_CR15,0,214,317_AL_.jpg",
    "description": "Keanu Charles Reeves, whose first name means \"cool breeze over the mountains\" in Hawaiian, was born September 2, 1964 in Beirut, Lebanon. He is the son of Patricia Taylor, a showgirl and costume designer, and Samuel Nowlin Reeves, a geologist. Keanu's father was born in Hawaii, of British, Portuguese, Native Hawaiian, and Chinese ancestry, and ...",
    "birthYear": 1964,
    "birthMonth": 9,
    "birthDay": 2,
    "birthPlace": "Beirut, Lebanon",
    "deathYear": null,
    "deathMonth": null,
    "deathDay": null,
    "deathPlace": null,
    "otherTitles": [
      {
        "id": 204430,
        "name": "Episode dated 2 September 2014",
        "slug": "episode-dated-2-september-2014",
        "imageSrc": null
      }
    ]
  }
}

```

Working example with full configuration for person


