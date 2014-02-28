beanstalk-extensions
====================

I've written quite a few extensions for AWS Elastic Beanstalk.  They are SUPER extensibe and very powerful but some of the customizations are not well documented and not obvious.  So, I've "annonomized" the ones I've created and posted them here in the hopes they may benefit others.

01_aws_resources.config

   This extension shows how to customize existing beanstalk resources (load balancer, security group) and add a new resources (SQS queue).  It also shows a technique to get the auto-generated queue name onto the instance.  For the load balancer, we have a beanstalk parameter set called HTTP_SERVER_PORT which we are then substituting into the security group rules.

01_install_s3get.config

   This extension installs a handy python script I found which allows GET of content from a private S3 bucket.  The nice thing is that using instance roles, it requires no access keys and the role can be used to lock down access to only the bucket you need.  It does nothing more than add the script/tool to an instance.
   
01_install_updateroute53.config

   Installs a small utility that allows updating of 'this' instance's IP address into Route53.  Takes a domain suffix as an argument (which in our case, we pass as a beanstalk paramter and then pass into the script later).  Uses instance roles for access control.

01_papertrail.config

   Extension to configure the instance to send logs to papertrail (http://papertrailapp.com).  I based this on the article in the papertrail knowledgebase BUT I modified it to use a 'hostname' of the beanstalk environment name concatenated with the instance ID.  Makes finding and searching the logs very easy.

01_tag_resources.config

   Small extension which shows how to tag instances with custom tags.

05_set_hostname.config

   We had a requirement to have a hostname that we control registered in DNS.  This extension sets the hostname to <beanstalk env name>-<instanceID>.  It then adds on the domain suffix passed as beanstalk parameter called DOMAIN_SUFFIX.  Finally, it calls the updateroute53 script installed by the 01_install_updateroute53 extension to update DNS.
   
   
10_cloudwatch.config

   Generates custom metrics for sending to cloudwatch.  In this example, the metric is a count of the number of processes running matching a particular pattern but it could be anything.  We tag them against the instance ID so we can see the metrics next to the standard instance metrics like disk space and CPU.
   
   
