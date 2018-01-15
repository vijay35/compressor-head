# Compressor Head

Compressor Head is a web application for compressing/scaling an image before downloading it.
It is built on [Python](https://www.python.org) and hosted on the [Google App Engine](https://cloud.google.com/appengine).

## Why Compressor Head?

Compressor Head compresses images to the desired resolution before passing these images back to the user to download. This saves data and storage resources. So this has a twin benefit.

Running on the Google App Engine, the image conversion is nearly instantaneous. The usage of the Memcache library also speeds up the conversion process if the same image had been retrieved before.

## Contents
* [Usage](#usage)
* [Usage example](#usage_exm)
* [Working with the project](#work)
* [API reference](#ref)
* [Set up *Compressor-head* in Google Cloud Platform](#google_cloud)
* [Author](#author)
* [Contact us](#gitter)
* [Copyright](#copyright)

### <a id="usage"></a>Usage

*URL* - 
```http://compressor-head.appspot.com/image/?image_url=[IMAGE_URL]&width=[WIDTH]&height=[HEIGHT]&format=[FORMAT]```

Where
```
*IMAGE_URL* is the URL of the image to be compressed.
*WIDTH* is the desired width.
*HEIGHT* is the desired height.
*FORMAT* is the desired image format (Supported formats - JPEG, PNG and WEBP).
```

Both WIDTH and HEIGHT should be integers greater than or equal to 0:
 * If *both are 0*, the image will not be scaled.
 * If *one of the two is 0*, it will scale that non-zero dimension and the other dimension will be scaled such that the aspect ratio remains the same.
 * If *both are greater than 0*, both the width and height will scale so, which may change the aspect ratio of the image.

### <a id="usage_exm"></a>Usage example

Sample Image URL - http://compressor-head.appspot.com/image
This is a `5.8 MB JPEG` image, with dimensions of `5649×3684`
![](http://compressor-head.appspot.com/image)

To resize the image -
- Resize (Width) : `http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=0&format=jpeg`
Note: This retains the aspect ratio of the image, and the height is scaled so.

![](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=0&format=jpeg)

This returns an image `37 KB JPEG` image with dimensions `500x326`

- Resize (Height) : `http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=0&height=250&format=png`
Note: This retains the aspect ratio of the image, and the width is scaled so.

![](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=0&height=250&format=png)

This returns an image `164 KB PNG` image with dimensions `383x250`

- Resize (Width & Height) : `http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=350&format=jpeg`
Note: This may change the aspect ratio of the image.

![](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=350&format=jpeg)

This returns an image `41 KB JPEG` image with dimensions `500x350`

**Note:** You can also use the `WEBP` format, but it's not shown as an example as GitHub does not make WEBPs. A sample WEBP conversion of this conversion could be found [here](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=350&format=webp).

### <a id="work"></a> Working with the project

If you'd like to get more hands-on with the project, check out the following documentation:
 * [Setting up the project](doc/SETUP.md)
 * [Contributing to the project](doc/CONTRIBUTING.md)

### <a id="ref"></a>API reference

 * [Google App Engine (Python): Images API](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.images.html)
 * [Google App Engine (Python): Memcache API](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.memcache.html)
 * [Google App Engine (Python): URL downloading API](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.urlfetch.html)
 * [Vinay Sajip: logging](http://www.red-dove.com/python_logging.html)
 * [The Webapp2 Maintainers: webapp2](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.images.html)

### <a id="google_cloud"></a>Set up *Compressor-head* in Google Cloud Platform
#### Steps to follow
1.Before starting with steps you must have installed the lastest version of Python.
2.For installing Python go to www.python.org and install it for your operating system.

1. **Sign up** or **log in** to the [Google Cloud Platform Console](https://console.cloud.google.com). ***(important)***

2. Create a new project on it.

    ![](https://image.ibb.co/bNyAu6/my_proj.png)
    ![](https://image.ibb.co/eZ6wZ6/add_proj.png)
3. In the upper left corner, click on the three perpendicular lines![](https://image.ibb.co/fZH3E6/three_perp.png), and then select API Manager.
4. In the Google Cloud APIs section, select Compute Engine API. 

![](https://image.ibb.co/iuxg1m/cloud_apis.png)

###### Click the Enable button.

Install and start the Google Cloud SDK on your local machine's platform by referring the Before you Begin and initialize the SDK sections with one of the following links below:
##### Instructions for 
[Windows](https://cloud.google.com/sdk/docs/quickstart-windows)

[Mac OS X](https://cloud.google.com/sdk/docs/quickstart-mac-os-x)

[Linux](https://cloud.google.com/sdk/docs/quickstart-linux)

[Debian and Ubuntu](https://cloud.google.com/sdk/docs/quickstart-debian-ubuntu)

### <a id="author"></a>Author

[@m-murad](https://github.com/m-murad)

#### <a id="gitter"></a>For any queries, [chat with us here](https://gitter.im/jboss-outreach)

## <a id="copyright"></a>Copyright

    Copyright 2017 Murad. All rights reserved.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may get a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
