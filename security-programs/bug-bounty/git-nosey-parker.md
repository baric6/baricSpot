# (git) Nosey Parker

Nosey Parker is a command-line tool that finds secrets and sensitive information in textual data. It is useful both for offensive and defensive security testing.

Key features:

* List itemIt supports scanning files, directories, and the entire history of Git repositories
* List itemIt uses regular expression matching with a set of 103 patterns chosen for high signal-to-noise based on experience and feedback from offensive security engagements
* List itemIt groups matches together that share the same secret, further emphasizing signal over noise
* List itemIt is fast: it can scan at hundreds of megabytes per second on a single core, and is able to scan 100GB of Linux kernel source history in less than 2 minutes on an older MacBook Pro

This open-source version of Nosey Parker is a re-implementation of the internal version that is regularly used in offensive security engagements at Praetorian. The internal version has additional capabilities for false positive suppression and an alternative machine learning-based detection engine. Read more in blog posts here and here.

Download

{% embed url="https://github.com/praetorian-inc/noseyparker" %}
