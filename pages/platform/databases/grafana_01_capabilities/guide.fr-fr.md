---
title: Grafana - Capacités et limitations (EN)
slug: grafana/capabilities
excerpt: Discover the capabilities and limitations of Public Cloud Databases for Grafana
section: Grafana - Guides
order: 010
routes:
    canonical: 'https://docs.ovh.com/gb/en/publiccloud/databases/grafana/capabilities/'
---

**Last updated January 19th, 2023**

## Objective

This page provides the technical capabilities and limitations of the Public Cloud Databases for Grafana offer.

We continuously improve our offers. You can follow and submit ideas to add to our roadmap at <https://github.com/ovh/public-cloud-roadmap/projects/2>.

## Capabilities and limitations

### Supported regions and multi-AZ

The Public Cloud Databases offer is available in the following regions:

- `BHS` (Beauharnois, Canada)
- `DE` (Frankfurt, Germany)
- `GRA` (Gravelines, France)
- `SBG` (Strasbourg, France)
- `UK` (London, United Kingdom)
- `WAW` (Warsaw, Poland)

Grafana nodes have to be in the same region. Multi-AZ is currently not supported.

### Grafana versions

The Public Cloud Databases offer supports the following Grafana versions:

- Grafana 8.3

You can follow the Grafana Release Cycle on their official page: <https://grafana.com/>.

### Grafana clients

You can use your browser to access your Grafana cluster.

### Plans

The only plan available is *Essential*.

Here is an overview of the *Essential* plan capabilities:

| Plan         | Number of nodes by default | Additional nodes |
| ------------ | -------------------------- | ---------------- |
| *Essential*  | 1                          | No               |

The *Essential* plan offer an automatic backup retention of 2 days. It supports public or private networks (vRack).

#### Nodes and replicas

- **Essential**: the cluster is delivered with 1 node.

#### License type

Grafana software is under the GNU Affero General Public License, a liberal open-source license.
More information on <https://raw.githubusercontent.com/grafana/grafana/main/LICENSE>.

### Hardware resources

Here are the node types you can choose from:

**Essential plans**

| Name    | Disk (GB) | Cores | Memory (GB) |
| ------- | --------- | ----- | ----------- |
| db1-4   | n/a       | 1     | 4           |
| db1-7   | n/a       | 2     | 7           |

### Features
#### Network
Grafana clusters are reachable through a random port, attributed during cluster creation. Once your cluster is in **RUNNING** status, the Service URI will display the port to use.

Public as well as private networking (vRack) can be used for all the offers.

Ingress and Egress traffic are included in the service plans and unmetered.

##### Private network considerations
Here are some considerations to take into account when using private network:

- Network ports are created in the private network of your choice. Thus, further operations on that network might be restricted - e.g. you won’t be able to delete the network if you didn’t stop the Public Cloud Databases services first.
- When connecting from outside subnet, Openstack IP gateway must be enabled in the subnet use for the Database service. The customer is responsible for any other custom network setup.


#### Advanced parameters

We do not currently support Grafana advanced parameters.

#### Backups

*Essential* plan clusters are automatically backed up daily during their backup window. Backup retention is 1 day.

#### Logs and metrics

Logs and metrics are available via the OVHcloud Public Cloud Control Panel.
As of today, you can't export logs and metrics, nor plug them into a remote tool.

- **Logs retention**: 1000 lines of logs
- **Metrics retention**: 1 calendar month

Please note that if the database instance is deleted, logs and metrics are also automatically deleted.

#### Users and roles

Creation of users must be done through the Grafana Web interface.

Only one user is created by default and its name is `admin`. You must reset its password to connect for the first time to the Grafana web interface.

## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have.

Are you on Discord? Connect to our channel at <https://discord.gg/ovhcloud> and interact directly with the team that builds our databases service!
