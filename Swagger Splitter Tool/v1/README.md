# Swagger Splitter Tool

## Why do we need this tool

Often times, the swagger providing API definition for a specific API set tends to get huge. We have seen swagger that have 500+ paths, 700+ objects and filesize 5+ MB. With this tool, you would be able to split the swagger based on tags. Each of the tags will let create a separate swagger file with have less paths, objects and a reduced size. These swagger files can then be used as per your requirements.

## Where can we use this tool

As this utility lets you split one **huge** swagger files into many **smaller, tag-based** swagger files, it can be used wherever you use the swagger to create a Client to third-party system.

There is one such way to create an API Client in [Cloud Application Integration Service](https://www.informatica.com/products/cloud-integration/cloud-application-integration.html) (Cloud Service available as part of [Informatica Intelligent Cloud Services](https://www.informatica.com/products/cloud-integration.html), Informatica's iPaas). It is called Service Connector and it let's you create connectivity to a third-party system on the fly using importing swagger or a WSDL file (Obviously, you can also create an API Client by defining actions manually).

In case you want to import a swagger to create a Service Connector, it may be cumbersome if the swagger is huge. You can then split the swagger using this tool and create multiple Service Connectors. By the way, we have already published a registry of pre-created Service Connectors in [Cloud Application Integration Community](https://network.informatica.com/community/informatica-network/products/cloud-integration/cloud-application-integration/). You can access them [here](https://network.informatica.com/community/informatica-network/products/cloud-integration/cloud-application-integration/blog/2018/10/16/registry-of-service-connectors-your-gateway-to-building-composite-api-using-cloud-application-integration)

## How do we use this tool

In order to run the tool you need to use java -jar command in your command line. The tool accepts two input parameters:
- tag handling mode
- input file path
	
Tag mode value can be either "-s" or "-a". It controls how the tool uses tags to group together operations.
- If you use "-s", a single tag is used for grouping. This means that from each operation, we take first tag found and use it to decide to which group we should copy it, all other present tags are ignored;
- If you use "-a", we take into account all present tags for each operation;
	
Example> java -jar SwaggerSplitter.jar -s swagger.json

The tool also creates an emtpy folder "output_swaggers_<source_file_name>" in the same folder as the input JSON file and uses it to store all generated Swagger files. Please note that if such folder already exists, the tool will fail.

Each generated swagger file is created with the filename as "<source_file_name>_tags_\[<tag(s)_used_to_generate_this_file>\].json.
Each generated swagger file will contain only operations that were selected by some tag and type definitions used in them.



