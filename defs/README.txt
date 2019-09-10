The defs/ directory contains a subdirectory for each Solr index plus a
default/ subdirectory.

The defs/default/ subdirectory contains the default files which are shared in
common across all the Solr indexes.

Each specific index's subdirectory (eg: defs/gxdMarker/) contains files in
addition to those in defs/default/ and/or those which should override those in
defs/default/ for that particular index.

The defs/solr.xml file is the one to be included in the installation's
multicore-* directory.  It must be kept in sync as new subdirectories are
added to defs/ for news indexes.  (This is how Solr knows which indexes to
include in its set of available indexes.)

The solrbuilder/bin/updateGxdSolrIndexDefinitions script is in charge of
copying these files into the appropriate place(s) and for overriding default
files with specific ones.

