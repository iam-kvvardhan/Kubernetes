| Concept                | Real-life example                                       | What it does                                    |
| ---------------------- | ------------------------------------------------------- | ----------------------------------------------- |
| **Ingress**            | The **directory or signboard** at the building entrance | Says where visitors should go                   |
| **Ingress Controller** | The **receptionist/security guard**                     | Actually directs people to the right room (app) |
| **Service**            | Each **room** inside the building                       | Runs the actual app                             |
| **Cluster**            | The **whole building**                                  | Contains all rooms (apps)                       |



| Concept                | Description                                                           |
| ---------------------- | --------------------------------------------------------------------- |
| **Ingress**            | Defines how external traffic reaches services inside the cluster      |
| **Ingress Controller** | Implements those rules and actually routes the traffic                |
| **Example Controller** | NGINX, Traefik, HAProxy, AWS Load Balancer Controller                 |
| **Goal**               | Let users access apps using simple URLs instead of multiple IPs/ports |
