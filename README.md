#TidalAPI  [![Build Status](https://img.shields.io/travis/lucaslg26/TidalAPI.svg)](https://travis-ci.org/lucaslg26/TidalAPI) [![npm version](http://img.shields.io/npm/v/tidalapi.svg)](https://npmjs.org/package/tidalapi) [![npm downloads](https://img.shields.io/npm/dm/tidalapi.svg)](https://npmjs.org/package/tidalapi) [![NPM](https://img.shields.io/npm/l/tidalapi.svg)](https://github.com/lucaslg26/TidalAPI/blob/master/LICENSE.md) [![David](https://img.shields.io/david/lucaslg26/TidalAPI.svg)](https://david-dm.org/lucaslg26/TidalAPI)

## About

Node.js TIDAL API, use TIDAL Web API simply using this API ;)

Created by [Lucas Vasconcelos](https://github.com/lucaslg26)

**NOTE:** Currently not supporting facebook login.

## How to use
Run the following:

``` javascript
npm install tidalapi
```

Simple usage searching and querying a track list

```javascript
var TidalAPI = require('tidalapi');

var api = new TidalAPI({
    username: '',
    password: '',
    token: '_KM2HixcUBZtmktH',
    quality: 'LOSSLESS'
});

api.search({type: 'artists', query: 'Dream Theater', limit: 1}, function(data){
  console.log(data.artists);
})

api.search({type: 'albums', query: 'Dream Theater', limit: 1}, function(data){
  console.log(data.albums);
})

api.search({type: 'tracks', query: 'Dream Theater', limit: 1}, function(data){
  console.log(data.tracks);
})

api.search({type: 'tracks,albums,artists', query: 'Dream Theater', limit: 1}, function(data){
  console.log(data.tracks);
  console.log(data.albums);
  console.log(data.artists);
})

api.getTrackInfo({id: 22560696 }, function(data){
  console.log(data)
})

api.getStreamURL({id: 22560696}, function(data){
  console.log(data)
})

api.getVideoStreamURL({id: 25470315}, function(data){
  console.log(data)
})

console.log(api.getArtURL('24f52ab0-e7d6-414d-a650-20a4c686aa57', 1280)) //coverid

api.getArtistVideos({id: 14670, limit: 2}, function(data){
  console.log(data)
})

api.genMetaflacTags({id: 22560696, coverPath: './albumart.jpg', songPath: './song.flac'}, function(data){
  console.log(data)
  /* --remove-all-tags --set-tag="ARTIST=Dream Theater" --set-tag="TITLE=Along For The Ride" --set-tag="ALBUM=Dream Theater" --set-tag="TRACKNUMBER=8" --set-tag="COPYRIGHT=2013 Roadrunner Records, Inc." -set-tag="DATE=2013" --import-picture-from="./albumart.jpg" "./song.flac" --add-replay-gain */

})

```
