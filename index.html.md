---
title: ELK for Pivotal Cloud Foundry
---

This is documentation for the [ELK for Pivotal Cloud Foundry](https://network.pivotal.io/products/elk) tile.

## Product snapshot

<dl>
<dt>Current ELK for Pivotal Cloud Foundry Details</dt>
<dd><strong>Version</strong>: v1.0-beta2 </dd>
<dd><strong>Release Date</strong>: 28th July 2015</dd>
<dd><strong>Software component version</strong>: Elasticsearch 1.6.0, Logstash 1.5.2, Kibana 4.2-snapshot, Redis 2.8.4</dd>
<dd><strong>Compatible Ops Manager Version(s)</strong>: 1.5.x, 1.4.x</dd>
<dd><strong>Compatible Elastic Runtime Version(s)</strong>: 1.5.x, 1.4.x</dd>
<dd><strong>vSphere support?</strong> Yes</dd>
<dd><strong>AWS support?</strong> Yes</dd>
<dd><strong>OpenStack support?</strong> Coming soon</dd>
</dl>

## Upgrading to the Latest Version

While in beta, it is **not** possible to upgrade from previous versions. You must uninstall previous versions and then install this latest version.

<p class="note"><strong>Note</strong>: Uninstalling previous versions will delete all data and saved dashboard settings.</p>

## Install via Pivotal Operations Manager

To install ELK for Pivotal Cloud Foundry, follow the procedure for installing Pivotal Ops Manager tiles:

1. Download the product file from [Pivotal Network](https://network.pivotal.io/).
1. Upload the product file to your Ops Manager installation.
1. Click **Add** next to the uploaded product description in the Available Products view to add this product to your staging area.
1. Click the newly added tile to review any configurable options.
1. Click **Apply Changes** to install the service.

## Application Logs

Once you have installed the product, it automatically subscribes to your Elastic Runtime firehose and starts consuming all application logs.

## Elastic Runtime and Data Service Component Logs

You can configure the Elastic Runtime and other Data Service tiles to send their component logs to the ELK-for-PCF's syslog ingestor.

0. Navigate to ELK-for-PCF Tile > Status, and find the `Ingestor for Syslog / RELP traffic` node's IP.
0. Update Pivotal Elastic Runtime Tile > External endpoints using the above IP, port 515, and protocol RELP.
0. Update RabbitMQ for PCF Tile > Syslog using the above IP, port 514.
0. Update Redis for Pivotal Cloud Foundry Tile > Syslog using the above IP, port 514.
0. Click **Apply Changes** to install the service.

## Kibana for CF Dashboards

A customized instance of the dashboarding application Kibana and some sample dashboards are installed at the following location:

```
https://logs.<system_domain>
```

When accessing Kibana, you will be prompted to log in with your Cloud Foundry UAA credentials. These are the same credentials used to access the App Manager console.

<p class="note"><strong>Note</strong>: Currently, all authenticated users can see logs from all applications. Users will be restricted to only seeing logs from applications in spaces they are a member of in a later beta.</p>

## Security
The following ports and ranges are used in this service:

* Destination port 443 for access to Kibana (via the Elastic Runtime `system domain` at `https://logs.<system_domain>` )
* Destination port 443 for access from the `Ingestor for Cloud Foundry Firehose` node to the Elastic Runtime Firehose
* Destination port 514 and 515 from the Elastic Runtime and Data Service network(s) to the  `Ingestor for Syslog / RELP traffic` node
* Destination ports 9200 from the Elastic Runtime DEA network(s) to the API node.

## Examples

The following examples demonstrate common log analysis use-cases supported by the ELK for Pivotal Cloud Foundry tile:

* [Evidence based blue / green app deploys](https://github.com/stayup-io/cf-dicey-app)
* Cross microservice log tracing - TODO

## Feedback

Please provide any bugs, feature requests, or questions to [the Pivotal Cloud Foundry Feedback list](mailto:pivotal-cf-feedback@pivotal.io).

## Further Reading

* [Official Elastic Elasticsearch 1.6.0 Documentation](https://www.elastic.co/guide/en/elasticsearch/reference/1.6/index.html)
* [Official Elastic Logstash Documentation](https://www.elastic.co/guide/en/logstash/current/index.html)
* [Official Elastic Kibana 4.1 Documentation](https://www.elastic.co/guide/en/kibana/current/index.html)