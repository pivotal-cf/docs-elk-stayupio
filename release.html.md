---
title: ELK for Pivotal Cloud Foundry&reg;
---

Release notes for [ELK for Pivotal Cloud Foundry](https://network.pivotal.io/products/elk)
### 0.5.0.beta.5
**Release Date: 21st Sept 2015**

### Overview

Auto-purge old logs, remove "first install" config steps, UAA Audit dashboard, Multiline exceptions, experimental features for forwarding selected logs and monitoring BOSH VM `load/cpu/mem/disk %` stats.  Only supports Ops Man 1.5+

### Targets:
* Ops Manager 1.5.x
* Elastic Runtime 1.5.x

### Supports
* RabbitMQ for PCF 1.4.x
* Redis for Pivotal CF 1.4.x
* MySQL for [Pivotal Cloud Foundry&reg;](https://network.pivotal.io/products/pivotal-cf) (PCF) 1.5.x

### Changes
* NEW: Purge logs older than `Settings > Retention Period` days
<img width="1077" alt="screen shot 2015-09-14 at 13 18 11" src="https://cloud.githubusercontent.com/assets/227505/9849452/1c8f5854-5ae3-11e5-8e3d-88ae49ba43db.png">
* NEW: UAA Audit dashboard
<img width="1677" alt="screen shot 2015-09-14 at 12 27 18" src="https://cloud.githubusercontent.com/assets/227505/9849463/2de55a04-5ae3-11e5-94b5-2999a89e7856.png">
* NEW: Parse spring-cloud logs, combine exception stack traces into single log event and extracting spring-cloud-sleuth trace/span Ids.
<img width="1677" alt="screen shot 2015-09-14 at 12 28 03" src="https://cloud.githubusercontent.com/assets/227505/9849469/382e119a-5ae3-11e5-87ca-7304bcc07168.png">
* NEW: Install Elasticsearch management tool [KOPF](https://github.com/lmenezes/elasticsearch-kopf)
* NEW (EXPERIMENTAL): Forward (selected) enriched logs to external locations.
* NEW (EXPERIMENTAL): Separate Monitor microELK VM that displays BOSH Health Monitor VM stats (`load/cpu/mem/disk %`).
<img width="1668" alt="screen shot 2015-09-14 at 12 27 26" src="https://cloud.githubusercontent.com/assets/227505/9849474/42f00bc4-5ae3-11e5-9a74-1642da1e94ee.png">
* ENHANCEMENT: Configure Kibana indices and Elasticsearch mappings at install time
* ENHANCEMENT: Split Elasticsearch nodes into master and data nodes to prevent potential split brain issues.
* REMOVE:  Drop support for PCF 1.4

### Known Issues

* Monitor microELK VM and KOPF plugins do not have public network routes.  Operators will need to configure port forwarding or a SSH tunnel (eg, ssh into a machine within the private VLAN with `-L9200:10.0.16.47:9200 -L9201:10.0.16.51:9200 -L5601:10.0.16.51:5601`) to access these via their local browser.
* A race condition with default elasticsearch mapping rules sometimes occurs where the first index is created before the mapping rules are in place.  This manifests itself by hyphened app names (eg, eureka-server) appearing as 2 separate apps.  The fix is to delete the current index via `curl -X DELETE https://<elasticsearch_master_ip>:9200/logstash-<today's date in yyyy-mm-dd format>`.
* Kibana 4.2-snapshot (still) has a memory leak.

### 0.1.0.beta.3
**Release Date: 4th Aug 2015**

#### Overview

* Support for common data services (MySQL, RabbitMQ, and Redis)
* New enhanced Blue/Green deployment demo and screencast - https://github.com/stayup-io/cf-dicey-app
* A number of minor enhancements and bug fixes

#### Changes
* NEW Logo and name "ELK for Pivotal Cloud Foundry&reg;"
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
