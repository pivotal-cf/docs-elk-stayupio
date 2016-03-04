---
title: ELK for Pivotal Cloud Foundry&reg;
owner: London Services
---

# Resource requirements for ELK for Pivotal Cloud Foundry&reg;
These are the default resource and IP requirements for installing the tile:

| Component     | Job                                                         | Instances | CPU | Ram   | Ephemeral | Persistent | Static IP | Dynamic IP |
|---------------|-------------------------------------------------------------|-----------|-----|-------|-----------|------------|-----------|------------|
| Logstash      | Ingestor for Elastic Runtime's firehose                     | 1         | 2   | 1024  | 4096      | 0          | 1         | 0          |
| Logstash      | Ingestor for other tiles (syslog port: 514, RELP port: 515) | 1         | 2   | 1024  | 4096      | 0          | 1         | 0          |
| Logstash      | Ingestor for BOSH                                          | 1         | 2   | 1024  | 4096      | 0          | 1         | 0          |
| Redis         | Queue                                                       | 1         | 2   | 15000 | 4096      | 30000      | 0         | 1          |
| Elasticsearch | Elasticsearch master node(s)                                | 1         | 1   | 1024  | 2048      | 5000       | 1         | 0          |
| Elasticsearch | Elasticsearch data nodes                                    | 2         | 4   | 32000 | 4096      | 50000      | 0         | 2          |
| Logstash      | Log parser                                                  | 2         | 2   | 1024  | 2048      | 0          | 0         | 1          |
| All           | Monitor VM                                                  | 0         | 2   | 32000 | 4096      | 25000      | 1         | 0          |
