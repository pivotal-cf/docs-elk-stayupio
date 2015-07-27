---
title: Redis for Pivotal Cloud Foundry
---

# Resource requirements for Redis for PCF
These are the default resource and IP requirements for installing the tile
<table border="1" class="nice">
	<tr>
		<th>Product</th>
		<th>Resource</th>
		<th>Instances</th>
		<th>CPU</th>
		<th>Ram</th>
		<th>Ephemeral</th>
		<th>Persistent</th>
		<th>Static IP</th>
		<th>Dynamic IP</th>
	</tr>
	<tr>
 		<td>Redis</td>
	 	<td>Redis Broker</td>
	 	<td>1</td><td>2</td>
	 	<td>1024</td><td>4096</td>
	 	<td>1024</td>
	 	<td>1</td>
	 	<td>0</td>
 	</tr>
 	<tr>
 		<td>Redis</td>
 		<td>Dedicated Node</td>
 		<td>5</td>
 		<td>2</td>
 		<td>1024</td>
 		<td>4096</td>
 		<td>4096</td>
 		<td>1</td>
 		<td>0</td>
 	</tr>
 	<tr>
 		<td>Redis</td>
 		<td>Broker Registrar</td>
 		<td>1</td>
 		<td>1</td>
 		<td>1024</td>
 		<td>2048</td>
 		<td>0</td>
 		<td>0</td>
 		<td>1</td>
 	</tr>
	<tr>
		<td>Redis</td>
		<td>Broker De-Registrar</td>
		<td>1</td>
		<td>1</td>
		<td>1024</td>
		<td>2048</td>
		<td>0</td>
		<td>0</td>
		<td>1</td>
	</tr>
	<tr>
		<td>Redis</td>
		<td>Compliation</td>
		<td>2</td>
		<td>2</td>
		<td>1024</td>
		<td>4096</td>
		<td>0</td>
		<td>0</td>
		<td>1</td>
	</tr>
</table>

#### Notes:
* The `shared-vm` plan is on the `Redis Broker` resource
* The `dedicated-vm` plan is on the `Dedicatd Node` resource