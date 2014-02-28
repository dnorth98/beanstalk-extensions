beanstalk-extensions
====================

I've written quite a few extensions for AWS Elastic Beanstalk.  They are SUPER extensibe and very powerful but some of the customizations are not well documented and not obvious.  So, I've "annonomized" the ones I've created and posted them here in the hopes they may benefit others.

01_aws_resources.config
   This extension shows how to customize existing beanstalk resources (load balancer, security group) and add a new resources (SQS queue).  It also shows a technique to get the auto-generated queue name onto the instance.
   
   For the load balancer, we have a beanstalk parameter set called HTTP_SERVER_PORT which we are then substituting into the security group rules.
