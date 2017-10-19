# Logstash config for OGP usage dashboard

Contains logstash configuration for the OGP usage dashboard. The first version
used logstash 1.x to parse tomcat and apache logs, then populate a Solr
instance that could be referenced by a Banana dashboard.

This config no longer works on logstash v5.x. The file in `logstash-5.x/` is
a start towards a configuration compatible with the newer Logstash versions.
This new version also uses Solr dynamic field types for greater flexibility and
ease of configuration.

Additionally, I had issues with the Logstash solr output plugin in Logstash v5.x.
I used a slightly modified version that can be found [here](https://github.com/chrissbarnett/logstash-output-solr_http)

Note: The core used to store OGP log info should not be in the same Solr instance
as the OGP core being monitored, since solr logs are being watched and parsed.

A better way forward, long term, might be to have OGP populate a solr core
directly, or to customize the OGP logs so that they provide the analytics we
need.

It's also worthwhile to investigate whether existing analytics frameworks will
meet our needs.  
