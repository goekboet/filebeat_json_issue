# Decode json in filebeat hint-based docker container logs

The purpose of this repository is to minimally reproduce a situation where a program logs in json format to stdout running in a container. Filebeat (also running in docker) is then configured via docker hints-based autodiscover to ship these logs together with added docker metadata. 
The question is if its possible to make filebeat to decode the message json and append the properties to the root object. I.e what we want to accomplish is a shipped entry that looks like:
```json
{
    "@timestamp": "2019-06-15T19:48:04.963Z",
    .
    .
    .
    "foo": "bar",
    .
    .
    .
}

```
instead of
```json
{
    "@timestamp": "2019-06-15T19:48:04.963Z",
    .
    .
    .
    "message": "{\"foo\":\"bar\"}",
    .
    .
    .
}

```

To run the sample: `docker-compose run -d`. Filebeat ships to the filebeat directory in the repo.