# Docker & Kubernetes Assessment Report

> [!TIP]
> Use this document to explain your design choices, optimisations and any challenges you faced.

## Dockerfile

<!-- TODO: (Optional) Explain any specific goals or design decisions -->

### Forked repository

<!-- TODO: If you submitted your changes to a fork, replace with your forked repository -->
`https://github.com/your-username/academic-calendar-api`

## Kubernetes

<!-- TODO: Document your process for deploying Navidrome on Kubernetes -->
<!-- Any challenges you encountered (e.g., networking, storage) and how you overcame them. --> 
<!-- Any interesting features or configurations you experimented with. --> 
Given the goal that we were translating the input Docker Compose file, I chose a very simple design which creates a Deployment and a corresponding Service. It mounts the required volumes as a one:one correspondence with the Docker Compose file. 

I tried to experiment with Ingress controller as NGINX to expose the app. This was a bit challenging because it added more configuration compared to just using a Service. I had to figure out how routing works and how the Ingress connects to the Service. At first, I ran into errors like 404 and 502 because my ports didn’t match properly or the Service wasn’t set up correctly. It took some time to understand how everything links together.

This was my first time using Kubernetes and I tried learning some basics from mindmajix.com - this guided me on the fundamentals of writing manifests. This has furthered my understanding of containers and container ochestration. I look forward to learning more!
