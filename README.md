GeoRaptor: Nodejs Geohash Compression Tool
==========================================

Geohash is a geocoding system invented by Gustavo Niemeyer and placed into the public domain. It is a hierarchical spatial data structure which subdivides space into buckets of grid shape, which is one of the many applications of what is known as a Z-order curve, and generally space-filling curves.

Geohash creation for a polygon at a given precision level could result in a huge set of geohashes.

GeoRaptor creates the best combination of geohashes across various levels to represent a polygon, by starting from the highest level and iterating till the optimal blend is brewed. Result accuracy remains the same as that of the starting geohash level, but data size reduces considerably for large polygons, thereby improving speed and performance.

Following is a sample of what georaptor does

.. image:: https://camo.githubusercontent.com/98016233c7ec25431c346d09043d61ca52b83803/68747470733a2f2f7261772e6769746875622e636f6d2f61736877696e3731312f67656f726170746f722f6d61737465722f696d616765732f7367705f696e7075742e706e67
   :width: 480
   :height: 320
.. image:: https://camo.githubusercontent.com/5136f17d38158fff6a14f26a39ca70b31fb93a37/68747470733a2f2f7261772e6769746875622e636f6d2f61736877696e3731312f67656f726170746f722f6d61737465722f696d616765732f7367705f6f75747075742e706e67
   :width: 480
   :height: 320

*Input:* 1096 geohashes at precision 6 for Singapore.

*Output:* 414 geohashes with a mix of precision 5 and 6.

## Credits

    https://github.com/ashwin711/georaptor

## Installation

```bash
npm install georaptor
```


### API


```js
var georaptor = require('georaptor');

let compressedHashes = georaptor.compress(new Set(["tdr1qr9","tdr1qr9","tdr1qz8","tdr1qz8","tdr1qr9","tdr1qr9","tdr1qz8","tdr1qz8","tdr1qr8","tdr1qr8","tdr1qz9","tdr1qz9","tdr1qr8","tdr1qr8","tdr1qz9","tdr1qz9","tdr1qpx","tdr1qpx","tdr1qzd","tdr1qzd","tdr1qpx","tdr1qpx","tdr1qzd","tdr1qzd","tdr1qpw","tdr1qpw","tdr1qze","tdr1qze","tdr1qpw","tdr1qpw","tdr1qze","tdr1qze","tdr1qpt","tdr1qpt","tdr1qzs","tdr1qzs","tdr1qpt","tdr1qpt","tdr1qzs","tdr1qzs","tdr1qps","tdr1qps","tdr1qzt","tdr1qzt","tdr1qps","tdr1qps","tdr1qzt","tdr1qzt","tdr1qpe","tdr1qpe","tdr1qzw","tdr1qzw","tdr1qpe","tdr1qpe","tdr1qxb","tdr1qx2","tdr1qxb","tdr1qx2","tdr1qxc","tdr1qx3","tdr1qrz","tdr1qrr","tdr1qxc","tdr1qx3","tdr1qrz","tdr1qrr","tdr1qxf","tdr1qx6","tdr1qry","tdr1qrq","tdr1qxf","tdr1qx6","tdr1qry","tdr1qrq","tdr1qxg","tdr1qx7","tdr1qrv","tdr1qrm","tdr1qxg","tdr1qx7","tdr1qrv","tdr1qrm","tdr1qxu","tdr1qxk","tdr1qru","tdr1qrk","tdr1qxu","tdr1qxk","tdr1qru","tdr1qrk","tdr1qxv","tdr1qxm","tdr1qrg","tdr1qr7","tdr1qxy","tdr1qxq","tdr1qrg","tdr1qr7","tdr1qxy","tdr1qxq","tdr1qrf","tdr1qr6","tdr1qxz","tdr1qxr","tdr1qrf","tdr1qr6","tdr1qxz","tdr1qxr","tdr1qrc","tdr1qr3","tdr1qzb","tdr1qz2","tdr1qrc","tdr1qr3","tdr1qzb","tdr1qz2","tdr1qrb","tdr1qr2","tdr1qzc","tdr1qz3","tdr1qrb","tdr1qr2","tdr1qzc","tdr1qz3","tdr1qpz","tdr1qpr","tdr1qzf","tdr1qz6","tdr1qpz","tdr1qpr","tdr1qzf","tdr1qz6","tdr1qpy","tdr1qpq","tdr1qzg","tdr1qz7","tdr1qpy","tdr1qpq","tdr1qzg","tdr1qz7","tdr1qpv","tdr1qpm","tdr1qzu","tdr1qzk","tdr1qpv","tdr1qpm","tdr1qzu","tdr1qzk","tdr1qpu","tdr1qpk","tdr1qzv","tdr1qzm","tdr1qpu","tdr1qpk","tdr1qzv","tdr1qzm","tdr1qpg","tdr1qp7","tdr1qzy","tdr1qzq","tdr1qpg","tdr1qp7","tdr1qxb","tdr1qx2","tdr1qxb","tdr1qx2","tdr1qxc","tdr1qx3","tdr1qrz","tdr1qrr","tdr1qxc","tdr1qx3","tdr1qrz","tdr1qrr","tdr1qxf","tdr1qx6","tdr1qry","tdr1qrq","tdr1qxf","tdr1qx6","tdr1qry","tdr1qrq","tdr1qxg","tdr1qx7","tdr1qrv","tdr1qrm","tdr1qxg","tdr1qx7","tdr1qrv","tdr1qrm","tdr1qxu","tdr1qxk","tdr1qru","tdr1qrk","tdr1qxu","tdr1qxk","tdr1qru","tdr1qrk","tdr1qxv","tdr1qxm","tdr1qrg","tdr1qr7","tdr1qxy","tdr1qxq","tdr1qrg","tdr1qr7","tdr1qxy","tdr1qxq","tdr1qrf","tdr1qr6","tdr1qxz","tdr1qxr","tdr1qrf","tdr1qr6","tdr1qxz","tdr1qxr","tdr1qrc","tdr1qr3","tdr1qzb","tdr1qz2","tdr1qrc","tdr1qr3","tdr1qzb","tdr1qz2","tdr1qrb","tdr1qr2","tdr1qzc","tdr1qz3","tdr1qrb","tdr1qr2","tdr1qzc","tdr1qz3","tdr1qpz","tdr1qpr","tdr1qzf","tdr1qz6","tdr1qpz","tdr1qpr","tdr1qzf","tdr1qz6","tdr1qpy","tdr1qpq","tdr1qzg","tdr1qz7","tdr1qpy","tdr1qpq","tdr1qzg","tdr1qz7","tdr1qpv","tdr1qpm","tdr1qzu","tdr1qzk","tdr1qpv","tdr1qpm","tdr1qzu","tdr1qzk","tdr1qpu","tdr1qpk","tdr1qzv","tdr1qzm","tdr1qpu","tdr1qpk","tdr1qzv","tdr1qzm","tdr1qpg","tdr1qp7","tdr1qzy","tdr1qzq","tdr1qpg","tdr1qp7","tdr1w80","tdr1qx0","tdr1w80","tdr1qx0","tdr1w81","tdr1qx1","tdr1w2p","tdr1qrp","tdr1w81","tdr1qx1","tdr1w2p","tdr1qrp","tdr1w84","tdr1qx4","tdr1w2n","tdr1qrn","tdr1w84","tdr1qx4","tdr1w2n","tdr1qrn","tdr1w85","tdr1qx5","tdr1w2j","tdr1qrj","tdr1w85","tdr1qx5","tdr1w2j","tdr1qrj","tdr1w8h","tdr1qxh","tdr1w2h","tdr1qrh","tdr1w8h","tdr1qxh","tdr1w2h","tdr1qrh","tdr1w8j","tdr1qxj","tdr1w25","tdr1qr5","tdr1w8n","tdr1qxn","tdr1w25","tdr1qr5","tdr1w8n","tdr1qxn","tdr1w24","tdr1qr4","tdr1w8p","tdr1qxp","tdr1w24","tdr1qr4","tdr1w8p","tdr1qxp","tdr1w21","tdr1qr1","tdr1wb0","tdr1qz0","tdr1w21","tdr1qr1","tdr1wb0","tdr1qz0","tdr1w20","tdr1qr0","tdr1wb1","tdr1qz1","tdr1w20","tdr1qr0","tdr1wb1","tdr1qz1","tdr1w0p","tdr1qpp","tdr1wb4","tdr1qz4","tdr1w0p","tdr1qpp","tdr1wb4","tdr1qz4","tdr1w0n","tdr1qpn","tdr1wb5","tdr1qz5","tdr1w0n","tdr1qpn","tdr1wb5","tdr1qz5","tdr1w0j","tdr1qpj","tdr1wbh","tdr1qzh","tdr1w0j","tdr1qpj","tdr1wbh","tdr1qzh","tdr1w0h","tdr1qph","tdr1wbj","tdr1qzj","tdr1w0h","tdr1qph","tdr1wbj","tdr1qzj","tdr1w05","tdr1qp5","tdr1w80","tdr1qx0","tdr1w80","tdr1qx0","tdr1w81","tdr1qx1","tdr1w2p","tdr1qrp","tdr1w81","tdr1qx1","tdr1w2p","tdr1qrp","tdr1w84","tdr1qx4","tdr1w2n","tdr1qrn","tdr1w84","tdr1qx4","tdr1w2n","tdr1qrn","tdr1w85","tdr1qx5","tdr1w2j","tdr1qrj","tdr1w85","tdr1qx5","tdr1w2j","tdr1qrj","tdr1w8h","tdr1qxh","tdr1w2h","tdr1qrh","tdr1w8h","tdr1qxh","tdr1w2h","tdr1qrh","tdr1w8j","tdr1qxj","tdr1w25","tdr1qr5","tdr1w8n","tdr1qxn","tdr1w25","tdr1qr5","tdr1w8n","tdr1qxn","tdr1w24","tdr1qr4","tdr1w8p","tdr1qxp","tdr1w24","tdr1qr4","tdr1w8p","tdr1qxp","tdr1w21","tdr1qr1","tdr1wb0","tdr1qz0","tdr1w21","tdr1qr1","tdr1wb0","tdr1qz0","tdr1w20","tdr1qr0","tdr1wb1","tdr1qz1","tdr1w20","tdr1qr0","tdr1wb1","tdr1qz1","tdr1w0p","tdr1qpp","tdr1wb4","tdr1qz4","tdr1w0p","tdr1qpp","tdr1wb4","tdr1qz4","tdr1w0n","tdr1qpn","tdr1wb5","tdr1qz5","tdr1w0n","tdr1qpn","tdr1wb5","tdr1qz5","tdr1w0j","tdr1qpj","tdr1wbh","tdr1qzh","tdr1w0j","tdr1qpj","tdr1wbh","tdr1qzh","tdr1w0h","tdr1qph","tdr1wbj","tdr1qzj","tdr1w0h","tdr1qph","tdr1wbj","tdr1qzj","tdr1w05","tdr1qp5","tdr1w82","tdr1qwb","tdr1w82","tdr1qwb","tdr1w83","tdr1qwc","tdr1w2r","tdr1qqz","tdr1w83","tdr1qwc","tdr1w2r","tdr1qqz","tdr1w86","tdr1qwf","tdr1w2q","tdr1qqy","tdr1w86","tdr1qwf","tdr1w2q","tdr1qqy","tdr1w87","tdr1qwg","tdr1w2m","tdr1qqv","tdr1w87","tdr1qwg","tdr1w2m","tdr1qqv","tdr1w8k","tdr1qwu","tdr1w2k","tdr1qqu","tdr1w8k","tdr1qwu","tdr1w2k","tdr1qqu","tdr1w8m","tdr1qwv","tdr1w27","tdr1qqg","tdr1w8q","tdr1qwy","tdr1w27","tdr1qqg","tdr1w8q","tdr1qwy","tdr1w26","tdr1qqf","tdr1w8r","tdr1qwz","tdr1w26","tdr1qqf","tdr1w8r","tdr1qwz","tdr1w23","tdr1qqc","tdr1wb2","tdr1qyb","tdr1w23","tdr1qqc","tdr1wb2","tdr1qyb","tdr1w22","tdr1qqb","tdr1wb3","tdr1qyc","tdr1w22","tdr1qqb","tdr1wb3","tdr1qyc","tdr1w0r","tdr1qnz","tdr1wb6","tdr1qyf","tdr1w0r","tdr1qnz","tdr1wb6","tdr1qyf","tdr1w0q","tdr1qny","tdr1wb7","tdr1qyg","tdr1w0q","tdr1qny","tdr1wb7","tdr1qyg","tdr1w0m","tdr1qnv","tdr1wbk","tdr1qyu","tdr1w0m","tdr1qnv","tdr1wbk","tdr1qyu","tdr1w0k","tdr1qnu","tdr1wbm","tdr1qyv","tdr1w0k","tdr1qnu","tdr1wbm","tdr1qyv","tdr1w07","tdr1qng","tdr1w82","tdr1qwb","tdr1w82","tdr1qwb","tdr1w83","tdr1qwc","tdr1w2r","tdr1qqz","tdr1w83","tdr1qwc","tdr1w2r","tdr1qqz","tdr1w86","tdr1qwf","tdr1w2q","tdr1qqy","tdr1w86","tdr1qwf","tdr1w2q","tdr1qqy","tdr1w87","tdr1qwg","tdr1w2m","tdr1qqv","tdr1w87","tdr1qwg","tdr1w2m","tdr1qqv","tdr1w8k","tdr1qwu","tdr1w2k","tdr1qqu","tdr1w8k","tdr1qwu","tdr1w2k","tdr1qqu","tdr1w8m","tdr1qwv","tdr1w27","tdr1qqg","tdr1w8q","tdr1qwy","tdr1w27","tdr1qqg","tdr1w8q","tdr1qwy","tdr1w26","tdr1qqf","tdr1w8r","tdr1qwz","tdr1w26","tdr1qqf","tdr1w8r","tdr1qwz","tdr1w23","tdr1qqc","tdr1wb2","tdr1qyb","tdr1w23","tdr1qqc","tdr1wb2","tdr1qyb","tdr1w22","tdr1qqb","tdr1wb3","tdr1qyc","tdr1w22","tdr1qqb","tdr1wb3","tdr1qyc","tdr1w0r","tdr1qnz","tdr1wb6","tdr1qyf","tdr1w0r","tdr1qnz","tdr1wb6","tdr1qyf","tdr1w0q","tdr1qny","tdr1wb7","tdr1qyg","tdr1w0q","tdr1qny","tdr1wb7","tdr1qyg","tdr1w0m","tdr1qnv","tdr1wbk","tdr1qyu","tdr1w0m","tdr1qnv","tdr1wbk","tdr1qyu","tdr1w0k","tdr1qnu","tdr1wbm","tdr1qyv","tdr1w0k","tdr1qnu","tdr1wbm","tdr1qyv","tdr1w07","tdr1qng","tdr1w88","tdr1qw8","tdr1w88","tdr1qw8","tdr1w89","tdr1qw9","tdr1w2x","tdr1qqx","tdr1w89","tdr1qw9","tdr1w2x","tdr1qqx","tdr1w8d","tdr1qwd","tdr1w2w","tdr1qqw","tdr1w8d","tdr1qwd","tdr1w2w","tdr1qqw","tdr1w8e","tdr1qwe","tdr1w2t","tdr1qqt","tdr1w8e","tdr1qwe","tdr1w2t","tdr1qqt","tdr1w8s","tdr1qws","tdr1w2s","tdr1qqs","tdr1w8s","tdr1qws","tdr1w2s","tdr1qqs","tdr1w8t","tdr1qwt","tdr1w2e","tdr1qqe","tdr1w8w","tdr1qww","tdr1w2e","tdr1qqe","tdr1w8w","tdr1qww","tdr1w2d","tdr1qqd","tdr1w8x","tdr1qwx","tdr1w2d","tdr1qqd","tdr1w8x","tdr1qwx","tdr1w29","tdr1qq9","tdr1wb8","tdr1qy8","tdr1w29","tdr1qq9","tdr1wb8","tdr1qy8","tdr1w28","tdr1qq8","tdr1wb9","tdr1qy9","tdr1w28","tdr1qq8","tdr1wb9","tdr1qy9","tdr1w0x","tdr1qnx","tdr1wbd","tdr1qyd","tdr1w0x","tdr1qnx","tdr1wbd","tdr1qyd","tdr1w0w","tdr1qnw","tdr1wbe","tdr1qye","tdr1w0w","tdr1qnw","tdr1wbe","tdr1qye","tdr1w0t","tdr1qnt","tdr1wbs","tdr1qys","tdr1w0t","tdr1qnt","tdr1wbs","tdr1qys","tdr1w0s","tdr1qns","tdr1wbt","tdr1qyt","tdr1w0s","tdr1qns","tdr1wbt","tdr1qyt","tdr1w0e","tdr1qne","tdr1w88","tdr1qw8","tdr1w88","tdr1qw8","tdr1w89","tdr1qw9","tdr1w2x","tdr1qqx","tdr1w89","tdr1qw9","tdr1w2x","tdr1qqx","tdr1w8d","tdr1qwd","tdr1w2w","tdr1qqw","tdr1w8d","tdr1qwd","tdr1w2w","tdr1qqw","tdr1w8e","tdr1qwe","tdr1w2t","tdr1qqt","tdr1w8e","tdr1qwe","tdr1w2t","tdr1qqt","tdr1w8s","tdr1qws","tdr1w2s","tdr1qqs","tdr1w8s","tdr1qws","tdr1w2s","tdr1qqs","tdr1w8t","tdr1qwt","tdr1w2e","tdr1qqe","tdr1w8w","tdr1qww","tdr1w2e","tdr1qqe","tdr1w8w","tdr1qww","tdr1w2d","tdr1qqd","tdr1w8x","tdr1qwx","tdr1w2d","tdr1qqd","tdr1w8x","tdr1qwx","tdr1w29","tdr1qq9","tdr1wb8","tdr1qy8","tdr1w29","tdr1qq9","tdr1wb8","tdr1qy8","tdr1w28","tdr1qq8","tdr1wb9","tdr1qy9","tdr1w28","tdr1qq8","tdr1wb9","tdr1qy9","tdr1w0x","tdr1qnx","tdr1wbd","tdr1qyd","tdr1w0x","tdr1qnx","tdr1wbd","tdr1qyd","tdr1w0w","tdr1qnw","tdr1wbe","tdr1qye","tdr1w0w","tdr1qnw","tdr1wbe","tdr1qye","tdr1w0t","tdr1qnt","tdr1wbs","tdr1qys","tdr1w0t","tdr1qnt","tdr1wbs","tdr1qys","tdr1w0s","tdr1qns","tdr1wbt","tdr1qyt","tdr1w0s","tdr1qns","tdr1w8b","tdr1qw2","tdr1w8b","tdr1qw2","tdr1w8c","tdr1qw3","tdr1w2z","tdr1qqr","tdr1w8c","tdr1qw3","tdr1w2z","tdr1qqr","tdr1w8f","tdr1qw6","tdr1w2y","tdr1qqq","tdr1w8f","tdr1qw6","tdr1w2y","tdr1qqq","tdr1w8g","tdr1qw7","tdr1w2v","tdr1qqm","tdr1w8g","tdr1qw7","tdr1w2v","tdr1qqm","tdr1w8u","tdr1qwk","tdr1w2u","tdr1qqk","tdr1w8u","tdr1qwk","tdr1w2u","tdr1qqk","tdr1w8v","tdr1qwm","tdr1w2g","tdr1qq7","tdr1w8y","tdr1qwq","tdr1w2g","tdr1qq7","tdr1w8y","tdr1qwq","tdr1w2f","tdr1qq6","tdr1w8z","tdr1qwr","tdr1w2f","tdr1qq6","tdr1w8z","tdr1qwr","tdr1w2c","tdr1qq3","tdr1wbb","tdr1qy2","tdr1w2c","tdr1qq3","tdr1wbb","tdr1qy2","tdr1w2b","tdr1qq2","tdr1wbc","tdr1qy3","tdr1w2b","tdr1qq2","tdr1wbc","tdr1qy3","tdr1w0z","tdr1qnr","tdr1wbf","tdr1qy6","tdr1w0z","tdr1qnr","tdr1wbf","tdr1qy6","tdr1w0y","tdr1qnq","tdr1wbg","tdr1qy7","tdr1w0y","tdr1qnq","tdr1wbg","tdr1qy7","tdr1w0v","tdr1qnm","tdr1wbu","tdr1qyk","tdr1w0v","tdr1qnm","tdr1wbu","tdr1qyk","tdr1w0u","tdr1qnk","tdr1wbv","tdr1qym","tdr1w0u","tdr1qnk","tdr1w8b","tdr1qw2","tdr1w8b","tdr1qw2","tdr1w8c","tdr1qw3","tdr1w2z","tdr1qqr","tdr1w8c","tdr1qw3","tdr1w2z","tdr1qqr","tdr1w8f","tdr1qw6","tdr1w2y","tdr1qqq","tdr1w8f","tdr1qw6","tdr1w2y","tdr1qqq","tdr1w8g","tdr1qw7","tdr1w2v","tdr1qqm","tdr1w8g","tdr1qw7","tdr1w2v","tdr1qqm","tdr1w8u","tdr1qwk","tdr1w2u","tdr1qqk","tdr1w8u","tdr1qwk","tdr1w2u","tdr1qqk","tdr1w8v","tdr1qwm","tdr1w2g","tdr1qq7","tdr1w8y","tdr1qwq","tdr1w2g","tdr1qq7","tdr1w8y","tdr1qwq","tdr1w2f","tdr1qq6","tdr1w8z","tdr1qwr","tdr1w2f","tdr1qq6","tdr1w8z","tdr1qwr","tdr1w2c","tdr1qq3","tdr1wbb","tdr1qy2","tdr1w2c","tdr1qq3","tdr1wbb","tdr1qy2","tdr1w2b","tdr1qq2","tdr1wbc","tdr1qy3","tdr1w2b","tdr1qq2","tdr1wbc","tdr1qy3","tdr1w0z","tdr1qnr","tdr1wbf","tdr1qy6","tdr1w0z","tdr1qnr","tdr1wbf","tdr1qy6","tdr1w0y","tdr1qnq","tdr1wbg","tdr1qy7","tdr1w0y","tdr1qnq","tdr1wbg","tdr1qy7","tdr1w0v","tdr1qnm","tdr1wbu","tdr1qyk","tdr1w0v","tdr1qnm","tdr1wbu","tdr1qyk","tdr1w0u","tdr1qnk","tdr1wbv","tdr1qym","tdr1w0u","tdr1qnk","tdr1w90","tdr1qw0","tdr1w90","tdr1qw0","tdr1w91","tdr1qw1","tdr1w3p","tdr1qqp","tdr1w91","tdr1qw1","tdr1w3p","tdr1qqp","tdr1w94","tdr1qw4","tdr1w3n","tdr1qqn","tdr1w94","tdr1qw4","tdr1w3n","tdr1qqn","tdr1w95","tdr1qw5","tdr1w3j","tdr1qqj","tdr1w95","tdr1qw5","tdr1w3j","tdr1qqj","tdr1w9h","tdr1qwh","tdr1w3h","tdr1qqh","tdr1w9h","tdr1qwh","tdr1w3h","tdr1qqh","tdr1w9j","tdr1qwj","tdr1w35","tdr1qq5","tdr1w9n","tdr1qwn","tdr1w35","tdr1qq5","tdr1w9n","tdr1qwn","tdr1w34","tdr1qq4","tdr1w9p","tdr1qwp","tdr1w34","tdr1qq4","tdr1w9p","tdr1qwp","tdr1w31","tdr1qq1","tdr1wc0","tdr1qy0","tdr1w31","tdr1qq1","tdr1wc0","tdr1qy0","tdr1w30","tdr1qq0","tdr1wc1","tdr1qy1","tdr1w30","tdr1qq0","tdr1wc1","tdr1qy1","tdr1w1p","tdr1qnp","tdr1wc4","tdr1qy4","tdr1w1p","tdr1qnp","tdr1wc4","tdr1qy4","tdr1w1n","tdr1qnn","tdr1wc5","tdr1qy5","tdr1w1n","tdr1qnn","tdr1wc5","tdr1qy5","tdr1w1j","tdr1qnj","tdr1wch","tdr1qyh","tdr1w1j","tdr1qnj","tdr1wch","tdr1qyh","tdr1w1h","tdr1qnh","tdr1w90","tdr1qw0","tdr1w90","tdr1qw0","tdr1w91","tdr1qw1","tdr1w3p","tdr1qqp","tdr1w91","tdr1qw1","tdr1w3p","tdr1qqp","tdr1w94","tdr1qw4","tdr1w3n","tdr1qqn","tdr1w94","tdr1qw4","tdr1w3n","tdr1qqn","tdr1w95","tdr1qw5","tdr1w3j","tdr1qqj","tdr1w95","tdr1qw5","tdr1w3j","tdr1qqj","tdr1w9h","tdr1qwh","tdr1w3h","tdr1qqh","tdr1w9h","tdr1qwh","tdr1w3h","tdr1qqh","tdr1w9j","tdr1qwj","tdr1w35","tdr1qq5","tdr1w9n","tdr1qwn","tdr1w35","tdr1qq5","tdr1w9n","tdr1qwn","tdr1w34","tdr1qq4","tdr1w9p","tdr1qwp","tdr1w34","tdr1qq4","tdr1w9p","tdr1qwp","tdr1w31","tdr1qq1","tdr1wc0","tdr1qy0","tdr1w31","tdr1qq1","tdr1wc0","tdr1qy0","tdr1w30","tdr1qq0","tdr1wc1","tdr1qy1","tdr1w30","tdr1qq0","tdr1wc1","tdr1qy1","tdr1w1p","tdr1qnp","tdr1wc4","tdr1qy4","tdr1w1p","tdr1qnp","tdr1wc4","tdr1qy4","tdr1w1n","tdr1qnn","tdr1wc5","tdr1qy5","tdr1w1n","tdr1qnn","tdr1wc5","tdr1qy5","tdr1w1j","tdr1qnj","tdr1wch","tdr1qyh","tdr1w1j","tdr1qnj","tdr1wch","tdr1qyh","tdr1w1h","tdr1qnh","tdr1w92","tdr1qtb","tdr1w92","tdr1qtb","tdr1w93","tdr1qtc","tdr1w3r","tdr1qmz","tdr1w93","tdr1qtc","tdr1w3r","tdr1qmz","tdr1w96","tdr1qtf","tdr1w3q","tdr1qmy","tdr1w96","tdr1qtf","tdr1w3q","tdr1qmy","tdr1w97","tdr1qtg","tdr1w3m","tdr1qmv","tdr1w97","tdr1qtg","tdr1w3m","tdr1qmv","tdr1w9k","tdr1qtu","tdr1w3k","tdr1qmu","tdr1w9k","tdr1qtu","tdr1w3k","tdr1qmu","tdr1w9m","tdr1qtv","tdr1w37","tdr1qmg","tdr1w9q","tdr1qty","tdr1w37","tdr1qmg","tdr1w9q","tdr1qty","tdr1w36","tdr1qmf","tdr1w9r","tdr1qtz","tdr1w36","tdr1qmf","tdr1w9r","tdr1qtz","tdr1w33","tdr1qmc","tdr1wc2","tdr1qvb","tdr1w33","tdr1qmc","tdr1wc2","tdr1qvb","tdr1w32","tdr1qmb","tdr1wc3","tdr1qvc","tdr1w32","tdr1qmb","tdr1wc3","tdr1qvc","tdr1w1r","tdr1qjz","tdr1wc6","tdr1qvf","tdr1w1r","tdr1qjz","tdr1wc6","tdr1qvf","tdr1w1q","tdr1qjy","tdr1wc7","tdr1qvg","tdr1w1q","tdr1qjy","tdr1wc7","tdr1qvg","tdr1w1m","tdr1qjv","tdr1wck","tdr1qvu","tdr1w1m","tdr1qjv","tdr1w92","tdr1qtb","tdr1w92","tdr1qtb","tdr1w93","tdr1qtc","tdr1w3r","tdr1qmz","tdr1w93","tdr1qtc","tdr1w3r","tdr1qmz","tdr1w96","tdr1qtf","tdr1w3q","tdr1qmy","tdr1w96","tdr1qtf","tdr1w3q","tdr1qmy","tdr1w97","tdr1qtg","tdr1w3m","tdr1qmv","tdr1w97","tdr1qtg","tdr1w3m","tdr1qmv","tdr1w9k","tdr1qtu","tdr1w3k","tdr1qmu","tdr1w9k","tdr1qtu","tdr1w3k","tdr1qmu","tdr1w9m","tdr1qtv","tdr1w37","tdr1qmg","tdr1w9q","tdr1qty","tdr1w37","tdr1qmg","tdr1w9q","tdr1qty","tdr1w36","tdr1qmf","tdr1w9r","tdr1qtz","tdr1w36","tdr1qmf","tdr1w9r","tdr1qtz","tdr1w33","tdr1qmc","tdr1wc2","tdr1qvb","tdr1w33","tdr1qmc","tdr1wc2","tdr1qvb","tdr1w32","tdr1qmb","tdr1wc3","tdr1qvc","tdr1w32","tdr1qmb","tdr1wc3","tdr1qvc","tdr1w1r","tdr1qjz","tdr1wc6","tdr1qvf","tdr1w1r","tdr1qjz","tdr1wc6","tdr1qvf","tdr1w1q","tdr1qjy","tdr1wc7","tdr1qvg","tdr1w1q","tdr1qjy","tdr1wc7","tdr1qvg","tdr1w1m","tdr1qjv","tdr1wck","tdr1qvu","tdr1w1m","tdr1qjv","tdr1w98","tdr1qt8","tdr1w98","tdr1qt8","tdr1w99","tdr1qt9","tdr1w3x","tdr1qmx","tdr1w99","tdr1qt9","tdr1w3x","tdr1qmx","tdr1w9d","tdr1qtd","tdr1w3w","tdr1qmw","tdr1w9d","tdr1qtd","tdr1w3w","tdr1qmw","tdr1w9e","tdr1qte","tdr1w3t","tdr1qmt","tdr1w9e","tdr1qte","tdr1w3t","tdr1qmt","tdr1w9s","tdr1qts","tdr1w3s","tdr1qms","tdr1w9s","tdr1qts","tdr1w3s","tdr1qms","tdr1w9t","tdr1qtt","tdr1w3e","tdr1qme","tdr1w9w","tdr1qtw","tdr1w3e","tdr1qme","tdr1w9w","tdr1qtw","tdr1w3d","tdr1qmd","tdr1w9x","tdr1qtx","tdr1w3d","tdr1qmd","tdr1w9x","tdr1qtx","tdr1w39","tdr1qm9","tdr1wc8","tdr1qv8","tdr1w39","tdr1qm9","tdr1wc8","tdr1qv8","tdr1w38","tdr1qm8","tdr1wc9","tdr1qv9","tdr1w38","tdr1qm8","tdr1wc9","tdr1qv9","tdr1w1x","tdr1qjx","tdr1wcd","tdr1qvd","tdr1w1x","tdr1qjx","tdr1wcd","tdr1qvd","tdr1w1w","tdr1qjw","tdr1wce","tdr1qve","tdr1w1w","tdr1qjw","tdr1wce","tdr1qve","tdr1w1t","tdr1qjt","tdr1w98","tdr1qt8","tdr1w98","tdr1qt8","tdr1w99","tdr1qt9","tdr1w3x","tdr1qmx","tdr1w99","tdr1qt9","tdr1w3x","tdr1qmx","tdr1w9d","tdr1qtd","tdr1w3w","tdr1qmw","tdr1w9d","tdr1qtd","tdr1w3w","tdr1qmw","tdr1w9e","tdr1qte","tdr1w3t","tdr1qmt","tdr1w9e","tdr1qte","tdr1w3t","tdr1qmt","tdr1w9s","tdr1qts","tdr1w3s","tdr1qms","tdr1w9s","tdr1qts","tdr1w3s","tdr1qms","tdr1w9t","tdr1qtt","tdr1w3e","tdr1qme","tdr1w9w","tdr1qtw","tdr1w3e","tdr1qme","tdr1w9w","tdr1qtw","tdr1w3d","tdr1qmd","tdr1w9x","tdr1qtx","tdr1w3d","tdr1qmd","tdr1w9x","tdr1qtx","tdr1w39","tdr1qm9","tdr1wc8","tdr1qv8","tdr1w39","tdr1qm9","tdr1wc8","tdr1qv8","tdr1w38","tdr1qm8","tdr1wc9","tdr1qv9","tdr1w38","tdr1qm8","tdr1wc9","tdr1qv9","tdr1w1x","tdr1qjx","tdr1wcd","tdr1qvd","tdr1w1x","tdr1qjx","tdr1wcd","tdr1qvd","tdr1w1w","tdr1qjw","tdr1wce","tdr1qve","tdr1w1w","tdr1qjw","tdr1w9b","tdr1qt2","tdr1w9b","tdr1qt2","tdr1w9c","tdr1qt3","tdr1w3z","tdr1qmr","tdr1w9c","tdr1qt3","tdr1w3z","tdr1qmr","tdr1w9f","tdr1qt6","tdr1w3y","tdr1qmq","tdr1w9f","tdr1qt6","tdr1w3y","tdr1qmq","tdr1w9g","tdr1qt7","tdr1w3v","tdr1qmm","tdr1w9g","tdr1qt7","tdr1w3v","tdr1qmm","tdr1w9u","tdr1qtk","tdr1w3u","tdr1qmk","tdr1w9u","tdr1qtk","tdr1w3u","tdr1qmk","tdr1w9v","tdr1qtm","tdr1w3g","tdr1qm7","tdr1w9y","tdr1qtq","tdr1w3g","tdr1qm7","tdr1w9y","tdr1qtq","tdr1w3f","tdr1qm6","tdr1w9z","tdr1qtr","tdr1w3f","tdr1qm6","tdr1w9z","tdr1qtr","tdr1w3c","tdr1qm3","tdr1wcb","tdr1qv2","tdr1w3c","tdr1qm3","tdr1wcb","tdr1qv2","tdr1w3b","tdr1qm2","tdr1wcc","tdr1qv3","tdr1w3b","tdr1qm2","tdr1wcc","tdr1qv3","tdr1w1z","tdr1qjr","tdr1wcf","tdr1qv6","tdr1w1z","tdr1qjr","tdr1wcf","tdr1qv6","tdr1w1y","tdr1qjq","tdr1w9b","tdr1qt2","tdr1w9b","tdr1qt2","tdr1w9c","tdr1qt3","tdr1w3z","tdr1qmr","tdr1w9c","tdr1qt3","tdr1w3z","tdr1qmr","tdr1w9f","tdr1qt6","tdr1w3y","tdr1qmq","tdr1w9f","tdr1qt6","tdr1w3y","tdr1qmq","tdr1w9g","tdr1qt7","tdr1w3v","tdr1qmm","tdr1w9g","tdr1qt7","tdr1w3v","tdr1qmm","tdr1w9u","tdr1qtk","tdr1w3u","tdr1qmk","tdr1w9u","tdr1qtk","tdr1w3u","tdr1qmk","tdr1w9v","tdr1qtm","tdr1w3g","tdr1qm7","tdr1w9y","tdr1qtq","tdr1w3g","tdr1qm7","tdr1w9y","tdr1qtq","tdr1w3f","tdr1qm6","tdr1w9z","tdr1qtr","tdr1w3f","tdr1qm6","tdr1w9z","tdr1qtr","tdr1w3c","tdr1qm3","tdr1wcb","tdr1qv2","tdr1w3c","tdr1qm3","tdr1wcb","tdr1qv2","tdr1w3b","tdr1qm2","tdr1wcc","tdr1qv3","tdr1w3b","tdr1qm2","tdr1wcc","tdr1qv3","tdr1w1z","tdr1qjr","tdr1wcf","tdr1qv6","tdr1w1z","tdr1qjr","tdr1wcf","tdr1qv6","tdr1w1y","tdr1qjq","tdr1wd0","tdr1qt0","tdr1wd0","tdr1qt0","tdr1wd1","tdr1qt1","tdr1w6p","tdr1qmp","tdr1wd1","tdr1qt1","tdr1w6p","tdr1qmp","tdr1wd4","tdr1qt4","tdr1w6n","tdr1qmn","tdr1wd4","tdr1qt4","tdr1w6n","tdr1qmn","tdr1wd5","tdr1qt5","tdr1w6j","tdr1qmj","tdr1wd5","tdr1qt5","tdr1w6j","tdr1qmj","tdr1wdh","tdr1qth","tdr1w6h","tdr1qmh","tdr1wdh","tdr1qth","tdr1w6h","tdr1qmh","tdr1wdj","tdr1qtj","tdr1w65","tdr1qm5","tdr1wdn","tdr1qtn","tdr1w65","tdr1qm5","tdr1wdn","tdr1qtn","tdr1w64","tdr1qm4","tdr1wdp","tdr1qtp","tdr1w64","tdr1qm4","tdr1wdp","tdr1qtp","tdr1w61","tdr1qm1","tdr1wf0","tdr1qv0","tdr1w61","tdr1qm1","tdr1wf0","tdr1qv0","tdr1w60","tdr1qm0","tdr1wf1","tdr1qv1","tdr1w60","tdr1qm0","tdr1wf1","tdr1qv1","tdr1w4p","tdr1qjp","tdr1wf4","tdr1qv4","tdr1w4p","tdr1qjp","tdr1wd0","tdr1qt0","tdr1wd0","tdr1qt0","tdr1wd1","tdr1qt1","tdr1w6p","tdr1qmp","tdr1wd1","tdr1qt1","tdr1w6p","tdr1qmp","tdr1wd4","tdr1qt4","tdr1w6n","tdr1qmn","tdr1wd4","tdr1qt4","tdr1w6n","tdr1qmn","tdr1wd5","tdr1qt5","tdr1w6j","tdr1qmj","tdr1wd5","tdr1qt5","tdr1w6j","tdr1qmj","tdr1wdh","tdr1qth","tdr1w6h","tdr1qmh","tdr1wdh","tdr1qth","tdr1w6h","tdr1qmh","tdr1wdj","tdr1qtj","tdr1w65","tdr1qm5","tdr1wdn","tdr1qtn","tdr1w65","tdr1qm5","tdr1wdn","tdr1qtn","tdr1w64","tdr1qm4","tdr1wdp","tdr1qtp","tdr1w64","tdr1qm4","tdr1wdp","tdr1qtp","tdr1w61","tdr1qm1","tdr1wf0","tdr1qv0","tdr1w61","tdr1qm1","tdr1wf0","tdr1qv0","tdr1w60","tdr1qm0","tdr1wf1","tdr1qv1","tdr1w60","tdr1qm0","tdr1wd2","tdr1qsb","tdr1wd2","tdr1qsb","tdr1wd3","tdr1qsc","tdr1w6r","tdr1qkz","tdr1wd3","tdr1qsc","tdr1w6r","tdr1qkz","tdr1wd6","tdr1qsf","tdr1w6q","tdr1qky","tdr1wd6","tdr1qsf","tdr1w6q","tdr1qky","tdr1wd7","tdr1qsg","tdr1w6m","tdr1qkv","tdr1wd7","tdr1qsg","tdr1w6m","tdr1qkv","tdr1wdk","tdr1qsu","tdr1w6k","tdr1qku","tdr1wdk","tdr1qsu","tdr1w6k","tdr1qku","tdr1wdm","tdr1qsv","tdr1w67","tdr1qkg","tdr1wdq","tdr1qsy","tdr1w67","tdr1qkg","tdr1wdq","tdr1qsy","tdr1w66","tdr1qkf","tdr1wdr","tdr1qsz","tdr1w66","tdr1qkf","tdr1wdr","tdr1qsz","tdr1w63","tdr1qkc","tdr1wf2","tdr1qub","tdr1w63","tdr1qkc","tdr1wf2","tdr1qub","tdr1w62","tdr1qkb","tdr1wd2","tdr1qsb","tdr1wd2","tdr1qsb","tdr1wd3","tdr1qsc","tdr1w6r","tdr1qkz","tdr1wd3","tdr1qsc","tdr1w6r","tdr1qkz","tdr1wd6","tdr1qsf","tdr1w6q","tdr1qky","tdr1wd6","tdr1qsf","tdr1w6q","tdr1qky","tdr1wd7","tdr1qsg","tdr1w6m","tdr1qkv","tdr1wd7","tdr1qsg","tdr1w6m","tdr1qkv","tdr1wdk","tdr1qsu","tdr1w6k","tdr1qku","tdr1wdk","tdr1qsu","tdr1w6k","tdr1qku","tdr1wdm","tdr1qsv","tdr1w67","tdr1qkg","tdr1wdq","tdr1qsy","tdr1w67","tdr1qkg","tdr1wdq","tdr1qsy","tdr1w66","tdr1qkf","tdr1wdr","tdr1qsz","tdr1w66","tdr1qkf","tdr1wdr","tdr1qsz","tdr1w63","tdr1qkc","tdr1wf2","tdr1qub","tdr1w63","tdr1qkc","tdr1wd8","tdr1qs8","tdr1wd8","tdr1qs8","tdr1wd9","tdr1qs9","tdr1w6x","tdr1qkx","tdr1wd9","tdr1qs9","tdr1w6x","tdr1qkx","tdr1wdd","tdr1qsd","tdr1w6w","tdr1qkw","tdr1wdd","tdr1qsd","tdr1w6w","tdr1qkw","tdr1wde","tdr1qse","tdr1w6t","tdr1qkt","tdr1wde","tdr1qse","tdr1w6t","tdr1qkt","tdr1wds","tdr1qss","tdr1w6s","tdr1qks","tdr1wds","tdr1qss","tdr1w6s","tdr1qks","tdr1wdt","tdr1qst","tdr1w6e","tdr1qke","tdr1wdw","tdr1qsw","tdr1w6e","tdr1qke","tdr1wdw","tdr1qsw","tdr1w6d","tdr1qkd","tdr1wdx","tdr1qsx","tdr1w6d","tdr1qkd","tdr1wd8","tdr1qs8","tdr1wd8","tdr1qs8","tdr1wd9","tdr1qs9","tdr1w6x","tdr1qkx","tdr1wd9","tdr1qs9","tdr1w6x","tdr1qkx","tdr1wdd","tdr1qsd","tdr1w6w","tdr1qkw","tdr1wdd","tdr1qsd","tdr1w6w","tdr1qkw","tdr1wde","tdr1qse","tdr1w6t","tdr1qkt","tdr1wde","tdr1qse","tdr1w6t","tdr1qkt","tdr1wds","tdr1qss","tdr1w6s","tdr1qks","tdr1wds","tdr1qss","tdr1w6s","tdr1qks"]),
1,12,false);

```