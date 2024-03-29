  
  
  Matrizen, um bspw. Tests auf verschiedenen Versionen testen zu können:
https://docs.github.com/de/actions/using-jobs/using-a-matrix-for-your-jobs

Scheduled Workflows, um Pipelines in regelmäßigen Abständen zu starten:
https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#onschedule

Ansible in GitHub Actions ausführen:
https://github.com/marketplace/actions/run-ansible-playbook
https://www.devopstricks.in/deploy-ansible-playbook-using-github-action/

Mehr GitHub Guides: https://docs.github.com/de/actions/guides


  <h1> Deployment of a Simple Node.js Application on AWS EC2 </h1>
  <p>Welcome to the guide on deploying your Node.js app to the cloud! This guide uses Terraform and GitHub Actions to automate the process.</p>


  <p>Here's a simple Node.js Express application serving an HTML page. It listens on port 3000 and displays a success message upon access.</p>

  <h2>🛠️ Infrastructure as Code (<code>main.tf</code>)</h2>
  <p>We use Terraform to create the necessary infrastructure components on AWS, including VPC, subnet, internet gateway, route table, and an EC2 instance for Docker.</p>

  <h2>🔒 Security Group Module (<code>module/security-group</code>)</h2>
  <p>A reusable Terraform module defines security group rules for ingress and egress traffic to the EC2 instance.</p>

 
  <p>The Dockerfile sets up the Node.js application within a Docker container, making it portable and scalable.</p>

  <h2>🔨 Build Pipeline (<code>build.yml</code>)</h2>
  <p>GitHub Actions workflow automates the deployment process:</p>
  <ul>
    <li>Installs Docker on the EC2 instance.</li>
    <li>Logs in to Docker Hub to manage the Docker images.</li>
    <li>Builds and pushes the Docker image to Docker Hub.</li>
    <li>Deploys the Docker image as a container on the EC2 instance.</li>
  </ul>

  <h2>🏃‍♂️ How to Run</h2>
  <p>To replicate this deployment:</p>
  <ol>
    <li>Clone this repository.</li>
    <li>Ensure you have Terraform and Docker installed.</li>
    <li>Set up your AWS credentials and configure the variables in <code>main.tf</code>.</li>
    <li>Set Docker Hub credentials in GitHub Secrets.</li>
    <li>Push code changes to the <code>main</code> branch to trigger the workflow.</li>
  </ol>

  <p>This guide simplifies the deployment of a Node.js app on AWS EC2 using Terraform and GitHub Actions. 🌟</p>
</body>
</html>
#   c i c d _ p i p e l i n e _ g i t h u b a c t i o n s 
 
 