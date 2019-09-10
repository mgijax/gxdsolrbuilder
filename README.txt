This gxdsolrbuilder product contains the Java libraries and webapp needed to
run Solr in a Jetty process.  It also contains GXD-specific index definitions
and scripts that can be used to build a directory hierarchy for a new Solr
instance.  The directory structure is as follows:

gxdsolrbuilder/
	buildGxdSolr - main script to build a new Solr instance
	updateGxdSolrIndexDefinitions - script to copy updated index 
		definitions into an existing Solr instance

	defs/ - directory of GXD-specific index definitions
	lib/ - directory of Java libraries needed by the Solr webapp
	templates/ - directory of config file and script templates which will
		have values filled in by buildGxdSolr
	webapps/ - directory with the solr.war webapp itself

buildGxdSolr takes four parameters on the command-line:
	<target directory> - path where you want to build the Solr instance
	<installation name> - shorthand one-word name for this instance
	<solr port> - port on which Jetty should listen for Solr searches
	<shutdown port> - port on which Jetty should listen for shutdown signal

	When finished, you should be able to cd to your <target directory> and
	run startSolr to start your Solr server and stopSolr when you want to
	stop it.

updateGxdSolrIndexDefinitions takes two parameters on the command-line:
	<target directory> - path where your Solr instance lives
	<installation name> - shorthand one-word name for this instance

	This script can be used to apply new index definitions and schema
	changes to an existing Solr installation.  Once you have run this
	script, you should run the installation's stopSolr and startSolr
	scripts to force Solr to pick up the changes, and then re-index the
	data for any indexes with changes.

Your Solr installation directory will contain a few other useful files, beyond
what is required for Solr itself:
	solr.pid - contains the process ID for the corresponding Solr process,
		if one is running
	solr.url - contains the base URL for accessing this Solr instance
	solr.port - contains the port on which this Solr instance listens
