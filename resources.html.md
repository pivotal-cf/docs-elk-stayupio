---
title: ELK for Pivotal Cloud Foundry
---

# Resource requirements for ELK for Pivotal Cloud Foundry
These are the default resource and IP requirements for installing the tile:
<table border="1" class="nice">
	<tr>
		<th>Component</th>
		<th>Job</th>
		<th>Instances</th>
		<th>CPU</th>
		<th>Ram</th>
		<th>Ephemeral</th>
		<th>Persistent</th>
		<th>Static IP</th>
		<th>Dynamic IP</th>
	</tr>
	<tr>
 		<td>Logstash with firehose adapter</td>
	 	<td>Ingestor for Cloud Foundry Firehose</td>
	 	<td>1</td>
	 	<td>2</td>
	 	<td>1024</td>
	 	<td>4096</td>
	 	<td>0</td>
	 	<td>1</td>
	 	<td>0</td>
 	</tr>
 	<tr>
 		<td>Logstash</td>
	 	<td>Ingestor for Syslog / RELP traffic</td>
	 	<td>1</td>
	 	<td>2</td>
	 	<td>1024</td>
	 	<td>4096</td>
	 	<td>0</td>
	 	<td>1</td>
	 	<td>0</td>
 	</tr>
 	<tr>
 		<td>Redis</td>
 		<td>Queue</td>
 		<td>1</td>
 		<td>2</td>
 		<td>15000</td>
 		<td>4096</td>
 		<td>30000</td>
 		<td>0</td>
 		<td>1</td>
 	</tr>
 	<tr>
 		<td>Elasticsearch</td>
 		<td>Elasticsearch data nodes</td>
 		<td>2</td>
 		<td>4</td>
 		<td>32000</td>
 		<td>4096</td>
 		<td>50000</td>
 		<td>0</td>
 		<td></td>
 	</tr>
	<tr>
		<td>Kibana</td>
		<td>API and Admin Kibana</td>
		<td>1</td>
		<td>1</td>
		<td>1024</td>
		<td>2048</td>
		<td>0</td>
		<td>1</td>
		<td>0</td>
	</tr>
	<tr>
		<td>Logstash</td>
		<td>Log parser</td>
		<td>2<td>
		<td>2</td>
		<td>1024</td>
		<td>2048</td>
		<td>0</td>
		<td>0</td>
		<td>1</td>
	</tr>

</table>
