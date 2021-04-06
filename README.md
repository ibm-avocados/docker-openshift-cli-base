# docker openshift cli base

## Scope

A simple docker container that has everything required to access OpenShift 4.x clusters on  IBM Cloud from the command line.

## Usage
This container is designed to be a parent container and not run directly:

It does the following for child containers:

- Provides both the  `oc` and `ibmcloud` cli for specific versions of OpenShift 4.x (currently 4.4, 4.5, 4.6)

- Copies all scripts in a **scripts** folder in the  child containers build env to the **scripts** folder in the child image.

The Dockerfile for a child container just needs the **FROM** statement:

```
FROM quay.io/ibm-avocados/openshift-cli-base:4.6
```

## Building the image

- To build the OpenShift 4.6 version of the image run the following command:
```
docker build -t <your image tag> .
```
- To build the OpenShift 4.5 version of the image run the following command:
```
docker build -t <your image tag> --build-arg OPENSHIFT_VERSION=4.5 --build-arg KUBECTL_VERSION=1.18.10 .
```
- To build the OpenShift 4.4 version of the image run the following command:
```
docker build -t <your image tag> --build-arg OPENSHIFT_VERSION=4.4 --build-arg KUBECTL_VERSION=1.17.13 .
```

## License & Authors

If you would like to see the detailed LICENSE click [here](./LICENSE).

- Author: David Carew <carew@us.ibm.com>
```text
Copyright:: 2020- IBM, Inc

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
