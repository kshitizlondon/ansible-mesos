# Summary
This will set you up, via anislbe, with a mesos cluster using 4 VMs using vagrant and virtualbox

# Prerequisites
Get the latest versions of
* Ansible
* Vagrant
* Virtualbox

# Usage
```vagrant up```

# Useful links
Mesos
http://192.168.50.30:5050/

Marathon
http://192.168.50.30:8080

# Test case
```
curl -X POST -H "Accept: application/json" -H "Content-Type: application/json" \
  localhost:8080/v2/apps -d '
{
    "id": "inky",
    "container": {
        "docker": {
            "image": "mesosphere/inky"
        },
        "type": "DOCKER",
        "volumes": []
    },
    "args": ["hello"],
    "cpus": 0.2,
    "mem": 32.0,
    "instances": 1
}'
```