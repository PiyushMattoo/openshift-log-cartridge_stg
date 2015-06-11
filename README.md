## OpenShift Logstash Cartridge

The logstash cartridge allows you to start a version of logstash which can be used to stream, collect all the logs from OPENSHIFT_LOG_DIR (in a pre-defined format) into Doradus.


## Environment Variables

These environment variables are used when configuring Logstash:

 * **`OPENSHIFT_DORADUS_HOST`**: URL of the Doradus hosting server. 
 * **`OPENSHIFT_DORADUS_PORT`**: Port-number of the Doradus service. 
 * **`OPENSHIFT_DORADUS_TENANT`**: Tenant name. 
 * **`OPENSHIFT_DORADUS_USER`**: Tenant User. 
 * **`OPENSHIFT_DORADUS_PWD`**: Tenant Password. 


## Installation

First, configure the application with the appropriate environment variables. Then, add the cartridge to your application:

    # Configure environment
    $ rhc env set OPENSHIFT_DORADUS_HOST=abc123-us-east-1.foundcluster.com OPENSHIFT_DORADUS_PORT=1123 OPENSHIFT_DORADUS_TENANT=secret 
	  OPENSHIFT_DORADUS_USER=lucille OPENSHIFT_DORADUS_PWD=agnes -a my-app

    # Add cartridge
    $ rhc cartridge add -a your-app-name https://raw.githubusercontent.com/PiyushMattoo/openshift-log-cartridge_stg/master/metadata/manifest.yml

## Usage

Redirect the application logs to OPENSHIFT_LOG_DIR in the below format and the log will be tailed, loaded into Doradus.

`<ISO 8601 Standard time> <LogLevel> <Log Message>`  
For example: `2015-03-20 11:08:05 INFO Test Message One` 

Doradus REST command to view the logs:

`http://<DoradusHost>:<DoradusPort>/LoggingApplication/Logs/_query?tenant=<DoradusTenant>&q=*`
	
## License

Released under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).