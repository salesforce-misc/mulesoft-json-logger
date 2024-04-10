# JSON Logger - Mule 4

Drop-in replacement for default Mule Logger that outputs a JSON structure based on a predefined JSON schema.

## Why?

- Logs are as good as the logging practices applied by developers
- Not all developers think alike on what needs to be logged
- No tools to enforce proper logging standards
- Simple but essential logging best practices (e.g. tie multiple log entries to a single transaction by using a correlation id) are inconsistent and drastically impact troubleshooting capabilities
- The rise of Splunk, ELK and other log aggregation platforms is due to their ability to aggregate, understand and exploit data
- These platforms typically understand key=value pairs or JSON data structures. Only then, the full potential of these tools can be unlocked in the form of advanced dashboards and reports

For these reasons and based on previous customer experiences, Andres Ramirez created this generic Java SDK JSON Logger Connector.

It was updated by Mike Jakeman to run on Java 17 when using Mule 4.6+ and Open Sourced

## How?

As mentioned above, this is a Java SDK based Mule 4 connector. However, in order to maximize customization to each customer's requirements while avoiding steep Java SDK learning curves, you can easily modify the output JSON data structure as well as connector configuration by editing 2 simple JSON schemas provided under:
>/json-logger/src/main/resources/schema/

In a nutshell, by defining the output JSON schema as well as providing some additional SDK specific details (e.g. default values, default expressions, etc.), we can dynamically generate a module that aligns to those schemas.

## Installation

It is recommended that you fork this project into your customers code base and maintain there. This project is not maintained by MuleSoft or MuleSoft Professional Services. Please check these blogposts for more details:

PART 1: https://blogs.mulesoft.com/dev/anypoint-platform-dev/json-logging-in-mule-4-getting-the-most-out-of-your-logs/

PART 2: https://blogs.mulesoft.com/dev/api-dev/json-logging-in-mule-4/

Running the provided deployment script will deploy JSON Logger to your Organization's Exchange:
>e.g. ./deploy-to-exchange.sh <ANYPOINT_ORG_ID>

PS1. You can only use the _deploy.sh_ script once (unless you manually delete the previous asset from your exchange within 7 days of deployment or increase the version in the pom.xml) as you can't deploy the same version to Exchange

Rather than running the deploy script you can instead do:

1. Move into the json-logger folder
2. Update the pom's GroupId to the orgId you want to deploy the asset into.
3. Update the pom's version (you can start from 1.0.0 if you dont have other versions of the JSON Logger)
4. Ensure that the you have the name and credentials configured in your settings.xml to the exchange servers in the POM
5. Run mvn deploy

## Support disclaimer

In case you haven't noticed the type of license for the source code, this is provided as a side project under MIT open source license which means it won't be officially supported by MuleSoft as it is considered a custom connector.
