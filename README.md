Cloudera CDP Administrator Private Cloud Base
============================

This is a study guide I built while studying to get CDP Administrator  Private Cloud Base (CDP-2001) certification.  I wish it helps to someone interested while having a good time as I had.

This guide has all the documentation to achieve the CDP Administrator Private Cloude Base (CDP-2001) Certification, and at the same time it gives you the oportunity to learn all the tecnologies  to manage a CDP Cluster efficiency following best practices and recommendations from Cloudera.


Table of Contents
--------------------

**General Concepts**
-	[Cloudera Data Platform](#Cloudera-Data-Platform) 
-	[CDP Private Cloud Base](#CDP-Private-Cloud-Base)

**Specific topics** 
-	[Cloudera Manager](#Cloudera-Manager) 
-	[CDP Installation](#CDP-Installation)

**Legal**
-	[References](#References) 
-	[Disclaimer](#Disclaimer)
-	[License](#License)

Cloudera Data Platform
--------------------------

"Cloudera Data Platform (CDP) is a hybrid data platform designed for unmatched freedom to choose—any cloud, any analytics, any data.
CDP delivers faster and easier data management and data analytics for data anywhere, with optimal performance, scalability, and security.
With CDP you get the value of CDP Private Cloud and CDP Public Cloud for faster time to value and increased IT control." ([Cloudera](https://www.cloudera.com/products/cloudera-data-platform.html))

In this guide we are focusing in CDP Private Cloud only.  But in cloudera docs you can find information about Public Cloud.


CDP Private Cloud Base
--------------------------

It is an on-premises version of Cloudera Data Platform.  This product is the result of the Cloudera Enterprise Data Hub and Hortonworks Data Platform (HDP) combination along with some new features and improvements.  

When installing a CDP Private Cloud Base cluster, you install a single parcel called Cloudera Runtime that contains all of the components. For a complete list of the included components, see [Cloudera Runtime Component Versions](https://docs.cloudera.com/cdp-private-cloud-base/7.1.8/runtime-release-notes/topics/rt-pvc-runtime-component-versions.html).

In addition to the Cloudera Runtime components, CDP Private Cloud Base includes powerful tools to help manage, govern, and secure your cluster, like Apache Atlas, Apache Ranger, Apache Spark, Apache Zookeeper, etc.  CDP also includes a powerful tool to manage one or more clusters and their configuration, and also, monitor cluster performance of the clusters and their services. This tool is called Cloudera Manager.

Cloudera Manager
--------------------

As mentioned before, this tools is used to manage the clusters and their services, but you can also use Cloudera Manager to execute installations, upgrades, maintanance workflows, encryption, access controls, and replication.

### Before installing Cloudera Manager

**Pre-install consideratons**

-	Create a plan for storage space.  This plan should consider logs, configuration files and data to be stored in HDFS.
-	Configure network names.  This must be configure in DNS and /etc/hosts to a better performance.
-	Disabled firewall for each host in the cluster
-	Temporarily disable SE Linux
-	Enable NTP service.  Not configuring this step might cause several sincronization problems.
-	Configure parcel repositories.  This can be local or remote repositories, it depends if you have a temporal or permanent internet access.

CDP Installation
--------------------

**Configure repositories**

We are going to need to configure a local or public repository, and it will be saved at */etc/yum.repos.d/*.  Repositories for Cloudera Manager (CM) and CDP Runtime are necessary.  Also, we need to have an active subscription of our Operating System to update and install some dependencies.

**Install JDK**

The Java Development Kit (JDK) is a distribution of Java Technology by Oracle Corporation. It implements the Java Language Specification (JLS) and the Java Virtual Machine Specification (JVMS) and provides the Standard Edition (SE) of the Java Application Programming Interface (API). It is derivative of the community driven OpenJDK which Oracle stewards. It provides software for working with Java applications. [Wikipedia](https://en.wikipedia.org/wiki/Java_Development_Kit)

We are going to use Java applications during the installation, for this reason it is extreamly important to install JDK.  We can install it manually or let the Cloudera Manager Wizard install it for us.  In any case, it is importat to remember that we need to install it on all cluster hosts.

-	**Supported JDKs for CDP Private Cloud Base 7.1.x**
	-	OpenJDK 1.8
	-	OpenJDK 11
	-	Oracle JDK 1.8

-	**Requirements** 
	-	It must be 64 bits
	-	The same version on each host
	-	Must be installed at */usr/java/jdk-version*

**Enable Auto-TLS (Recommended)**

Transport Layer Security (TLS) is a cryptographic protocol designed to provide communications security over a computer network. [Wikipedia](https://en.wikipedia.org/wiki/Transport_Layer_Security)

This protocol gives you security over our cluster, e.g., avoid that malicious host installing a Cloudera Manager Agent and joining to our cluster.

We can configure TLS manually using your certificate authority or automatically with Auto-TLS (Recommended by Cloudera).

-	**Benefits of Auto-TLS**
	-	Auto-TLS automates the creation of an internal certificate authority (CA).
	-	All hosts and services will automatically have TLS configured and enabled.	

**Install Cloudera Manager**

Ones we have the repositories ready, we proceed to install CM.  Cloudera Manaager (CM) is installed on the Cloudera Manager Server host.  This is an example of the command using RHEL as OS.

> $ sudo yum install cloudera-manager-daemons cloudera-manager-agent cloudera-manager-server

[Back to top :arrow_up:](#table-of-contents)

References
-------------
[docs.cloudera.com](https://docs.cloudera.com) 

Disclaimer
------------
The author of this content cannot guarantee the validity of the information found here. Please make sure that you understand that the information provided here is being provided freely, and that no kind of agreement or contract is created between you and any persons associated with this content or project. The authors and contributors do not assume and hereby disclaim any liability to any party for any loss, damage, or disruption caused by errors or omissions in the information contained in, associated with, or linked from this content, whether such errors or omissions result from negligence, accident, or any other cause.

License
---------
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
