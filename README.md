Metric_fu Module
===
  Installs metric_fu and its prereqs and configures an apache vhost to serve its output
  
Requires:
---
   Module "apache" and its dependencies (specifically, a2enmod must be present)  
   Module "vcsrepo" (some vcsrepo provider must be present; if it is not git, git will be installed)  
   rubygems (for the gem provider) correctly installing binaries into path. Check this on Debian  
   Metric_fu can consume up 2-300MB of memory while running; 500MB at least is recommended  

Defined Type:
---
	metric_fu::codebase

Sample Usage:
---
	include metric_fu [or] class { "metric_fu" : site_alias => "metricsvhost.puppetlabs.lan" }  
	metric_fu::codebase { "puppet" : repo_url => "https://github.com/puppetlabs/puppet.git", repo_rev => "origin/master", repo_name => "puppet"}

Parameters in metric_fu::codebase 
---
-  $repo_url: the git url of the repository  
-  $repo_rev: what branch of that repository to run metrics on  

Action - metric_fu::codebase
---
   The subclass 'codebse' pulls down one codebase/repo and runs metric_fu every time it changes  
   Assumes a git repository, though other vcsrepos should work with minor changes  
   Class metric_fu to be included frst  


