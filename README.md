# dpreno-react-redux-chart
This is a Helm chart for deploying the RealWorld example app.


## Assumptions
You need to have the following:
* Helm 3.0 installed and working
* A Kubernetes cluster which you are currently connected/authenticated to
## Instructions
Clone this git repo to your local machine:
``` git clone https://github.com/dpreno-mcgill/dpreno-react-redux-chart.git ```

For an install with defaults, simply run Helm install :
helm install *<Helm deployment name>* *<Helm chart location>*
 
Assuming the default chart name and repo name:
``` helm install dpreno-react-redux dpreno-react-redux-chart ```

## Modifiable default values:
The skeleton structure was created with "helm create" in order to respect best practices, there are some unused features in the current version of this chart. They have been intentionally left in for future use, but can be safely ignored as of this writing.
 
Here are the sections that may be modified to tailor the app to your environment:
### Chart.yaml
* *name:* This defines the name of the Helm chart, but is also used throughout the chart to define the name of the various Kubernetes elements being deployed. If you need to modify the name of the individual elements, either modify this chart name or consider changing the template code to pull the name from a different value.
* *version:* This defines the version of the Helm chart. It is recommended to increment it with each modification/improvement.
* *appVersion:* This defines the version of the application being deployed by the Helm chart. This is used in a few different places, notably it is the default tag for the image pull of the application. It is recommended to update this if the application version changes or if the container image tag changes.

### values.yaml
* *replicaCount:* This defines the number of replicas that you want the deployment to run.
* *image.repository:* This defines the container image base location. Do not explicitly define the tag here.
* *image.tag:* This explicitly defines the container image tag for the version to be pulled. If none is present, it will use appVersion from the Chart.yaml file. It's recommended to leave it explicitly defined for clarity at this time.
* *service.type:* This defines the type of Service object. The default is set to LoadBalancer for use with Minikube, but can be modified for use in other contexts as needed.
