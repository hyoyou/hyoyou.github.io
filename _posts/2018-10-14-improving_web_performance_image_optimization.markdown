---
layout: post
title:      "Improving Web Performance: Image Optimization"
date:       2018-10-14 16:40:06 +0000
permalink:  improving_web_performance_image_optimization
---

Have you ever navigated away from a web page because images were taking *forever* to load?

Images are easily one of the most downloaded bytes when visiting a web page and also take a good amount of visual space. Therefore, image optimization can yield a big performance improvement.

## Is the Image Necessary?
Try to weigh whether the image is absolutely essentially to deliver what you're after. Can it be replaced with CSS effects or CSS animations instead? What about web fonts?

## If so, Optimize
By optimize, what it means is to reduce the image size without sacrificing too much quality. You can either open up an image editor and decrease the size of the image files or use a "Save for Web" command in the case that you are using Adobe Photoshop. A good rule of thumb is to try and keep the file sizes to below 70kb.

Reduce the file size by compressing and removing all the unnecessary metadata associated with it (without sacrificing quality, of course!). 

Make sure you are using the correct image dimensions, ie. loading an image that is 800px by 1200px when the container only fits 200px by 300px.

## Choose the Right File Type
GIF: Lower quality than JPEG/JPG, but support animation.

JPEG/JPG: Can be compressed a good amount, and results in decent quality for a lower file size.

PNG: Support many more colors, but file sizes can get very big if not careful.

Below is a handy flow chart to help decide which file type may suit you best.

![Flow Chart](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/images/format-tree.png)

## Use Progressive JPEG
Instead of loading an image from top to bottom, known as baseline loading pattern, a progressive loading pattern will load a lower resolution image first, then improve quality as the page loads.

![Baseline to Progressive](https://cdn-images-1.medium.com/max/1600/1*Ge5BVVt8lzpsVnqn83xH5Q.jpeg)

## Consider Using a CDN
Hosting your image on a Content Delivery Network, or CDN, will use the server geographically closer to the user, which will result in faster response time.

Some popular CDNs are Cloudfare, Microsoft Azure CDN, and Amazon CloudFront. 


