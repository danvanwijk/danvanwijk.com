---
date: 2020-09-26
title: What keeps this site running
subtitle: A brief look at the technology behind this static site.
feature: images/posts/powered-by-aws.jpeg
caption: Amazon Web Services, the "Powered by AWS" logo are trademarks of Amazon.com, Inc. or its affiliates in the United States and/or other countries.
---

My main requirement for this site is that it must be static and easy to manage (i.e post new content). I ventured into the world of static site generators a few years back and the tool that stood out to me then was [Hugo](https://gohugo.io/). In recent years, one that has become very popular is [Gatsby](https://www.gatsbyjs.com/). It's on my list of stuff to dig deeper into, because it definitely looks interesting. For my simple needs though, I felt Hugo was the perfect fit right now.

***

## Content
I'll start off with a short explanation of how I've divided this site into 3 different content types - pages, posts and journal entries.
* **Pages** are regular pages such as About and Contact. These are rarely changed.
* **Posts** are pages such as this one you are reading now, touching a specific subject. I intend to add new posts regularly.
* **Journal** are pages I add daily, i.e journal entries. Just things that are on my mind. Some are longer, some are shorter. Many are related to running :)

You can see these different pages on [GitHub](https://github.com/danvanwijk/danvanwijk.com/tree/master/content).

## Hugo
Hugo is a CLI tool written in Go. It's not necessary to use on a day-to-day basis, e.g. when creating content, but depending on the size and complexity of your site it can definitely help as it allows you to easily start off new content based on templates. Of course you need to use it later when actually building your site into the final static files.

For my part I'm just creating new content using GitHub's online interface. Not the best writing experience but it works - and it enables me to easily post new journal entries from my phone.

### Getting Started
Hugo has good documentation that will help you understand all aspects of it. To get started you can have a look [here](https://gohugo.io/getting-started/quick-start/).

### Cost
Free

## GitHub
I'm using a public [GitHub repository](https://github.com/danvanwijk/danvanwijk.com) to store all files.

### Actions
GitHub has a neatly integrated CI/CD tool called Actions. You can use this to setup automated workflows for specific events in your repository, such as when you push a commit or create a pull request.

I'm using a [basic workflow](https://github.com/danvanwijk/danvanwijk.com/blob/master/.github/workflows/main.yml) to build this site with Hugo, publish it to S3 and then clear any cached files from CloudFront - the CDN used to deliver the site to you.

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
