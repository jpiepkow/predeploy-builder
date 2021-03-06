predeploy-builder
==
A builder used to generate an api at apiary/generate client lib and publish client lib to npm

##Requirements

	1.Install swagger-codegen command line tools at https://github.com/swagger-api/swagger-codegen
	2.npm install -g cli-codegen 
	3.Easiest to run this code while app is running and swagger is at localhost:8000/swagger.json
	4.Look at https://www.npmjs.com/package/cli-codegen if swagger location different.
##Example
First:
	
	npm install predeploy-builder
	
Next: 
	
	var builder = require('builder');
	
	var config  = {
		client: { //required for .makeClientLib(),writePackage() and publish() 
			file: 'File name' //not required,
			classname: 'classname for javascript gen' //required for js
			language: 'language to generate lib for' //required
		}
		apiary : {
			token: 'your apiary account token' //required
			name: 'your apiary api name' //required,
			sub_domain: 'This is used to point readme to your proper api location in apiary' //required for writeReadme()
		}
		package: { //Anything not passed in will be pulled from project package file that was used to generate lib
			name: 'name that will go in package' //not required
			version: 'version that will go in package' //not required
			description: 'description that will go in package' //not required
			author: 'author that will go in package' //not required
			license: 'license that will go in package' //not required
		}
		port: 'port your api is hosted on' // will default to 8000 if not passed in
	}	
	
	var build = new builder(config);
	

###genDocs:

	build.genDocs( (err,result) => {} )
	
	//This Method is used to publish api to apiary
	
###makeClientLib:

	build.makeClientLib( (err,result => {} )
	
	//This Method is used to generate client library for a language based on config from earlier.
	
###writePackage
	
	build.writePackage( (err,result) => {} )
	
	//this Method is used to write a package file in order to prep for npm publish
	
###writeReadme
	
	build.writeReadme ( (err,result) => {} )
	
	//This Method is used to write a readme.md pointing to apiary docs.	
	
###publish

	build.publish( (err,result) => {} )
	
	//This method is used to publish the newly made client lib to npm
	
###Note: makeClientLib(),writePackage() and publish() should all be used togeather. Only makeClientLib() can work on its own.	
				
	
	
