---
layout: postc
title:  "Graphics Dimensions For Social Networks"
date:   2017-06-28 09:58:57 +0100
tags: facebook twitter product-hunt
---
Every social platform has their own requirements for used graphics. In this post I am summarizing their dimensions.

![Graphics Dimensions For Social Networks](/assets/2017-06-28-social-media-graphics.png)

# Facebook #

Facebook provides [explicit instructions] about required sizes for page profile and cover photo. Link to your product will be shared on Facebook, so you also need to provide [Open Graph] markup specifying image used for share preview. Facebook also provides recommendation about their [dimensions](https://developers.facebook.com/docs/sharing/best-practices#images). You can try out, how your share will look like with [sharing debugger](https://developers.facebook.com/tools/debug/).

* Profile photo: 170x170 pixels
* Cover photo: 851x315 pixels (at least 399x150 pixels)
* Shareble image: 1200x630 pixels (at least 600x315, minimum 200x200 pixels); ratio: 1.91:1; less than 8MB

# Twitter #

Twitter also provides [instructions](https://support.twitter.com/articles/127871) for customizing profile. For twitter two images are needed - head and profile photo. Twitter also provides it's own markup for controlling appearance of shared content. The most common ones are [summary card]((https://dev.twitter.com/cards/types/summary)) and [summary card with large image](https://dev.twitter.com/cards/types/summary-large-image). You can try out, how it will look like with [card validator](https://cards-dev.twitter.com/validator).

* Header photo: 1500x500 pixels; doesn't support animated GIF
* Profile photo: 400x400 pixels; doesn't support animated GIF
* Summary card: 144x144 to 4096x4096 pixels; ratio 1:1; less than 5MB; first frame from GIF is used
* Summary card with large image: 300x157 to 4096x4096 pixels; ratio: 2:1; less than 5MB; first frame from GIF is used

# Product Hunt #

Product Hunt has recommendation about image sizes displayed during submission. It's possible to include thumbnail and screenshots.

* Thumbnail: 600x600 px or more, it can be animated gif, less than 3MB

# Other #

Do you know some other social network which requires specific graphics dimensions? Please, let me know in comments.

[explicit instructions]: https://www.facebook.com/help/www/125379114252045
[Open Graph]: https://developers.facebook.com/docs/sharing/webmasters#markup
