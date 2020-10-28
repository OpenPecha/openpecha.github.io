 Image API 3.0 — IIIF | International Image Interoperability Framework            

[Home](https://iiif.io/ "IIIF : International Image Interoperability Framework")

*   [About](https://iiif.io/about/)
*   [Technical Details](https://iiif.io/technical-details/)
*   [Apps & Demos](https://iiif.io/apps-demos/)
*   [Community](https://iiif.io/community/)
*   [Events](https://iiif.io/event/)
*   [News](https://iiif.io/news/)

IIIF Image API 3.0
==================

Status of this Document
-----------------------

**This Version:** 3.0.0

**Latest Stable Version:** [3.0.0](/api/image/3.0/ "Image API")

**Previous Version:** [2.1.1](/api/image/2.1/ "Image API 2.1")

**Editors:**

*   **[Michael Appleby](https://orcid.org/0000-0002-1266-298X)** [![ORCID iD](/img/orcid_16x16.png)](https://orcid.org/0000-0002-1266-298X), [_Yale University_](http://www.yale.edu/)
*   **[Tom Crane](https://orcid.org/0000-0003-1881-243X)** [![ORCID iD](/img/orcid_16x16.png)](https://orcid.org/0000-0003-1881-243X), [_Digirati_](http://digirati.com/)
*   **[Robert Sanderson](https://orcid.org/0000-0003-4441-6852)** [![ORCID iD](/img/orcid_16x16.png)](https://orcid.org/0000-0003-4441-6852), [_J. Paul Getty Trust_](http://www.getty.edu/)
*   **[Jon Stroop](https://orcid.org/0000-0002-0367-1243)** [![ORCID iD](/img/orcid_16x16.png)](https://orcid.org/0000-0002-0367-1243), [_Princeton University Library_](https://library.princeton.edu/)
*   **[Simeon Warner](https://orcid.org/0000-0002-7970-7855)** [![ORCID iD](/img/orcid_16x16.png)](https://orcid.org/0000-0002-7970-7855), [_Cornell University_](https://www.cornell.edu/)

_Copyright © 2012-2020 Editors and contributors. Published by the IIIF Consortium under the [CC-BY](http://creativecommons.org/licenses/by/4.0/ "Creative Commons — Attribution 4.0 International") license, see [disclaimer](/api/annex/notes/disclaimer/)._

* * *

Table of Contents
-----------------

*   [1\. Introduction](#1-introduction)
    *   [1.1. Audience and Scope](#11-audience-and-scope)
    *   [1.2. Terminology](#12-terminology)
*   [2\. URI Syntax](#2-uri-syntax)
    *   [2.1. Image Request URI Syntax](#21-image-request-uri-syntax)
    *   [2.2. Image Information Request URI Syntax](#22-image-information-request-uri-syntax)
*   [3\. Identifier](#3-identifier)
*   [4\. Image Requests](#4-image-requests)
    *   [4.1. Region](#41-region)
    *   [4.2. Size](#42-size)
    *   [4.3. Rotation](#43-rotation)
    *   [4.4. Quality](#44-quality)
    *   [4.5. Format](#45-format)
    *   [4.6. Order of Implementation](#46-order-of-implementation)
    *   [4.7. Floating Point Values](#47-floating-point-values)
    *   [4.8. Canonical URI Syntax](#48-canonical-uri-syntax)
    *   [4.9. Extensions](#49-extensions)
*   [5\. Image Information](#5-image-information)
    *   [5.1. Image Information Request](#51-image-information-request)
    *   [5.2. Technical Properties](#52-technical-properties)
    *   [5.3. Sizes](#53-sizes)
    *   [5.4. Tiles](#54-tiles)
    *   [5.5. Preferred Formats](#55-preferred-formats)
    *   [5.6. Rights](#56-rights)
    *   [5.7. Extra Functionality](#57-extra-functionality)
    *   [5.8. Linking Properties](#58-linking-properties)
    *   [5.9. Complete Response](#59-complete-response)
*   [6\. Compliance Level and Profile Document](#6-compliance-level-and-profile-document)
*   [7\. Server Responses](#7-server-responses)
    *   [7.1. CORS](#71-cors)
    *   [7.2. Successful Responses](#72-successful-responses)
    *   [7.3. Error Conditions](#73-error-conditions)
    *   [7.4. HTTP Versions](#74-http-versions)
*   [8\. Authentication](#8-authentication)
*   [9\. URI Encoding and Decoding](#9-uri-encoding-and-decoding)
*   [10\. Security Considerations](#10-security-considerations)
*   [11\. Appendices](#11-appendices)
    *   [A. Versioning](#a-versioning)
    *   [B. Acknowledgments](#b-acknowledgments)
    *   [C. Change Log](#c-change-log)

1\. Introduction
----------------

This document describes an image delivery API defined by the International Image Interoperability Framework (IIIF, pronounced “Triple-Eye-Eff”) Consortium. The IIIF Image API specifies a web service that returns an image in response to a standard HTTP or HTTPS request. The URI can specify the region, size, rotation, quality characteristics and format of the requested image. A URI can also be constructed to request basic technical information about the image to support client applications. This API was conceived of to facilitate systematic reuse of image resources in digital image repositories maintained by cultural heritage organizations. It could be adopted by any image repository or service, and can be used to retrieve static images in response to a properly constructed URI.

Please send feedback to [iiif-discuss@googlegroups.com](mailto:iiif-discuss@googlegroups.com "Email Discussion List").

### 1.1. Audience and Scope

This document is intended for architects and developers building applications that share and consume digital images, particularly from cultural heritage institutions, museums, libraries and archives. Target applications include:

*   Digital image repositories and distributed content networks.
*   Image focused web applications, such as pan/zoom viewers, book-readers, etc.
*   Client applications using image content for analysis or comparison.

This specification concerns image requests by a client, but not management of the images by the server. It covers how to respond to requests that follow a particular URI syntax, but does not cover methods of implementation such as rotation algorithms, transcoding, color management, compression, or how to respond to URIs that do not conform to the specified syntax. This allows flexibility for implementation in domains with particular constraints or specific community practices, while supporting interoperability in the general case.

Implementations may use a pre-generated set of files served as static web resources and still enable rich user experiences. Dynamic image server implementations may provide additional functionality beyond the base [level of compliance](/api/image/3.0/#6-compliance-level-and-profile-document "6. Compliance Level and Profile Document").

### 1.2. Terminology

The term **underlying image content** is used to refer to the source image data. No assumptions are made about its format or structure. It might be derived from one or more source images but could also be dynamically generated.

The term **full image** is used to refer to the entire area of the underlying image content, with the pixel dimensions given in the [image information](/api/image/3.0/#5-image-information "5. Image Information") document, and which is imagined as the starting point for [image requests](/api/image/3.0/#4-image-requests "4. Image Requests").

The key words _must_, _must not_, _required_, _shall_, _shall not_, _should_, _should not_, _recommended_, and _optional_ in this document are to be interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119 "RFC Keywords").

2\. URI Syntax
--------------

The IIIF Image API can be called in two ways:

*   Request an image, derived from the underlying image content.
*   Request information about the image service, including characteristics, functionality available, and related services.

Both convey the request’s information in the path segments of the URI, rather than as query parameters. This makes responses easier to cache, either at the server or by standard web-caching infrastructure. It also permits a minimal implementation using pre-computed files in a matching directory structure.

There are four parameters shared by the requests, and other IIIF specifications:

Name

Description

scheme

Indicates the use of the HTTP or HTTPS protocol in calling the service.

server

The host server on which the service resides. The parameter may also include a port number.

prefix

The path on the host server to the service. This prefix is optional, but may be useful when the host server supports multiple services. The prefix _may_ contain multiple path segments, delimited by slashes, but all other special characters _must_ be encoded. See [URI Encoding and Decoding](/api/image/3.0/#9-uri-encoding-and-decoding "9. URI Encoding and Decoding") for more information.

identifier

The identifier of the requested image. This may be an ARK, URN, filename, or other identifier. Special characters _must_ be URI encoded.

The combination of these parameters forms the image service’s base URI and identifies the underlying image content. It is constructed according to the following URI template ([RFC6570](https://tools.ietf.org/html/rfc6570 "URI Template")):

    {scheme}://{server}{/prefix}/{identifier}
    

When the base URI is dereferenced, the interaction _should_ result in the image information document. It is _recommended_ that the response be a 303 status redirection to the image information document’s URI. Implementations _may_ also exhibit other behavior for the base URI beyond the scope of this specification in response to HTTP request headers and methods.

To allow for extensions, this specification does not define the server behavior when it receives requests that do not match either the base URI or one of the described URI syntaxes below.

### 2.1. Image Request URI Syntax

The IIIF Image API URI for requesting an image _must_ conform to the following URI template:

    {scheme}://{server}{/prefix}/{identifier}/{region}/{size}/{rotation}/{quality}.{format}
    

For example:

    https://example.org/image-service/abcd1234/full/max/0/default.jpg
    

The parameters of the Image Request URI include region, size, rotation, quality and format, which define the characteristics of the returned image. These are described in detail in [Image Requests](/api/image/3.0/#4-image-requests "4. Image Requests").

### 2.2. Image Information Request URI Syntax

The URI for requesting image information _must_ conform to the following URI template:

    {scheme}://{server}{/prefix}/{identifier}/info.json
    

For example:

    https://example.org/image-service/abcd1234/info.json
    

The scheme, server, prefix and identifier components of the information request _must_ be identical to those for the image request described above for the image content that the image information document describes. The image information document is described in detail in the [Image Information](/api/image/3.0/#5-image-information "5. Image Information") section.

3\. Identifier
--------------

The API places no restrictions on the form of the identifiers that a server may use or support. All special characters (e.g. `?` or `#`) _must_ be URI encoded to avoid unpredictable client behaviors. The URI syntax relies upon slash (`/`) separators so any slashes in the identifier _must_ be URI encoded (also called “percent encoded”). See the additional discussion in [URI Encoding and Decoding](/api/image/3.0/#9-uri-encoding-and-decoding "9. URI Encoding and Decoding").

4\. Image Requests
------------------

All parameters described below are required for compliant construction of a IIIF Image API URI. The sequence of parameters in the URI _must_ be in the order described below. The order of the parameters is also intended as a mnemonic for the order of the operations by which the service should manipulate the image content. Thus, the requested image content is first extracted as a region of the full image, then scaled to the requested size, mirrored and/or rotated, and finally transformed into the requested color quality and format. This resulting image is returned as the representation for the URI.

Size and region parameters in pixels _must_ be non-negative integers. Size and region parameters in percentages and the rotation parameter _must_ be positive floating point numbers or integers. For details of the representation of floating point numbers in IIIF URIs, see the [Floating Point Values](/api/image/3.0/#47-floating-point-values "4.7. Floating Point Values") section.

Servers _should_ support [CORS](/api/image/3.0/#71-cors "7.1. CORS") on image responses.

### 4.1. Region

The region parameter defines the rectangular portion of the underlying image content to be returned. Region can be specified by pixel coordinates, percentage or by the value `full`, which specifies that the full image should be returned.

Form

Description

`full`

The full image is returned, without any cropping.

`square`

The region is defined as an area where the width and height are both equal to the length of the shorter dimension of the full image. The region may be positioned anywhere in the longer dimension of the full image at the server’s discretion, and centered is often a reasonable default.

_`x,y,w,h`_

The region of the full image to be returned is specified in terms of absolute pixel values. The value of _`x`_ represents the number of pixels from the 0 position on the horizontal axis. The value of _`y`_ represents the number of pixels from the 0 position on the vertical axis. Thus the _`x,y`_ position 0,0 is the upper left-most pixel of the image. _`w`_ represents the width of the region and _`h`_ represents the height of the region in pixels.

_`pct:x,y,w,h`_

The region to be returned is specified as a sequence of percentages of the full image’s dimensions, as reported in the image information document. Thus, _`x`_ represents the number of pixels from the 0 position on the horizontal axis, calculated as a percentage of the reported width. _`w`_ represents the width of the region, also calculated as a percentage of the reported width. The same applies to _`y`_ and _`h`_ respectively.

If the request specifies a region which extends beyond the dimensions of the full image as reported in the image information document, then the service _should_ return an image cropped at the image’s edge, rather than adding empty space.

If the requested region’s height or width is zero, or if the region is entirely outside the bounds of the reported dimensions, then the server _should_ return a 400 (Bad Request) status code.

Examples:

![Full Region](img/full.png)

**1** region=full

`.../full/max/0/default.jpg`

![Square Region](img/region_square.png)

**2** region=square

`.../square/max/0/default.jpg`

![Region by Pixels](img/region_px.png)

**3** region=125,15,120,140

`.../125,15,120,140/max/0/default.jpg`

![Region by Percent](img/region_pct.png)

**4** region=pct:41.6,7.5,40,70

`.../pct:41.6,7.5,40,70/max/0/default.jpg`

![Region by Pixels](img/region_px_over.png)

**5** region=125,15,200,200

`.../125,15,200,200/max/0/default.jpg`

_N.B. Returned image is 175,185 px_

![Region by Percent](img/region_pct_over.png)

**6** region=pct:41.6,7.5,66.6,100

`.../pct:41.6,7.5,66.6,100/max/0/default.jpg`

_N.B. Returned image is 175,185 px_

### 4.2. Size

The size parameter specifies the dimensions to which the extracted region, which might be the full image, is to be scaled. With the exception of the _`w,h`_ and _`^w,h`_ forms, the returned image maintains the aspect ratio of the extracted region as closely as possible. Sizes prefixed with `^` allow upscaling of the extracted region when its pixel dimensions are less than the pixel dimensions of the scaled region.

Form

Description

`max`

The extracted region is returned at the maximum size available, but will not be upscaled. The resulting image will have the pixel dimensions of the extracted region, unless it is constrained to a smaller size by `maxWidth`, `maxHeight`, or `maxArea` as defined in the [Technical Properties](/api/image/3.0/#52-technical-properties "5.2 Technical Properties") section.

`^max`

The extracted region is scaled to the maximum size permitted by `maxWidth`, `maxHeight`, or `maxArea` as defined in the [Technical Properties](/api/image/3.0/#52-technical-properties "5.2 Technical Properties") section. If the resulting dimensions are greater than the pixel width and height of the extracted region, the extracted region is upscaled.

_`w,`_

The extracted region should be scaled so that the width of the returned image is exactly equal to _`w`_. The value of _`w`_ _must not_ be greater than the width of the extracted region.

_`^w,`_

The extracted region should be scaled so that the width of the returned image is exactly equal to _`w`_. If _`w`_ is greater than the pixel width of the extracted region, the extracted region is upscaled.

_`,h`_

The extracted region should be scaled so that the height of the returned image is exactly equal to _`h`_. The value of _`h`_ _must not_ be greater than the height of the extracted region.

_`^,h`_

The extracted region should be scaled so that the height of the returned image is exactly equal to _`h`_. If _`h`_ is greater than the pixel height of the extracted region, the extracted region is upscaled.

_`pct:n`_

The width and height of the returned image is scaled to _`n`_ percent of the width and height of the extracted region. The value of _`n`_ _must not_ be greater than 100.

_`^pct:n`_

The width and height of the returned image is scaled to _`n`_ percent of the width and height of the extracted region. For values of _`n`_ greater than 100, the extracted region is upscaled.

_`w,h`_

The width and height of the returned image are exactly _`w`_ and _`h`_. The aspect ratio of the returned image _may_ be significantly different than the extracted region, resulting in a distorted image. The values of _`w`_ and _`h`_ _must not_ be greater than the corresponding pixel dimensions of the extracted region.

_`^w,h`_

The width and height of the returned image are exactly _`w`_ and _`h`_. The aspect ratio of the returned image _may_ be significantly different than the extracted region, resulting in a distorted image. If _`w`_ and/or _`h`_ are greater than the corresponding pixel dimensions of the extracted region, the extracted region is upscaled.

_`!w,h`_

The extracted region is scaled so that the width and height of the returned image are not greater than _`w`_ and _`h`_, while maintaining the aspect ratio. The returned image _must_ be as large as possible but not larger than the extracted region, _`w`_ or _`h`_, or server-imposed limits.

_`^!w,h`_

The extracted region is scaled so that the width and height of the returned image are not greater than _`w`_ and _`h`_, while maintaining the aspect ratio. The returned image _must_ be as large as possible but not larger than _`w`_, _`h`_, or server-imposed limits.

Requests for sizes not prefixed with `^` that result in a scaled region with pixel dimensions greater than the pixel dimensions of the extracted region are errors that _should_ result in a 400 (Bad Request) status code.

Requests for sizes prefixed with `^` that require upscaling _should_ result in a 501 (Not Implemented) status code if the server does not support upscaling, while a 400 (Bad Request) status code _should_ be returned in response to other client request syntax errors. For example, a request for the size `^pct:120` should result in a 501 status code if the server does not support upscaling.

For all requests the pixel dimensions of the scaled region _must not_ be less than 1 pixel or greater than the server-imposed limits. Requests that would generate images of these sizes are errors that _should_ result in a 400 (Bad Request) status code.

Examples:

![Maximum Size](img/size_max.png)

**1** size=max

`.../full/max/0/default.jpg`

_N.B. Assuming that the image has a `maxWidth` of 200px_

![Above Maximum Size](img/size_up_max.png)

**1** size=^max

`.../full/^max/0/default.jpg`

_N.B. Assuming that the image has a `maxWidth` of 360px_

![Size by Width](img/size_wc.png)

**2** size=150,

`.../full/150,/0/default.jpg`

![Size by Width Above Maximum](img/size_up_max.png)

**2** size=^360,

`.../full/^360,/0/default.jpg`

![Size by Height](img/size_ch.png)

**3** size=,150

`.../full/,150/0/default.jpg`

![Size by Height Above Maximum](img/size_up_max.png)

**3** size=,^240

`.../full/,^240/0/default.jpg`

![Size by Percent](img/size_pct.png)

**4** size=pct:50

`.../full/pct:50/0/default.jpg`

![Size by Percent Above Maximum](img/size_up_max.png)

**4** size=pct:120

`.../full/pct:120/0/default.jpg`

![Size by Width,Height](img/size_wch.png)

**5** size=225,100

`.../full/225,100/0/default.jpg`

![Size by Width,Height Above Maximum](img/size_up_wch.png)

**5** size=^360,360

`.../full/^360,360/0/default.jpg`

![Size By Bang Width Height](img/size_bwch.png)

**6** size=!225,100

`.../full/!225,100/0/default.jpg`

_N.B. Returned image is 150,100 px_

![Size By Bang Width Height Above Maximum](img/size_up_bwch.png)

**6** size=^!360,360

`.../full/^!360,360/0/default.jpg`

_N.B. Returned image is 360,240 px_

### 4.3. Rotation

The rotation parameter specifies mirroring and rotation. A leading exclamation mark (“!”) indicates that the image should be mirrored by reflection on the vertical axis before any rotation is applied. The numerical value represents the number of degrees of clockwise rotation, and may be any floating point number from 0 to 360.

Form

Description

_`n`_

The degrees of clockwise rotation from 0 up to 360.

_`!n`_

The image should be mirrored and then rotated as above.

A rotation value that is out of range or unsupported _should_ result in a 400 (Bad Request) status code.

In most cases, rotation will change the width and height dimensions of the returned image. The service _should_ return an image that contains all of the image contents requested in the region and size parameters, even if the dimensions of the returned image file are different than specified in the size parameter. The image contents _should not_ be scaled as a result of the rotation, and there _should_ be no additional space between the corners of the rotated image contents and the bounding box of the returned image.

For rotations which are not multiples of 90 degrees, it is _recommended_ that the client request the image in a format that supports transparency, such as `png`, and that the server return the image with a transparent background. There is no facility in the API for the client to request a particular background color or other fill pattern.

Examples:

![Rotation 0](img/full.png)

**1** rotation=0

`.../full/max/0/default.jpg`

![Rotation 180](img/rotate_180.png)

**2** rotation=180

`.../full/max/180/default.jpg`

![Rotation 90](img/rotate_90.png)

**3** rotation=90

`.../full/max/90/default.jpg`

![Rotation 22.5](img/rotate_22-5.png)

**4** rotation=22.5

`.../full/max/22.5/default.png`

![Mirroring](img/mirror.png)

**5** rotation=!0

`.../full/max/!0/default.jpg`

![Mirroring and Rotation](img/mirror_180.png)

**6** rotation=!180

`.../full/max/!180/default.jpg`

### 4.4. Quality

The quality parameter determines whether the image is delivered in color, grayscale or black and white.

Quality

Parameter Returned

`color`

The image is returned with all of its color information.

`gray`

The image is returned in grayscale, where each pixel is black, white or any shade of gray in between.

`bitonal`

The image returned is bitonal, where each pixel is either black or white.

`default`

The image is returned using the server’s default quality (e.g. `color`, `gray` or `bitonal`) for the image.

The `default` quality exists to support [level 0 compliant implementations](/api/image/3.0/compliance/#quality "Image API Compliance: Quality") that may not know the qualities of individual images in their collections. It also provides a convenience for clients that know the values for all other parameters of a request except the quality (e.g. `.../full/120,80/90/{quality}.png` to request a thumbnail) in that a preliminary image information request that would only serve to find out which qualities are available can be avoided.

Regardless of level of compliance, services that make additional qualities beyond `default` available _must_ list those qualities in the [`extraQualities` property](/api/image/3.0/#57-extra-functionality "5.7. Extra Functionality") of the response to the [Image Information Request](/api/image/3.0/#5-image-information "5. Image Information"). A request for an image with an unsupported quality value _should_ return a 400 (Bad Request) status code.

A request for the `color` quality of an image _must_ return an image. This image may be comprised solely of grayscale or bitonal pixels if this is all of the color information the server has available. The server _should not_ include `color` in the `extraQualities` list in such cases, but a request for the `color` quality _must not_ result in an error. Similarly, a request for the grayscale quality may return an image comprised solely of bitonal pixels.

Examples:

![Default Quality](img/full.png)

**1** quality=default

`.../full/max/0/default.jpg`

![Color Quality](img/full.png)

**2** quality=color

`.../full/max/0/color.jpg`

![Gray Quality](img/gray.png)

**3** quality=gray

`.../full/max/0/gray.jpg`

![Bitonal Quality](img/bitonal.png)

**4** quality=bitonal

`.../full/max/0/bitonal.jpg`

### 4.5. Format

The format of the returned image is expressed as a suffix, mirroring common filename extensions, at the end of the URI.

Extension

MIME Type

`jpg`

image/jpeg

`tif`

image/tiff

`png`

image/png

`gif`

image/gif

`jp2`

image/jp2

`pdf`

application/pdf

`webp`

image/webp

A format value that is unsupported _should_ result in a 400 (Bad Request) status code.

Examples:

1.  `.../full/max/0/default.jpg`
2.  `.../full/max/0/default.png`
3.  `.../full/max/0/default.tif`

### 4.6. Order of Implementation

The sequence of parameters in the URI is intended as a mnemonic for the order in which image manipulations are made against the underlying image content. This is important to consider when implementing the image service because applying the same parameters in a different sequence will often result in a different image being delivered.

The parameters should be interpreted as if the sequence of image manipulations were:

`Region THEN Size THEN Rotation THEN Quality THEN Format`

If the rotation parameter includes mirroring (`!`), the mirroring is applied before the rotation.

![Order of Implementation](img/transformation.png)

**1** region=125,15,120,140 size=90, rotation=!345 quality=gray

`.../125,15,120,140/90,/!345/gray.jpg`

### 4.7. Floating Point Values

Size and region parameters given as percentages and the rotation parameter allow positive floating point number values. Integer values _should_ be used where possible. When floating point values are used, they _must_ consist only of decimal digits and “.” (e.g. 0.9 not +0.9), _should_ be represented with a leading 0 if less than 1 (e.g. 0.9 not .9), and _should not_ include trailing zeros (e.g. 0.9 not 0.90). Intermediate calculations may use floating point numbers and the rounding method is implementation specific.

### 4.8. Canonical URI Syntax

It is possible to request the same image using different combinations of parameters. While it is useful for clients to be able to express their requests in a convenient form, there are several reasons why a canonical URI syntax is desirable:

*   It enables static, file-system based implementations, which will have only a single URI at which the content is available.
*   Caching becomes significantly more efficient, both client and server side, when the URIs used are the same between systems and sessions.
*   Response times can be improved by avoiding redirects from a requested non-canonical URI syntax to the canonical syntax by using the canonical form directly.

In order to support the above requirements, clients _should_ construct image request URIs using the following canonical parameter values where possible. Image servers _may_ redirect the client to the canonical URI from a non-canonical equivalent.

Parameter

Canonical value

region

`full` if the full image is requested  
otherwise the _`x,y,w,h`_ syntax.

size

`max` if the maximum size without upscaling is requested,  
`^max` if the maximum upscaled size is requested, otherwise  
_`w,h`_ if the size requested does not require upscaling, or  
_`^w,h`_ if the request requires upscaling of the extracted region.

rotation

`!` if the image is mirrored, followed by an integer if possible, otherwise a floating point value represented according to the recommendations of the [Floating Point Values](/api/image/3.0/#47-floating-point-values "4.7. Floating Point Values") section.

quality

`default` if the server’s default quality is requested,  
otherwise the quality string.

format

An explicit format string is always required.

When the client requests an image, the server _may_ add a link header to the response that indicates the canonical URI for that request:

    Link: <http://iiif.example.com/server/full/400,300/0/default.jpg>;rel="canonical"
    

The server _may_ also include this link header on the image information response, however it is unnecessary as it is included in the JSON representation retrieved.

### 4.9. Extensions

The IIIF Image API is extensible within the [Image Request URI Syntax](/api/image/3.0/#22-image-information-request-uri-syntax "2.2. Image Information Request URI") through the addition of new parameter patterns for the [region](/api/image/3.0/#41-region "4.1. Region"), [size](/api/image/3.0/#42-size "4.2. Size") and [rotation](/api/image/3.0/#43-rotation "4.3. Rotation") parameters, or new values for the [quality](/api/image/3.0/#44-quality "4.4. Quality") and [format](/api/image/3.0/#45-format "4.5. Format") parameters. Request information beyond the scope of the existing parameters could be passed to an image server as query parameters. Extension features _should_ be described in the image information document following the guidelines in the [Extra Functionality](/api/image/3.0/#57-extra-functionality "5.7. Extra Functionality") section.

5\. Image Information
---------------------

Servers _must_ support requests for image information. The response is a JSON document that includes technical properties about the full image. It may also contain rights information, and services related to the image.

### 5.1. Image Information Request

The request for the image information _must_ conform to the URI template:

    {scheme}://{server}{/prefix}/{identifier}/info.json
    

The syntax for the response is [JSON-LD](http://www.w3.org/TR/json-ld/ "JSON-LD 1.0"). If the server receives a request with an `Accept` header, it _should_ respond following the rules of [content negotiation](https://tools.ietf.org/html/rfc7231#section-5.3.2 "HTTP 1.1, 5.3.2. Accept"). Note that content types provided in the `Accept` header of the request _may_ include parameters, for example `profile` or `charset`.

If the request does not include an `Accept` header, the HTTP `Content-Type` header of the response _should_ have the value `application/ld+json` (JSON-LD) with the `profile` parameter given as the context document: `http://iiif.io/api/image/3/context.json`.

    Content-Type: application/ld+json;profile="http://iiif.io/api/image/3/context.json"
    

If the `Content-Type` header `application/ld+json` cannot be generated due to server configuration details, then the `Content-Type` header _should_ instead be `application/json` (regular JSON), without a `profile` parameter.

    Content-Type: application/json
    

Servers _should_ support [CORS](/api/image/3.0/#71-cors "7.1. CORS") on image information responses.

### 5.2. Technical Properties

The JSON response has several technical properties that describe the available functionality for the image content.

Property

Required?

Description

`@context`

Required

The `@context` property _should_ appear as the very first key-value pair of the JSON representation. Its value _must_ be either the URI `http://iiif.io/api/image/3/context.json` or a JSON array with the URI `http://iiif.io/api/image/3/context.json` as the last item. The `@context` tells Linked Data processors how to interpret the image information. If extensions are used then their context definitions _should_ be included in this top-level `@context` property.

`id`

Required

The base URI of the image as defined in [URI Syntax](/api/image/3.0/#2-uri-syntax "2. URI Syntax"), including scheme, server, prefix and identifier without a trailing slash.

`type`

Required

The type for the Image API. The value _must_ be the string `ImageService3`.

`protocol`

Required

The URI `http://iiif.io/api/image` which can be used to determine that the document describes an image service which is a version of the IIIF Image API.

`profile`

Required

A string indicating the highest [compliance level](/api/image/3.0/#6-compliance-level-and-profile-document "6. Compliance Level and Profile Document") which is fully supported by the service. The value _must_ be one of `level0`, `level1`, or `level2`.

`width`

Required

The width in pixels of the full image, given as an integer.

`height`

Required

The height in pixels of the full image, given as an integer.

`maxWidth`

Optional

The maximum width in pixels supported for this image. Clients _must not_ expect requests with a width greater than this value to be supported. `maxWidth` _must_ be specified if `maxHeight` is specified.

`maxHeight`

Optional

The maximum height in pixels supported for this image. Clients _must not_ expect requests with a height greater than this value to be supported. If `maxWidth` is specified and `maxHeight` is not, then clients should infer that `maxHeight = maxWidth`.

`maxArea`

Optional

The maximum area in pixels supported for this image. Clients _must not_ expect requests with a width\*height greater than this value to be supported.

The `width` and `height` properties give the size of the full image and are required in order to construct tile requests.

The `maxWidth`, `maxHeight`, and `maxArea` parameters provide a way for image servers to express limits on the sizes supported for the image. If `maxWidth` alone, or `maxWidth` and `maxHeight` are specified then clients should expect requests with larger linear dimensions to be rejected. If `maxArea` is specified then clients should expect requests with larger pixel areas to be rejected. The `maxWidth / maxHeight` and `maxArea` parameters are independent, servers may implement either or both limits. Servers _must_ ensure that sizes specified by any `sizes` or `tiles` properties are within any size limits expressed. Clients _should not_ make requests that exceed size limits expressed.

    {
      "@context": "http://iiif.io/api/image/3/context.json",
      "id": "https://example.org/image-service/abcd1234/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "maxHeight": 2000,
      "maxWidth": 3000,
      "maxArea": 4000000
    }
    

### 5.3. Sizes

The JSON response _may_ have the `sizes` property, which is used to describe preferred `height` and `width` combinations for representations of the full image.

Property

Required?

Description

`sizes`

Optional

An array of JSON objects with the `height` and `width` properties. These sizes specify preferred values to be provided in the _`w,h`_ syntax of the size request parameter for scaled versions of the full image. In the case of servers that do not support requests for arbitrary sizes, these may be the only sizes available. A request constructed with the _`w,h`_ syntax using these sizes _must_ be supported by the server, even if arbitrary width and height are not.

The JSON objects in the `sizes` array have the properties in the following table. Image requests for these sizes _should_ have a region parameter of `full`, size parameter in the canonical _`w,h`_ form, and rotation of `0`. Thus, the full URL for an image with `default` quality in `jpg` format would be: `{scheme}://{server}/{prefix}/{identifier}/full/{width},{height}/0/default.jpg`

Property

Required?

Description

`type`

Optional

The type of the object. If present, the value _must_ be the string `Size`.

`width`

Required

The width in pixels of the image to be requested, given as an integer.

`height`

Required

The height in pixels of the image to be requested, given as an integer.

    {
      "@context": "http://iiif.io/api/image/3/context.json",
      "id": "https://example.org/image-service/abcd1234/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "sizes": [
        { "width": 150, "height": 100 },
        { "width": 600, "height": 400 },
        { "width": 3000, "height": 2000 }
      ]
    }
    

### 5.4. Tiles

The JSON response _may_ have the `tiles` property which describes a set of image regions that have a consistent height and width, over a series of resolutions, that can be stitched together visually.

Property

Required?

Description

`tiles`

Optional

An array of JSON objects describing the parameters to use to request regions of the image (tiles) that are efficient for the server to deliver. Each description gives a width, optionally a height for non-square tiles, and a set of scale factors at which tiles of those dimensions are available.

The JSON objects in the `tiles` array have the properties in the following table. The `width` and `height` should be used to fill the size parameter, and be used together with the `scaleFactors` to compute the region parameter of the image requests. This is described in detail in the [Implementation Notes](/api/image/3.0/implementation/ "Implementation Notes").

Property

Required?

Description

`type`

Optional

The type of the object. If present, the value _must_ be the string `Tile`.

`scaleFactors`

Required

The set of resolution scaling factors for the image’s predefined tiles, expressed as positive integers by which to divide the full size of the image. For example, a scale factor of 4 indicates that the service can efficiently deliver images at 1/4 or 25% of the height and width of the full image. A particular scale factor value _should_ appear only once in the `tiles` array.

`width`

Required

The width in pixels of the predefined tiles to be requested, given as an integer.

`height`

Optional

The height in pixels of the predefined tiles to be requested, given as an integer. If it is not specified in the JSON, then it defaults to the same as `width`, resulting in square tiles.

Objects in the `tiles` array _must_ each have a unique combination of `width` and `height`, where `height` = `width` if it is not explicitly specified.

    {
      "@context": "http://iiif.io/api/image/3/context.json",
      "id": "https://example.org/image-service/abcd1234/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "tiles": [
        { "width": 512, "scaleFactors": [ 1, 2, 4, 8, 16 ] }
      ]
    }
    

### 5.5. Preferred Formats

The JSON response _may_ have the `preferredFormats` property, which lists one or more format parameter values for this image service. This allows the publisher to express a preference for the format a client requests, for example to encourage use of a more efficient format such as webp, or to suggest a format that will give better results for the image content, such as lossless webp or png for line art or graphics.

Property

Required?

Description

`preferredFormats`

Optional

An array of strings that are the preferred format parameter values, arranged in order of preference. The format parameter values listed _must_ be among those specified in the referenced profile or listed in the `extraFormats` property (see [Extra Functionality](/api/image/3.0/#57-extra-functionality "5.7. Extra Functionality")).

    {
      "@context": "http://iiif.io/api/image/3/context.json",
      "id": "https://example.org/image-service/",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "extraFormats": [ "webp" ],
      "preferredFormats": [ "webp", "png" ]
    }
    

### 5.6. Rights

The `rights` property has the same semantics and requirements as it does in the [Presentation API](/api/presentation/3.0/ "Presentation API").

Property

Required?

Description

`rights`

Optional

A string that identifies a license or rights statement that applies to the content of this image. The value of this property _must_ be a string drawn from the set of [Creative Commons](https://creativecommons.org/licenses/ "Create Commons Licenses") license URIs, the [RightsStatements.org](http://rightsstatements.org/page/1.0/ "rightsstatements.org") rights statement URIs, or those added via the [Registry of Known Extensions](/api/registry/ "IIIF Extension Registry") mechanism. The inclusion of this property is informative, and for example could be used to display an icon representing the rights assertions.

If the publisher of this image requires additional information to be shown when it is viewed, the information should be provided by a [Presentation API](/api/presentation/3.0/ "Presentation API") Manifest, as described in the [Linking Properties](/api/image/3.0/#58-linking-properties "5.8. Linking Properties") section.

    {
      "@context": "http://iiif.io/api/image/3/context.json",
      "id": "https://example.org/image-service/abcd1234/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "rights": "http://rightsstatements.org/vocab/InC-EDU/1.0/"
    }
    

### 5.7. Extra Functionality

The JSON response _may_ also contain properties that describe additional functionality available via the image service.

Property

Required?

Description

`extraQualities`

Optional

An array of strings that can be used as the quality parameter, in addition to `default`.

`extraFormats`

Optional

An array of strings that can be used as the format parameter, in addition to the ones specified in the referenced profile.

`extraFeatures`

Optional

An array of strings identifying features supported by the service, in addition to the ones specified in the referenced profile. These strings are defined either in the [table](/api/image/3.0/#features-table) below or by [registering an extension](/api/extension/).

The following features are defined for use in the `extraFeatures` property:

Feature Name

Description

`baseUriRedirect`

The base URI of the service will redirect to the image information document.

`canonicalLinkHeader`

The canonical image URI HTTP link header is provided on image responses.

`cors`

The CORS HTTP headers are provided on all responses.

`jsonldMediaType`

The JSON-LD media type is provided when requested.

`mirroring`

The image may be rotated around the vertical axis, resulting in a left-to-right mirroring of the content.

`profileLinkHeader`

The profile HTTP link header is provided on image responses.

`regionByPct`

Regions of the full image may be requested by percentage.

`regionByPx`

Regions of the full image may be requested by pixel dimensions.

`regionSquare`

A square region may be requested, where the width and height are equal to the shorter dimension of the full image.

`rotationArbitrary`

Image rotation may be requested using values other than multiples of 90 degrees.

`rotationBy90s`

Image rotation may be requested in multiples of 90 degrees.

`sizeByConfinedWh`

Image size may be requested in the form _`!w,h`_.

`sizeByH`

Image size may be requested in the form _`,h`_.

`sizeByPct`

Images size may be requested in the form _`pct:n`_.

`sizeByW`

Image size may be requested in the form _`w,`_.

`sizeByWh`

Image size may be requested in the form _`w,h`_.

`sizeUpscaling`

Image sizes prefixed with `^` may be requested.

A server that supports neither `sizeByW` or `sizeByWh` is only required to serve the image sizes listed under the `sizes` property or implied by the `tiles` property of the image information document, allowing for a static file implementation.

A server that supports `sizeUpscaling` _must_ specify `maxWidth` or `maxArea` (see [Technical Properties](/api/image/3.0/#52-technical-properties "5.2 Technical Properties")).

The set of features, formats and qualities supported is the union of those declared in the external profile document and those added by the `extraQualities`, `extraFormats`, and `extraFeatures` properties. If a feature is not present in either the profile document or the `extraFeatures` property, then a client _must_ assume that the feature is not supported.

Additional strings used in the `extraQualities`, `extraFormats`, and `extraFeatures` properties, or additional properties used in the image information, that are not defined in this specification _should_ be mapped to RDF predicates using further context documents. These extensions _should_ be added to the top level `@context` property (see [Technical Properties](/api/image/3.0/#52-technical-properties "5.2 Technical Properties")). The JSON-LD 1.1 functionality of predicate specific context definitions, known as [scoped contexts](https://json-ld.org/spec/latest/json-ld/#scoped-contexts "JSON-LD Scoped Contexts"), _must_ be used to minimize cross-extension collisions. Extensions intended for community use _should_ be [registered in the extensions registry](/api/registry/ "IIIF Extension Registry"), but registration is not mandatory.

    {
      "@context": "http://iiif.io/api/image/3/context.json",
      "id": "https://example.org/image-service/abcd1234/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "extraFormats": [ "gif", "pdf" ],
      "extraQualities": [ "color", "gray" ],
      "extraFeatures": [ "canonicalLinkHeader", "rotationArbitrary", "profileLinkHeader" ]
    }
    

### 5.8. Linking Properties

The JSON response _may_ contain linking properties that reference external resources, including services that make additional functionality available to a viewer. The linking properties have the same semantics and requirements as those in the [Presentation API](/api/presentation/3.0/ "Presentation API").

Property

Required?

Description

`partOf`

Optional

A link to another resource that references this image service, for example a link to a Canvas or Manifest. The value _must_ be an array of JSON objects. Each item _must_ have the `id` and `type` properties, and _should_ have the `label` property.

`seeAlso`

Optional

A link to an external, machine-readable resource that is related to this resource, such as an XML or RDF description. Properties of the external resource should be given to help the client select between multiple descriptions (if provided), and to make appropriate use of the document. The URI of the document _must_ identify a single representation of the data in a particular format. The value _must_ be an array of JSON objects. Each item _must_ have the `id` and `type` properties, and _should_ have the `label`, `format` and `profile` properties.

`service`

Optional

A reference to an external service that the client might interact with directly to gain additional information or functionality, for example a link to an authentication service. The value _must_ be an array of JSON objects. Each object will have properties depending on the service’s definition, but _must_ have either the `id` and `type` properties, or the `@id` and `@type` properties for backwards compatibility with other IIIF APIs. Each object _should_ have a `profile` property. See the [Service Registry](/api/annex/services/ "Services Annex Document") for known service types.

The JSON objects in `partOf`, `seeAlso`, and `service` have the properties indicated in the following table.

Property

Required?

Description

`id`

Required

The URI of the external resource. (The `@id` property _may_ be used in `service` objects for backwards compatibility as described above.)

`type`

Required

The type or class of this resource. Recommendations for basic types such as image, text or audio are [given in the Presentation API](/api/presentation/3.0/#type). (The `@type` property _may_ be used in `service` objects for backwards compatibility as described above.)

`label`

Recommended

A human-readable label for this resource. The `label` property can be fully internationalized, and each language can have multiple values. This pattern is described in more detail in [the languages section of the Presentation API](/api/presentation/3.0/#language-of-property-values "Language of Property Values").

`format`

Recommended for `seeAlso`

The specific media type (often called a MIME type) for this content resource, for example “image/jpeg”. This is important for distinguishing different formats of the same overall type of resource, such as distinguishing text in XML from plain text. The value must be a string, and it should be the value of the Content-Type header returned when this resource is dereferenced.

`profile`

Recommended for `seeAlso`, `service`

A schema or named set of functionality available from this resource. The profile can further clarify the `type` and/or `format` of an external resource. The value must be a string, either taken from the [Registry of Profiles](/api/registry/ "IIIF Extension Registry") or a URI.

    {
      "@context": [
        "http://iiif.io/api/image/3/context.json"
      ],
      "id": "https://example.org/image-service/abcd12345/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level2",
      "width": 6000,
      "height": 4000,
      "seeAlso": [
        {
          "id": "https://example.org/image1.xml",
          "label": { "en": [ "Technical image metadata" ] },
          "type": "Dataset",
          "format": "text/xml",
          "profile": "https://example.org/profiles/imagedata"
        }
      ],
      "partOf": [
        {
          "id": "https://example.org/manifest/1",
          "type": "Manifest",
          "label": { "en": [ "A Book" ] }
        }
      ],
      "service": [
        {
          "@id": "https://example.org/auth/login",
          "@type": "AuthCookieService1",
          "profile": "http://iiif.io/api/auth/1/login",
          "label": "Login to Example Institution"
        }
      ]
    }
    

### 5.9. Complete Response

The following shows an image information response including all of the required and optional properties.

    {
      "@context": [
        "http://example.org/extension/context1.json",
        "http://iiif.io/api/image/3/context.json"
      ],
      "id": "https://example.org/image-service/abcd1234/1E34750D-38DB-4825-A38A-B60A345E591C",
      "type": "ImageService3",
      "protocol": "http://iiif.io/api/image",
      "profile": "level1",
      "width": 6000,
      "height": 4000,
      "maxWidth": 3000,
      "maxHeight": 2000,
      "maxArea": 4000000,
      "sizes": [
        { "width": 150, "height": 100 },
        { "width": 600, "height": 400 },
        { "width": 3000, "height": 2000 }
      ],
      "tiles": [
        { "width": 512, "scaleFactors": [ 1, 2, 4 ] },
        { "width": 1024, "height": 2048, "scaleFactors": [ 8, 16 ] }
      ],
      "rights": "http://rightsstatements.org/vocab/InC-EDU/1.0/",
      "preferredFormats": [ "png", "gif"],
      "extraFormats": [ "png", "gif", "pdf" ],
      "extraQualities": [ "color", "gray" ],
      "extraFeatures": [ "canonicalLinkHeader", "rotationArbitrary", "profileLinkHeader" ],
      "service": [
        {
          "id": "https://example.org/service/example",
          "type": "Service",
          "profile": "https://example.org/docs/example-service.html"
        }
      ]
    }
    

6\. Compliance Level and Profile Document
-----------------------------------------

The image information document _must_ specify the extent to which the API is supported by including the compliance level as the value of the `profile` property. The compliance level _must_ be one of those listed in the [Image API Compliance](/api/image/3.0/compliance/ "Image API Compliance") document and shown in the table below. The compliance level _should_ be the highest compliance level for which all requirements are met. The compliance levels each correspond with a profile document that describes the set of features required by that level, as discussed in the [Image Information](/api/image/3.0/#5-image-information "5. Image Information") section. A server _may_ declare different compliance levels for images with different identifiers.

Compliance level

Profile document URI

`level0`

`http://iiif.io/api/image/3/level0.json`

`level1`

`http://iiif.io/api/image/3/level1.json`

`level2`

`http://iiif.io/api/image/3/level2.json`

The compliance level _may_ also be given in a HTTP `Link` header ([RFC5988](https://tools.ietf.org/html/rfc5988 "Web Linking")), using the profile document URI with the parameter `rel="profile"`, on both Image and Image Information responses. A complete header might look like:

    Link: <http://iiif.io/api/image/3/level1.json>;rel="profile"
    

A recipe for setting this header on the Apache HTTP Server is shown in the [Apache HTTP Server Implementation Notes](/api/annex/notes/apache/#set-compliance-link-header "Apache HTTP Server Implementation Notes: Set Compliance Link Header").

7\. Server Responses
--------------------

Servers _must_ support the HTTP GET method for retrieval of Image API resources. Servers _should_ support the HTTP OPTIONS method as part of the [CORS](/api/image/3.0/#71-cors "7.1. CORS") preflight request pattern, and it is _recommended_ that implementations also support the HTTP HEAD method.

### 7.1. CORS

Servers _should_ support reuse of Image API resources by following the relevant requirements of the [CORS specification](https://www.w3.org/TR/cors/ "Cross-Origin Resource Sharing"), including the `Access-Control-Allow-Origin` header and the preflight request pattern. A recipe for enabling these behaviors is provided in the [Apache HTTP Server Implementation Notes](/api/annex/notes/apache/#conditional-content-types "Apache HTTP Server Implementation Notes: Conditional Content Types").

### 7.2. Successful Responses

Servers may transmit HTTP responses with 200 (Successful) or 3xx (Redirect) status codes when the request has been successfully processed. If the status code is 200, then the entity-body _must_ be the requested image or information document. If the status code is 301, 302, 303, or 304, then the entity-body is unrestricted, but it is _recommended_ to be empty. If the status code is 301, 302, or 303 then the Location HTTP Header _must_ be set containing the URI of the image that fulfills the request. This enables servers to have a single canonical URI to promote caching of responses. Status code 304 is handled exactly as per the HTTP specification. Clients _should_ expect to encounter all of these situations and _must not_ assume that the entity-body of the initial response necessarily contains the image data.

### 7.3. Error Conditions

The order in which servers parse requests and detect errors is not specified. A request is likely to fail on the first error encountered and return an appropriate HTTP status code, with common codes given in the list below. It is _recommended_ that the body of the error response includes a human-readable description of the error in either plain text or html.

Status Code

Description

400 Bad Request

The server cannot fulfill the request, as the syntax of the request issued by the client is incorrect.

401 Unauthorized

Authentication is required and not provided. See the [Authentication](/api/image/3.0/#8-authentication "8. Authentication") section for details.

403 Forbidden

The user, authenticated or not, is not permitted to perform the requested operation.

404 Not Found

The image resource specified by [identifier](/api/image/3.0/#3-identifier "3. Identifier") does not exist, the value of one or more of the parameters is not supported for this image service, or the requested size is greater than the limits specified.

500 Internal Server Error

The server encountered an unexpected error that prevented it from fulfilling the request.

501 Not Implemented

The server received a valid IIIF request that is not implemented.

503 Service Unavailable

The server is busy/temporarily unavailable due to load/maintenance issues.

### 7.4. HTTP Versions

Implementations that anticipate the need to respond to many concurrent requests from the same client _should_ make the API available via [HTTP/2](https://tools.ietf.org/html/rfc7540 "HTTP/2") in order to avoid repeatedly opening and closing connections. This also avoids the browser-imposed limit on the number of concurrent connections per site via [HTTP 1.1](https://tools.ietf.org/html/rfc7230 "HTTP 1.1").

8\. Authentication
------------------

Images are generally secondary resources in a web page or application. In the case of web pages, images are embedded in the HTML `img` tag, and are retrieved via additional HTTP requests. When a user cannot load a web page, it is possible — and a generally accepted behavior — to redirect the user to another page and offer the opportunity to authenticate. This is not an option for secondary resources such as images, and the user is instead simply presented with a broken image icon.

No new authentication mechanisms are proposed, nor roles for authorization business logic. Instead, it is expected that authentication requirements and processes are handled outside of any IIIF\-specific context, but within a IIIF\-aware access control workflow. Please see the [IIIF Authentication specification](/api/auth/1.0/ "IIIF Authentication API 1.0").

9\. URI Encoding and Decoding
-----------------------------

The URI syntax of this API relies upon slash (`/`) separators which _must not_ be encoded. Clients _must_ percent-encode special characters (the to-encode set below: percent and gen-delims of [RFC3986](https://tools.ietf.org/html/rfc3986 "Uniform Resource Identifier (URI): Generic Syntax") except the colon) plus any characters outside the US-ASCII set within the components of requests. For example, any slashes within the identifier part of the URI _must_ be percent-encoded. Encoding is necessary only for the identifier because other components will not include special characters. Percent-encoding other characters introduces no ambiguity but is unnecessary.

    to-encode = "/" / "?" / "#" / "[" / "]" / "@" / "%"
    

Parameters

URI path

identifier=id1 region=full size=max rotation=0 quality=default

`id1/full/max/0/default`

identifier=id1 region=0,10,100,200 size=pct:50 rotation=90 quality=default format=png

`id1/0,10,100,200/pct:50/90/default.png`

identifier=id1 region=pct:10,10,80,80 size=50, rotation=22.5 quality=color format=jpg

`id1/pct:10,10,80,80/50,/22.5/color.jpg`

identifier=bb157hs6068 region=full size=max rotation=270 quality=gray format=jpg

`bb157hs6068/full/max/270/gray.jpg`

identifier=ark:/12025/654xz321 region=full size=max rotation=0 quality=default

`ark:%2F12025%2F654xz321/full/max/0/default`

identifier=urn:foo:a123,456 region=full size=max rotation=0 quality=default

`urn:foo:a123,456/full/max/0/default`

identifier=urn:sici:1046-8188(199501)13:1%3C69:FTTHBI%3E2.0.TX;2-4 region=full size=max rotation=0 quality=default

`urn:sici:1046-8188(199501)13:1%253C69:FTTHBI%253E2.0.TX;2-4/full/max/0/default`

identifier=https://example.com/?54#a region=full size=max rotation=0 quality=default

`http:%2F%2Fexample.com%2F%3F54%23a/full/max/0/default`

Servers which are incapable of processing arbitrarily encoded identifiers _should_ make their best efforts to expose only image identifiers for which clients will not encode any of the characters, and thus it is _recommended_ to limit characters in identifiers to letters, numbers and the underscore character.

10\. Security Considerations
----------------------------

This API defines a URI syntax and the semantics associated with its components. The composition of URIs has few security considerations except possible exposure of sensitive information in URIs or revealing of browse/view behavior of users.

Server applications implementing this API should consider possible denial-of-service attacks, and authentication vulnerabilities based on DNS spoofing. Applications must be careful to parse and sanitize incoming requests (URIs) in ways that avoid overflow, injection, and directory traversal attacks.

Early sanity checking of URIs (lengths, trailing GET, invalid characters, out-of-range parameters) and rejection with appropriate response codes is recommended.

11\. Appendices
---------------

### A. Versioning

Starting with version 2.0, this specification follows [Semantic Versioning](http://semver.org/spec/v2.0.0.html "Semantic Versioning 2.0.0"). See the note [Versioning of APIs](/api/annex/notes/semver/ "Versioning of APIs") for details regarding how this is implemented.

### B. Acknowledgments

Many thanks to the members of the [IIIF community](/community/ "IIIF Community") for their continuous engagement, innovative ideas and feedback.

### C. Change Log

Date

Description

2020-06-03

Version 3.0 (Orange Blooms) [View change log](/api/image/3.0/change-log/ "Image API 3.0 Change Log")

2017-06-09

Version 2.1.1 [View change log](/api/image/2.1/change-log-211/ "Image API 2.1.1 Change Log")

2016-05-12

Version 2.1 (Crowned Eagle) [View change log](/api/image/2.1/change-log/ "Change Log for Version 2.1")

2014-09-11

Version 2.0 (Voodoo Bunny) [View change log](/api/image/2.0/change-log/ "Change Log for Version 2.0")

2013-09-17

Version 1.1 (unnamed) [View change log](/api/image/1.1/change-log/ "Change Log for Version 1.1")

2012-08-10

Version 1.0 (unnamed)

*   Feedback: [iiif-discuss@googlegroups.com](mailto:iiif-discuss@googlegroups.com)
*   Get involved: [Join IIIF](https://iiif.io/community/#how-to-get-involved)

(function(i,s,o,g,r,a,m){i\['GoogleAnalyticsObject'\]=r;i\[r\]=i\[r\]||function(){ (i\[r\].q=i\[r\].q||\[\]).push(arguments)},i\[r\].l=1\*new Date();a=s.createElement(o), m=s.getElementsByTagName(o)\[0\];a.async=1;a.src=g;m.parentNode.insertBefore(a,m) })(window,document,'script','//www.google-analytics.com/analytics.js','ga'); ga('create', 'UA-7219229-22', 'iiif.io'); ga('send', 'pageview');
