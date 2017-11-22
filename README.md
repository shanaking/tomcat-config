# tomcat-config
external tomcat configuration

# Configure Repository
 - Alter configuration files in the tomcat/conf directory
 - Create tar file of tomcat directory 
    - `tar -cvf tomcat_config.tar tomcat`
 - Verify tomcat_config.tar file is located in repository directory at same level as index.yml
# Configure Index
 - In index.yml, update <domain>
 - Add entries for any additional repository versions
   - Repository version to be used can be set by:
     - java buildpack config/tomcat.yml
     - application manifest in the JBP_CONFIG_TOMCAT environment variable
       - external_configuration: { repository_root: "http://tomcat-repo.<domain>", version: "2.0.0" }
# Push repository application
 - `cf push -f /repository/manifest.yml`
# Designate repository in application manifest
 - env:
    JBP_CONFIG_TOMCAT: '{ tomcat: { external_configuration_enabled: true }, external_configuration: { repository_root: "http://tomcat-repo.<domain>"}}'
 
