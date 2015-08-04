---
title: ELK for Pivotal Cloud Foundry
---

Release notes for [ELK for Pivotal Cloud Foundry](https://network.pivotal.io/products/elk)

### 0.1.0.beta.3
**Release Date: 4th Aug 2015**

#### Overview

* Support for common data services (MySQL, RabbitMQ, and Redis)
* New enhanced Blue/Green deployment demo and screencast - https://github.com/stayup-io/cf-dicey-app
* A number of minor enhancements and bug fixes

#### Changes
* NEW Logo and name "ELK for Pivotal Cloud Foundry"
* NEW Overview dashboard
* NEW MySQL, RabbitMQ, Redis data service dashboards
* UPGRADE required stemcell to 3026
* UPGRADE Kibana to 4.2-snapshot
* UPGRADE Elasticsearch to 1.6.0
* UPGRADE Logstash to 1.5.2
* FIX Kibana is now deployed to PCF system domain
* FIX Kibana OAuth2 client_secret updated on re-installation
* FIX Force use of HTTPS during login process

### Known Issues

* Kibana 4.2-snapshot has memory leak
