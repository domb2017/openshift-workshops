---
layout: lab
title: JBoss Kitchen Sink
subtitle: xPaaS "Hello World" Example
html_title: xPaaS Quick Start
categories: [lab, ops]
next: workshop-lab-jboss.html
previous: workshop-lab-bluegreen.html
---

### Introduction

The quickstarts demonstrate JBoss EAP, Java EE 7 and a few additional technologies. They provide small, specific, working examples that can be used as a reference for your own project.

### Let's Execute the S2I xPaaS JBoss EAP Build Pipeline and Deploy

>Click "New Project"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-projects.png" width="500"/></p>

>Enter "jboss-xpaas" under name and click "Create"


<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-newproject.png" width="500"/></p>


>Type in "eap" in the box next to "Browse" and select "jboss-eap64-openshift:1.4"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-catalog.png" width="500"/></p>

<i class="fa fa-warning"></i> **If you don't enter a unique user name, then we will have conflicting routes between users.**

> Enter kitchensink-"your user name" under Name For example, if you are user1, please enter "kitchensink-user1" and so on.

> Click "Try it" and Git Repository URL should automatically be filled

> Click "Create"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-eapimage.png" width="500"/></p>

> Click "Continue to overview"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-appcreated.png" width="500"/></p>

> Click "View Log"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-appcreatedoverview.png" width="500"/></p>

>See the log start with cloning from the GIT repoistory

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-log1.png" width="500"/></p>

>The build will be successful once it says "Push Successful"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-log2.png" width="500"/></p>

>Navigate to Applications > Routes

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-navigateroute.png" width="500"/></p>


>Click the link under hostname.

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-route.png" width="500"/></p>

>This takes you to the JBoss EAP.  Feel free to add your name to the JBoss EAP Application.

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-welcomejboss.png" width="500"/></p>


### Let's Delete the Project

<i class="fa fa-warning"></i> **Please follow these directions to delete your project so we can free up resources for the next lab.**

>Find your jboss-xpaas project and click the trash can icon

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-navigateproject.png" width="500"/></p>

>Enter "jboss-xpaas" and click "delete"

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-deleteroute1.png" width="500"/></p>

>Confirm project has been deleted

<p><img alt="login to OSE" src="{{ site.baseurl }}/www-default/screenshots/ose-lab-xpaas-deleteconfirm.png" width="500"/></p>
