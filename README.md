# Iolara

[Iolara source repository at GitHub](https://github.com/concilium/iolara)  
[Iolara build and deploy chain at Semaphore](https://semaphoreci.com/concilium/iolara)  
[Iolara generated site content at AWS S3](https://console.aws.amazon.com/s3/home?region=us-west-2#&bucket=iolara.white-knight.org&prefix=)  
[Iolara website, long URL](http://iolara.white-knight.org.s3-website-us-west-2.amazonaws.com/)  
[Iolara website, aliased URL](http://iolara.white-knight.org/)  

Iolara is a [Dungeons & Dragons 5th edition](http://dnd.wizards.com/)
campaign world created by Mike Simpson in 2016, based on various ideas
("What if the hobbits were conquered and enslaved by the humans?", "What
if elves and dwarves suffered from internalized racism?") that had been
percolating over the prior couple of years.

It's also an experiment in using a static site generator, [Hugo](http://gohugo.io/),
along with various software-as-a-service components, to deliver website
content documenting the campaign world and the adventures therein,
i.e., campaign content as continuously deployed code flow.

The current authoring (i.e., development) path is:

*   Local authoring (mostly in [Markdown](https://daringfireball.net/projects/markdown/)
    format) in a Git local repository, using the
    [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/)
    method and naming conventions along with a couple of standard
    development tools (Eclipse, SourceTree).
    
*   Commits to the master branch (what Git Flow calls "finishing
    a release") are pushed to the corresponding build repository
    on GitHub.
    
*   The Semaphore service sees the new master branch commit, which
    triggers a build (via Hugo) of the website content.
    
*   Also in Semaphore, a successful build in turn triggers a 
    deployment hook that copies the generated website content to
    an AWS S3 bucket.
    
*   The S3 bucket has been
    [pre-configured as a static website source](http://docs.aws.amazon.com/ AmazonS3/latest/dev/WebsiteHosting.html);
    that, along with a CNAME record in DNS to simplify the website
    URL, should make the new "release" of the campaign content 
    show up at the appropriate URL.

As of April 2016, all of the above seems to be working, at least enough
to allow for development of the campaign content.  I'll undoubtedly be
tuning and tweaking the processing flow at the same time as I'm writing
up the campaign material.  If you have any questions, comments, suggestions,
etc., go ahead and use the GitHub issues functions to let me know.  If you
want to collaborate, let me know that as well -- expansion of a campaign
setting via GitHub pull requests, now there's something weird. :)

Mike
