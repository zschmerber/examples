# Developing and Testing Bloblang mappings
Use RedPanda to perform the bloblang translation using sample data and mapping
```
docker pull ghcr.io/redpanda-data/connect:latest 
docker run -p 4195:4195 --rm http://ghcr.io/redpanda-data/connect  blobl server --no-open --ho
```

1. Drag the mapping (.blobl) file in the bottom panel
1. Drag the source (.json) file to the top right
1. Copy the output containing the data translated to OCSF

Use ocsf-server and ocsf-schema to validate the Translated data
```
mkdir ~/etl-ocsf
cd ~/etl-ocsf
git clone https://github.com/ocsf/ocsf-schema.git
git clone https://github.com/ocsf/ocsf-server.git
cd ocsf-server
docker build -t ocsf-server .
docker run -it --rm --volume ~/etl-ocsf/ocsf-schema:/app/schema -p 8080:8080 -p 8443:8443 
```
Paste translated data into [ocsf validation API endpoint](https://localhost:8443/doc/index.html#/Tools/SchemaWeb_SchemaController_validate2)

# Reference
[Bloblang Walkthrough ](https://docs.redpanda.com/redpanda-connect/guides/bloblang/walkthrough/)