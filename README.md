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
