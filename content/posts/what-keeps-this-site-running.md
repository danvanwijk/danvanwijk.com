---
date: 2020-09-26
title: What keeps this site running
subtitle: A brief look at the technology behind this static site.
feature: images/posts/powered_by_aws.png
caption: "Amazon Web Services, the "Powered by AWS" logo are trademarks of Amazon.com, Inc. or its affiliates in the United States and/or other countries.
---

My main requirement for this site is that it must be static and easy to manage (i.e post new content). I ventured into the world of static site generators a few years back and the tool that stood out to me then was [Hugo](https://gohugo.io/). In recent years, one that has become very popular is [Gatsby](https://www.gatsbyjs.com/). It's on my list of stuff to dig deeper into, because it definitely looks interesting. For my simple needs though, I felt Hugo was the perfect fit right now.

***

## Hugo
Without trailing into details about Hugo and how it works I'll describe how I've divided this site into 3 different content types - pages, posts and journal entries.
* **Pages** are regular pages such as About and Contact. These are rarely changed.
* **Posts** are pages such as this one you are reading now, touching a specific subject. I intend to add new posts regularly.
* **Journal** are pages I add daily, i.e journal entries. Just things that are on my mind. Some are longer, some are shorter. Many are related to running :)

You can see these different pages on [GitHub](https://github.com/danvanwijk/danvanwijk.com/tree/master/content).

### Cost
Free

## GitHub
I'm using a public [GitHub repository](https://github.com/danvanwijk/danvanwijk.com) to store all files.

### Actions
GitHub has a neatly integrated CI/CD tool called Actions. You can use this to setup automated workflows for specific events in your repository, such as when you push a commit or create a pull request.

I'm using a [basic workflow](https://github.com/danvanwijk/danvanwijk.com/actions) to build this site with Hugo, publish it to S3 and then clear any cached files from CloudFront - the CDN used to deliver the site to you.

### Cost
Free

## Hosting
The site runs on [AWS](https://aws.amazon.com/), using 4 of their products:
* **S3** hosts all files, i.e. HTML, CSS, JS, images etc. - the static files built by Hugo.
* **CloudFront** CDN used to speed up delivery of the site. CloudFront connects directly to S3 to get the files, then caches them around the globe.
* **ACM** manages the SSL/TLS certificate so the site can be delivered securely with HTTPS. This is a free product.
* **Route 53** houses the DNS records for the domain.

### Cost
~$1 / month - the varying factor is simply amount of traffic to the site.

***

## Server Management / Patches / Headaches
None!

## Overall Cost
~$1 / month
