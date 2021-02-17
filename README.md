# Alvearie Health Patterns NiFi Flows
The purpose of this Github repository is to deliver the public NiFi flows created under the [health-patterns](https://github.com/Alvearie/health-patterns) project.

The health patterns NiFi flows are developed to support or implement the various clinical data integration use cases, and are stored here as a way to facilitate delivery to users.

A consumer of the flows here can setup a [NiFi Registry](https://nifi.apache.org/registry.html) with a _Git flow persistence provider_ pointing at this repository and load the NiFi flows stored here into their own [NiFi](https://nifi.apache.org/registry.html) instances.

**Important:** This repository should not be interacted with other than through a NiFi Registry.

## Setup

In order to setup a NiFi Registry backed by this repository, follow the instructions below:

1. In your NiFi Registry home go to the `./conf` folder and open the `providers.xml` file
2. Comment out the default `FileSystemFlowPersistenceProvider` entry
3. Uncomment the `GitFlowPersistenceProvider` entry and configure it as follows:
```xml
    <flowPersistenceProvider>
        <class>org.apache.nifi.registry.provider.flow.git.GitFlowPersistenceProvider</class>
        <property name="Flow Storage Directory">./nifi-flows</property>
        <property name="Remote To Push"></property>
        <property name="Remote Access User"></property>
        <property name="Remote Access Password"></property>
        <property name="Remote Clone Repository">https://github.com/Alvearie/health-patterns-nifi-flows.git</property>
    </flowPersistenceProvider>
```
4. Start your NiFi Registry
