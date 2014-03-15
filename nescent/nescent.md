# [phylobabble](http://phylobabble.org): a moden discussion forum for phylogenetics


I have started [phylobabble.org](http://phylobabble.org), a phylogenetics discussion forum for the discussion of research and best practice.
I have done so with my own work and funding from unrelated research budgets.
This initial implementation has already shown that it will be a useful tool for phylogenetics researchers.
In order to make phylobabble into a stable resource that will be able to persist into the future, I would like to optimize compute resources as well as establish upgrade and backup procedures.

Contact: Erick Matsen ([matsen@fhcrc.org](mailto:matsen@fhcrc.org))

## Background

It is a long-term goal of mine to expand community involvement and participation in phylogenetics.
This was the motivation for starting [phyloseminar.org](http://phyloseminar.org), which is a freely accessible series of talks that are accessible online.
Over the last four and a half years, phyloseminar has grown tremendously, and has hosted seminars from a wide variety of speakers on a broad array of topics which range from practical to highly theoretical.
In this way it has already succeeded in making the material typically only available at a conference to a wider audience.

It is commonly acknowledged that one of the most valuable aspects of conferences is the informal discourse that happens between sessions.
Indeed, I often hear something like "I was talking to David Hillis at Evolution two years ago, and he said that..." in the process of conversation.
I have often wondered how one might enable that sort of discourse electronically.
Electronic discourse has the advantages that it forms a permanent record (and thus can be authoritatively cited), it does not have any beginning or ending dates, requires no travel, and is accessible to the general public.

Social media does fill some of these roles.
Twitter has become popular among scientists, and is wonderful for sharing papers and short thoughts.
However, by its nature it does not work for extended discussion.
Google Plus and Facebook are also useful tools, but have gotten less traction in the scientific community.

I believe that the [Discourse](http://discourse.org) web application forms a perfect solution to enable in-depth discussion of phylogenetics issues.
It was started by Jeff Atwood, who was one of the two founders of the popular set of StackExchange collection of websites, including [Stack Overflow](http://stackoverflow.com/) and [Server Fault](http://serverfault.com/).
Although it is structurally similar to a simple mailing list, it provides a number of features that make it significantly better than a forum such as Google Groups.
In addition to being attractive and easy to use, it also automatically provides protection against spam and non-constructive (a.k.a. "trolling") behavior.
It allows embedding of images,
[YouTube videos](http://phylobabble.org/t/mike-steels-2011-predictions-how-is-he-doing-so-far/48/5),
[SlideShare presentations](http://phylobabble.org/t/concept-taxonomy/182),
and other rich media.
It also allows easy sharing by social media.

We have seen very rapid growth since beginning the website.
By today, March 11th, it has over a hundred *registered* users who had visited in the past 6 days.
We have had over one thousand unique visitors, and over 53% of our visits are return visits.
Our first public announcement was only two weeks ago, and we continue to acquire new visitors and new registered users at a solid pace.
We have had posts from many leading individuals in phylogenetics, such as Roderic Page, Alexei Drummond, and Mike Steel.
I am most proud of how it has enabled communication between scientists, reducing duplicate effort and informing people of the most recent developments.
It has brought together postdocs, sequence database administrators, and senior researchers.


## Project Description (including use cases)

I started the phylobabble website with a "let's see how it goes" mind-set, to see if there was sufficient interest to motivate more sophisticated development.
I am now confident of the potential for phylobabble.
We have reached a critical mass of consistent participants such that it will continue to be a way for them to converse into the future, and these conversations will attract others.

So far I have done a lot of work myself and funded phylobabble through other research budgets.
In addition to doing set-up and the usual forum administration tasks, I have also done a substantial amount of system administration that is associated with keeping up a complex web application that has a variety of log in methods and emails users.
The site was launched using the [Bitnami](http://bitnami.com) platform.
As it has become popular, the website became slow, so I had to scale up to an [Medium M3](http://aws.amazon.com/ec2/instance-types/) EC2 instance.
I have backed up the web application sporadically.
I have also [added](https://github.com/dysania/onebox/pull/199/files) a feature to [make a summary of a paper based on its PubMed link](https://meta.discourse.org/t/oneboxes-for-pubmed-are-here/13294).
However, ironically, I have not had the time or to actually upgrade our instance to take advantage of this feature for phylobabble, although it works well on up to date Discourse instances such as [meta.discourse.org](http://meta.discourse.org).

It is clear to me that phylobabble will succeed if I commit to its continued development, and I would like to do so.
However, I need some resources to make that happen.
I would like to have some support for improving and maintaining it, as well as support to cover the hosting fees.


## Relevant or Related Projects

I started the [phyloseminar.org](http://phyloseminar.org) website to provide an international forum for the discussion of phylogenetics methodology disseminate information on phylogenetic best practice.
This is also something that I started with no budget and a lot of initial work, and have recently gotten support from the Society of Systematic Biologists.
There is a lot of opportunity for synergy between these two projects.

## Major Technical Considerations

### Find the best hosting platform for phylobabble and set it up
I have used Bitnami with good success thus far, but this may not be the optimal way forward in the long term.
For instance, it is not possible to use advanced features of Amazon Web Services such as [elastic load balancing](http://aws.amazon.com/elasticloadbalancing/) which would enable redundancy and allow us to decrease hosting cost.
Also, although it is easy to bring up an instance, it is not completely straightforward to upgrade the software, and I have had difficulties in modifying the way it runs.

Fortunately, there is now a [Docker](https://www.docker.io/) [image for Discourse](https://github.com/discourse/discourse_docker).
This should greatly simplify maintenance of phylobabble, although the Discourse Docker image, as well as Docker itself, is definitely still a [work in progress](http://samsaffron.com/archive/2013/11/07/discourse-in-a-docker-container).
Such an image should make it easy to keep up to date with Discourse releases, and to either use advanced features of Amazon Web Services or another lower-cost platform such as [Digital Ocean](https://www.digitalocean.com).


### Establish procedures for maintenance
Right now the system is backed up sporadically when I think of it, and have not kept up with improvements and bugfixes in the Discourse software.
It would be a tragedy to lose the interesting dialog that has happened even in this short interval, and the current site may have some vulnerabilities.
Thus I propose a regular maintenance schedule to make backups automatically and a regular schedule of upgrades.


## People and Organizations (either potential participants or experts that could be consulted for more information).

I invite you to reach out to anyone who has registered for the forum to get their opinion of it.

## What I would like
In a broad sense, I would like assistance with the computing costs associated with phylobabble as well as the systems administration tasks.
For the systems administration, I would be happy if either NESCent staff got directly involved (assuming they had the necessary expertise in deploying Rails apps on the cloud) or if NESCent provided funding for a programmer in my group to take this on.
There are several ways to proceed.

1. *Leave phylobabble in a structurally similar state and provide computing costs as well as a small amount of support to maintain it.*
This option would have phylobabble continue to be hosted through Bitnami.
I would then request about $1,200 a year for AWS fees, and about 8 days per year of programmer effort to back up the databases and keep the instance up to date.

2. *Move to a more flexible deployment scheme, which will require upfront investment but will be cheaper in the long run.*
The Discourse authors have committed to deployment with Docker, which allows deployment on many different platforms.
This will allow us to reduce computing costs by either using several Micro AWS instances through elastic load balancing, or thorough using a cheaper service such as Digital Ocean.
I think that we could reduce computing fees to under $600 a year.
I think that this would require a one-time effort of 15 days, and then 6 days per year after that.

I prefer the second plan, as it is independent of changes that may happen at Bitnami.
These changes could seriously impact us.
For example, in the month or so since I signed up for Bitnami it is no longer possible to sign up for a plan that allows Medium AWS instances to be run through their system.
I would not be surprised if they stopped allowing free use of this service tier even for users who had signed up previously.
This would substantially change phylobabble finances, as the cheapest plan that allows our current Medium instance is $49/month.

This project, as well as phyloseminar, do not appear fundable through traditional channels because they do not fit into any standard categories.
So far I have tried to attract funding for phylobabble from the Sloan Foundation (through Josh Greenberg) and Amazon (through Jamie Kinney) with no results.
In the past I have looked for mechanisms to support phyloseminar, without any results until the Society for Systematic Biologists stepped in and supported an initial improvement of phyloseminar as well as a small amount of continuing funding.

Phylobabble is inherently more expensive than phyloseminar because phylobabble requires a dynamic host, and is much more complex of a website than phyloseminar.
This dynamic hosting is much more expensive than a static site, and nontrivial resources are required to have reasonable response times.
Specifically, I ran phyloseminar on zero budget for years, but phylobabble will end as soon as I stop paying hosting fees.

Thus the participation of the center is greatly needed here, either for continuing support, for an initial burst of funding and/or effort to set us up for a more sustainable future, or for direction to where we might secure more long-term funding.
I would also appreciate any effort that NESCent could do to promote participation in phylobabble, and participation from NESCent staff and postdocs.
NESCent could also use its outreach experience to engage the broader public.
My experience with phyloseminar tells me that after the initial spike of interest, what will make phylobabble successful in the long term is to have a continual stream of high-quality content and a stable platform.

I hope NESCent will help enable greater communication among researchers and communication with the greater public through phylobabble.
In case it's not already clear, I'm in this for the long haul.

