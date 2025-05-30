## Mongo Compass Web Helm Chart

This Helm chart provides an easy way to deploy a web-based MongoDB Compass UI on your Kubernetes cluster, offering a convenient graphical interface to manage and interact with your MongoDB databases.

---

## 🚀 Features

*   **Web-Based MongoDB Compass**: Access MongoDB Compass through your browser without installing a desktop application.
*   **Kubernetes Integration**: Seamlessly deploy and manage the Compass UI within your Kubernetes environment.
*   **Helm Chart Deployment**: Simplify the deployment process using Helm, the package manager for Kubernetes.

---

## 📦 Installation

### Prerequisites

*   A running Kubernetes cluster
*   Helm installed on your local machine

### Steps

1.  **Add the Helm Repository**:
    
    `helm repo add mongo-compass-web https://underndog.github.io/mongo-compass-web-helm helm repo update`
    

1.  **Install the Chart**:
    
    `helm install mongo-compass-web mongo-compass-web/mongo-compass`
    

1.  **Access the UI**:
    
    `kubectl get svc`
    

Access the MongoDB Compass UI by navigating to the service's external IP or using port forwarding:

`kubectl port-forward svc/mongo-compass-web 8080:8080`

Then open your browser and go to `http://localhost:8080`.

---

## ⚙️ Configuration

The chart can be customized using the following parameters in your `values.yaml` file:

*   `replicaCount`: Number of replicas for the deployment (default: `1`)
*   `image.repository`: Docker image repository (default: `haohanyang/compass-web`)
*   `image.tag`: Docker image tag (default: `“”`)
*   `service.type`: Kubernetes service type (default: `ClusterIP`)
*   `service.port`: Service port (default: `80`)
*   `defaultMongodbUri`: Default MongoDB connection URI shown in the Compass UI (default: `""`)

To override these values during installation:

`helm install mongo-compass-web mongo-compass-web/mongo-compass \  --set replicaCount=2 \  --set service.type=LoadBalancer \ --set defaultMongodbUri=\"mongodb://username:password@host:27017/dbname\"`

> **Note:** Setting `defaultMongodbUri` will pre-fill the connection string in the Compass UI, making it easier for users to connect to your MongoDB instance by default. You can leave it empty to require users to enter their own connection string.

---

## 🧪 Development

To package and test the chart locally:

1.  **Package the Chart**:
    
    `helm package ./mongo-compass --destination .`
    

1.  **Create or Update the Helm Repository Index**:
    
    `helm repo index ./ --url https://underndog.github.io/mongo-compass-web-helm`
    

1.  **Install the Chart Locally**:
    
    `helm install mongo-compass-web ./mongo-compass-0.1.1.tgz`
    

---

## 📄 License

This project is licensed under the [Apache 2.0 License](https://github.com/underndog/mongo-compass-web-helm/blob/master/LICENSE).

---

## 🙏 Acknowledgments

This Helm chart utilizes the Docker image from [haohanyang/compass-web](https://github.com/haohanyang/compass-web), which brings MongoDB Compass to the browser.

---

For more information and updates, visit the [GitHub repository](https://github.com/underndog/mongo-compass-web-helm).

## Script
helm package ./mongo-compass --destination .
helm repo index ./ --url  https://underndog.github.io/mongo-compass-web-helm