This tutorial explains how to implement OSLC consumers and providers by examining realistic use cases and showing how to implement OSLC specifications with lots of examples and working code. It is organized into the following parts:

1. This introduction
2. [__A brief overview of OSLC__](http://open-services.net/resources/tutorials/integrating-products-with-oslc/overview-of-oslc/)
3. [**Downloading and starting the sample applications**](http://open-services.net/resources/tutorials/integrating-products-with-oslc/running-the-examples/)
3. [**Part 1**, turning Bugzilla into a provider of the Change Management OSLC specification](http://open-services.net/resources/tutorials/integrating-products-with-oslc/implementing-an-oslc-provider/). We'll walk through the architecture of the integration, create OSLC catalogs and representations, provide delegated UIs, and allow you to create Bugzilla bugs programmatically.
4. [**Part 2**, turning a home-grown application into a consumer of the Change Management OSLC specification](http://open-services.rtp.raleigh.ibm.com/resources/tutorials/integrating-products-with-oslc/integrating-with-an-oslc-provider/) that works with the Bugzilla adapter from Part 1. We'll implement links to Bugzilla bugs, UI previews, delegated UIs, and automated bug creation.


## Audience

This tutorial is for people who will be writing code to implement OSLC consumers and providers; we assume the following about you:

+ You understand the basics of software development, web architecture, HTTP, [linked data](http://youtu.be/40mjwqGEKBU), and [RDF](http://www.youtube.com/watch?v=Nk9TOx1sBUk&feature=share&list=PLpqpu1CS6Rj4dRKWX1UICKseBq_20nk6k)
+ You want to learn more about OSLC
+ You can follow examples in XML, JSON, HTML, and JavaScript
+ You can understand server-side programming languages, particularly in Java and JSP (see below)
+ You want to learn more about how [Eclipse Lyo](http://www.eclipse.org/lyo/) can help you more quickly develop OSLC-driven integrations

<div class="notice">
  <div class="header">
    <h3 class="title">On the choice of server-side programming language</h3>
  </div>  
  <div class="body">
    Although our sample applications use Java and JSP, many of the methods of implementing OSLC are the same regardless of your choice of server-side programming-language. Later versions of this document might expand to other languages and platforms. OSLC is a community effort and we'd love your help in adding examples in different programming languages to this tutorial (or other material) to help those on other platforms such as Perl, PHP, Python, Ruby, or .Net.  
  </div>
</div>

## The Sample applications

You can follow along with the OSLC Tutorial by using the following software:

+ Bugzilla: a common open-source defect tracking application. You can use [the public Bugzilla Landfill](http://landfill.bugzilla.org/) site if you do not want to set up your own Bugzilla application.
+ OSLC4J Bugzilla adapter: a full-featured adapter that presents Bugzilla bugs as OSLC Change Management v2 resources. In our examples, we assume the Bugzilla adapter is running at [`http://localhost:8080/OSLC4JBugzilla`](http://localhost:8080/OSLC4JBugzilla)
+ NinaCRM: A simple, fictional Customer Relationship Management (CRM) system that hosts OSLC UI Preview and OSLC Delegated UI examples, implemented as a Java EE web application. In our examples, we assume that NinaCRM is running at [`http://localhost:8181/ninacrm`](http://localhost:8181/ninacrm)
+ Poster browser plugin (for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/poster/) or [Chrome](https://chrome.google.com/webstore/detail/chrome-poster/cdjfedloinmbppobahmonnjigpmlajcd)): we will browse and manipulate OSLC resources with this plugin that makes it easy to issue HTTP requests and set custom headers. An alternative for Firefox is [RESTClient](https://addons.mozilla.org/en-us/firefox/addon/restclient/).

See our section about [downloading, building, and starting the NinaCRM and OSLC4J Bugzilla applications](http://open-services.net/resources/tutorials/integrating-products-with-oslc/running-the-examples/).