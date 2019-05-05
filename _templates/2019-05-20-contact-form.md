---
title: Contact Form
featured: images/pic03.jpg
layout: post
---

<p>A git commit brings changes to a git repository. Every time this happens, a Cloudwatch event (2) triggers the CodePipeline execution (3): this pipeline is composed of three stages.</p>
<p>It first gets the source code from the repository (4) defined in CodeCommit and puts it inside the artifact bucket (5);</p>
<p>then, the build stage gets (6) the source code and starts the jekylls build - using a ruby docker image managed by aws - and puts the artifacts back in the bucket (in another prefix).</p>
<p>Finally, it copies the artifacts to the content bucket.</p>
<p>After that, a lambda is triggered (9) to invalidate the CloudFront cache: CloudFront starts cache invalidation (10) by retrieving (11) and propagating the new content from the content bucket again to the edge location.</p>

<p>Every time a user B makes an https request to my new domain, Route53 resolves (13) the request the CloudFront CDN, that uses the certificate manager (14) to operate in ssl, and stores logs (15) about the requests done by the users.</p>