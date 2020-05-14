In order to run the tool you need to use java -jar command in your command line. The tool acceps two input parameters:
	- tag handling mode
	- input file path
	
Tag mode value can be either "-s" or "-a". It controls how the tool uses tags to group together opertaions:
"-s" - a single tag is used for grouping. Basically this means that from each operation we take first found tag and use it to decide to which group we should copy it, all other present tags are ignored;
"-a" - we take into account all present tags for each operation;
	
Example> java -jar SwaggerSplitter.jar -s trucare_2.0_swagger.json

The tool creates an emtpy folder "output_swaggers_<source_file_name>" near the provided input file and uses it to store all generated Swagger files (Please note that if such folder already exists the tool will fail).

Each generated swagger file has the following name format "<soruce_file_name>_tags_[<tag(s)_used_to_generate_this_file>].json.

Each generated swagger file will contain only operations that were selected by some tag and type definitions used in them.
