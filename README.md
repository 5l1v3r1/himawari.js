<a href="https://github.com/jakiestfu/himawari.js">
  <img src="http://i.imgur.com/MUefuXm.png">
</a>


## Getting Started

```sh
brew install imagemagick
brew install graphicsmagick
npm i himawari
```

## Usage
```javascript
var himawari = require('himawari');

himawari({

  /**
   * The zoom level of the image. Can be 1-5 (default: 1)
   * Each zoom level requires more images to be downloaded and therefore stitched
   * together. Higher zoom yields a higher resolution image.
   * @type {Number}
   */
  zoom: 1,

  /**
   * The time of the picture desired. If you want to get the latest image, use 'latest'
   * @type {String|Date}
   */
  date: 'latest', // Or new Date() or a date string

  /**
   * If set to true, an image on the infrared light spectrum will be generated
   * @type {Boolean}
   */
  infrared: false,

  /**
   * The location to save the resulting image
   * @type {String}
   */
  outfile: '/path/to/output/earth.jpg',

  /**
   * Skip empty images from being saved
   * @type {Boolean}
   */
  skipEmpty: true,

  /**
   * A success callback if the image downloads successfully
   * @type {Function}
   */
  success: function () { process.exit(); },

  /**
   * A callback if the image cannot be downloaded or saved
   * @type {Function}
   * @param  {Object} err An error object or information surrounding the issue
   */
  error: function (err) { console.log(err); },

  /**
   * A callback that is fired every time a tile has been downloaded.
   * @param  {Object} info Information about the download such as filepath, part, and total images
   */
  chunk: function (info) {
    console.log(info.outfile + ': ' + info.part + '/' + info.total);
  }
});

```

### Command Line Interface

There is also a command-line interface available if you install it with `-g`.

```sh
npm i -g himawari
```

This installs a program called `himawari` that can be used like so:

```sh
Usage: himawari [options]
    --zoom, -z            The zoom level of the image. Can be 1-5. (Default: `1`)
    --date, -d            The time of the picture desired. If you want to get the latest image, use 'latest'. (Default: `"latest"`)
    --debug, -l           Turns on logging. (Default: `false`)
    --outfile, -o         The location to save the resulting image. (Default: `"himawari-{date}.jpg"` in current directory)
    --skipempty, -s       Skip saving images that contain no useful information (i.e. "No Image") (Default: `true`)
    --infrared, -i        Capture picture on the infrared spectrum (Default: `false`)
    --help, -h            Show help
```

### Acknowledgement
[Michael Pote](https://github.com/MichaelPote) created a [Powershell Script](https://gist.github.com/MichaelPote/92fa6e65eacf26219022) that inspired this library.

### Example Images
<img src="http://i.imgur.com/kJcfCoN.jpg">
<img src="http://i.imgur.com/376ZTvB.jpg" width="50%"><img src="http://i.imgur.com/XnAAjzy.jpg" width="50%">

## License
MIT
