# Crossplane, GitOps, and Kubernetes Notes

**Kubernetes as an Ultimate API**: Kubernetes (K8s) is a powerful API that enables various operations like pod scheduling and infrastructure provisioning. It is a strong candidate for a comprehensive API that can handle all requests efficiently. Kubernetes API brings us closer to the goal of a unified API for managing infrastructure.

**Challenges with Existing Tools**: Existing tools like Chef, Puppet, and Terraform have automation capabilities but are not ideal for tracking drifts and achieving automatic synchronization between desired and actual states. Crossplane emerges as a potential next-generation tool for managing infrastructure, leveraging the Kubernetes API.

**Crossplane Overview**: Crossplane is based on the Kubernetes API and can be installed in a Kubernetes cluster using Helm. It offers features such as declarative infrastructure provisioning and acting as a single source of truth for managing infrastructure.

**Scenario: Deploying a Kubernetes Cluster**: In a scenario where a Kubernetes cluster is initially deployed with one node instead of the intended three nodes spread across multiple availability zones, Crossplane comes into action. By manually adding two additional nodes via the UI, Crossplane detects the discrepancy between the desired state defined in its manifests and the actual state.

**Crossplane's Role**: Crossplane, being the single source of truth, automatically removes the newly created nodes, recognizing them as drifts. To bring the actual state in line with the desired state, the manifest file needs to be modified. For example, by adding two additional node locations (e.g., us-east1-c, us-east1-b) to the manifest. The changes can be reapplied using `kubectl apply` or through the use of Argo CD.

**Argo CD and GitOps**: Argo CD, following the GitOps principle, can be set up to automatically detect changes in the GitHub repository and execute them. When the new manifest is pushed to the repository, Argo CD identifies the changes and triggers their automatic execution.

**Crossplane Considerations**: While Crossplane has advantages such as a unified API and similarities to native Kubernetes objects, it has drawbacks, including limited documentation, a smaller community compared to Terraform, and fewer providers. Initial setup of Crossplane requires a Kubernetes cluster.

**Terraform vs. Crossplane**: Terraform represents infrastructure using declarative configuration, but it can become challenging to manage collaboration and scalability. Terraform relies on a monolithic state file and has blocking processes during configuration application. In contrast, Crossplane promotes loose coupling and eventual consistency, allowing for better collaboration. Each infrastructure piece in Crossplane is an independent API endpoint supporting CRUD operations.

In summary, Crossplane, combined with GitOps principles, offers advantages such as scalable collaboration and a unified API for managing infrastructure. While Terraform has its strengths, Crossplane provides a more flexible and efficient approach to infrastructure management, addressing challenges related to scalability and collaboration in large environments.