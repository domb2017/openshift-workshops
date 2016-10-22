---
layout: lab
title: Blue-green Deployment with Jenkins
subtitle:
html_title: Blue/Green
categories: [lab, ops, blue, green]
---

## Blue/Green deployments
When implementing continuous delivery for your software, one very useful technique is called Blue/Green deployments.  It addresses the desire to minimize downtime during the release of a new version of an application to production.  Essentially, it involves running two production versions of your app side-by-side and then switching the routing from the last stable version to the new version once it is verified.  Using OpenShift, this can be very seamless because using containers we can easily and rapidly deploy a duplicate infrastructure to support alternate versions and modify routes as a service.  In this lab, we will walk through a simple Blue/Green Jenkins Pipeline with an simple web application on OpenShift.



### Let's Login

>Navigate to the URI provided by your instructor and log in with the user/password provided.

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-login.png" width="500"/></p>

>Select the Application Development Environment

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-projectlist.png" width="500"/></p>

### Let's Execute the S2I Build Pipeline and Deploy in Dev

>Navigate to Builds > Pipelines

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-navigatepipeline.png" width="500"/></p>

:information_source: Please note that the Pipeline feature is in Tech Preview for this release of OpenShift 3.3

>Click "Start Pipeline".  This will start the S2I build.

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-startpipeline.png" width="500"/></p>

>Notice the pipeline has started. Wait for the image to build and deploy to Dev

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-builddev.png" width="500"/></p>

>Navigate back to the overview and click the link for the bluegreen dev app in the top right

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-devoverview.png" width="500"/></p>

>View the newly deployed app

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-devapp.png" width="500"/></p>

<i class="fa fa-warning"></i> **Be sure that the Development build completes and the image is pushed into the repository before you approve a deployment into QA or Prod. If you approve into QA or Prod before the newly built image is pushed into the registry from Dev, you'll end up with a bit of a race condition where QA and Prod simply redeploy the now older image.**


### Let's Approve Promotion to QA

>Navigate to Builds > Pipeline and click "Input Requested"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-builddev.png" width="500"/></p>

>Log in to Jenkins with username: "admin" and password: "password"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-jenkinslogin.png" width="500"/></p>

>Click "Proceed"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-approveqa.png" width="500"/></p>

>Wait till your Pipeline shows "Deploy to QA" has been completed

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-deployqapipeline.png" width="500"/></p>

>Navigate to the Application QA Environment and click the link for the bluegreen qa app in the top right

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-qaoverview.png" width="500"/></p>

>View newly deployed app in QA

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-qaapp.png" width="500"/></p>


### Let's Approve Promotion to Production

>Navigate back to the Application Development Environment

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-devoverview.png" width="500"/></p>

>Navigate to Builds > Pipeline and click "Input Requested"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-deployqapipeline.png" width="500"/></p>

>Log in to Jenkins with username: "admin" and password: "password"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-jenkinslogin.png" width="500"/></p>

>Click "Proceed"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-approveprod.png" width="500"/></p>

>Wait till your Pipeline shows "Deploy to Production" has been completed

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-deployprodpipeline.png" width="500"/></p>

>Navigate to your Application Production Environment and click the link for the bluegreen qa app in the top right

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-prodoverview.png" width="500"/></p>

>View newly deployed app in Production

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-prodapp.png" width="500"/></p>


### Release a new version of our app and test it in the same environment

>Your Instructor will make a quick code change in the Git Repository for the app to go from Blue to Green.  Once the change is made, repeat the steps above to create a new S2I Build Pipeline changing your deployments in Dev, QA, and Production from Blue to Green

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-bluegreen-jekins-devappgreen.png" width="500"/></p>

## Summary
Pretty easy, right?

If you want to read more about Blue/Green check out [this post][2] with a longer description as well as links to additional resources.

[1]: https://github.com/VeerMuchandi/bluegreen
[2]: http://martinfowler.com/bliki/BlueGreenDeployment.html
