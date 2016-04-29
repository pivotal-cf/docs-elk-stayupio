---
title: stayUp.io ELK for Pivotal Cloud Foundry&reg;
owner: London Services
---

This is documentation for the [stayUp.io ELK for Pivotal Cloud Foundry](https://network.pivotal.io/products/elk) tile

## Product snapshot

<dl>
<dt>Current stayUp.io ELK for <a href="https://network.pivotal.io/products/pivotal-cf">Pivotal Cloud Foundry&reg;</a> Details</dt>
<dd><strong>Version</strong>: v1.0.0.rc1 </dd>
<dd><strong>Release Date</strong>: 13 Nov 2015</dd>
<dd><strong>Software component version</strong>: Elasticsearch 2.0.0, Logstash 1.5.4, Kibana 4.2.0, Redis 2.8.4</dd>
<dd><strong>Compatible Ops Manager Version(s)</strong>: 1.6.x, 1.5.x</dd>
<dd><strong>Compatible Elastic Runtime Version(s)</strong>:  1.6.x, 1.5.x</dd>
<dd><strong>vSphere support?</strong> Yes</dd>
<dd><strong>AWS support?</strong> Yes</dd>
</dl>

## Upgrading to the Latest Version

You must delete any previous beta versions before installing this release candidate.

<p class="note"><strong>Note</strong>: Uninstalling previous versions will delete all data and saved dashboard settings.</p>

From this point forward it will be possible to upgrade to the final GA releases.

## Install via Pivotal Operations Manager

To install ELK for Pivotal Cloud Foundry&reg;, follow the procedure for installing Pivotal Ops Manager tiles:

0. Download the product file from [Pivotal Network](https://network.pivotal.io/).
0. Upload the product file to your Ops Manager installation.
0. Click **Add** next to the uploaded product description in the Available Products view to add this product to your staging area.
0. PCF 1.5:  Elastic Runtime 1.5.x must have the binary buildpack installed -  [download](https://network.pivotal.io/products/buildpacks#/releases/349)

        cf create-buildpack binary_buildpack binary_buildpack-cached-v1.0.1.zip 8

0. Add `ELK-for-PCF` Tile version `1.0.0.rc1`.  Configure Availability zone.
0. Apply changes to install `ELK-for-PCF`
0.  Browse to `https://logs.<your-pcf-system-domain>`.  Login using a valid CF user (eg, the same credentials you would use to authenticate with the `cf` CLI client.

## Application Logs

Once you have installed the product, it automatically subscribes to your Elastic Runtime firehose and starts consuming all application logs.

## Elastic Runtime and Data Service Component Logs

You can configure the Elastic Runtime and other Data Service tiles to send their component logs to the ELK-for-PCF's syslog ingester.

0.  Navigate to `ELK-for-PCF` Tile > Status, and find `Ingestor for Syslog / RELP traffic` node's IP.
0.  Update `Pivotal Elastic Runtime` Tile
   0. PCF 1.5: Update `Pivotal Elastic Runtime` Tile > External endpoints using above IP, port `514` and protocol `TCP`.
   0. PCF 1.6: Update `Pivotal Elastic Runtime` Tile > System Logging endpoints using above IP, port `514` and protocol `TCP`.
0.  Update `RabbitMQ for PCF` Tile > Syslog using above IP, port `514`.
0.  Update `Redis for Pivotal Cloud Foundry` Tile > Syslog using above IP, port `514`.
0.  Apply Changes
0.  (Optional) Install `cf-app-events-logger` into the Elastic Runtime.  Clone https://github.com/stayup-io/cf-app-events-logger and follow instructions in README

## Kibana for CF Dashboards

A customized instance of the dashboarding application Kibana and some sample dashboards are installed at the following location:

```
https://logs.<system_domain>
```

When accessing Kibana, you will be prompted to log in with your Cloud Foundry UAA credentials. These are the same credentials used to access the App Manager console.

If your user is a member of the `system` organisation, you will be able to see all logs.

Otherwise, you will only be able to see application logs from applications deployed to `spaces` that you are a member of.

## Security
The following ports and ranges are used in this service:

* Destination port 443 for access to Kibana (via the Elastic Runtime `system domain` at `https://logs.<system_domain>` )
* Destination port 443 for access from the `Ingestor for Cloud Foundry Firehose` node to the Elastic Runtime Firehose
* Destination port 514 and 515 from the Elastic Runtime and Data Service network(s) to the  `Ingestor for Syslog / RELP traffic` node

## Examples

The following examples demonstrate common log analysis use-cases supported by the ELK for Pivotal Cloud Foundry&reg; tile:

* [Evidence based blue / green app deploys](https://github.com/stayup-io/cf-dicey-app)
* Cross microservice log tracing - TODO

## Feedback

Please provide any bugs, feature requests, or questions to [support@stayup.io](mailto:support@stayup.io).

## Further Reading

* [Official Elastic Elasticsearch 2.0.0 Documentation](https://www.elastic.co/guide/en/elasticsearch/reference/2.0/index.html)
* [Official Elastic Logstash Documentation](https://www.elastic.co/guide/en/logstash/current/index.html)
* [Official Elastic Kibana 4.2 Documentation](https://www.elastic.co/guide/en/kibana/4.2/index.html)
