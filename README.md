# Docker to ECS Action

This composite action takes in the required inputs from your workflow, builds a docker image, pushes the image to your docker hub repository, creates an ECS Task Definition and finally deploys the image to ECS using Fargate.

## Required Inputs

- **aws-region**:
    description: 'AWS region'
    default: 'us-east-1'
    required: false
- **aws-access-key-id**:
    description: 'AWS access key ID'
    required: true
- **aws-secret-access-key**:
    description: 'AWS secret access key'
    required: true
- **docker-hub-username**:
    description: 'Docker Hub username'
    required: true
- **docker-hub-password**:
    description: 'Docker Hub password'
    required: true
- **dockerfile-path**:
    description: 'Path to Dockerfile'
    required: true
- **ecs-service-name**:
    description: 'ECS Service Name'
    required: true
- **ecs-cluster-name**:
    description: 'ECS Cluster Name'
    required: true
- **ecs-task-definition-family**:
    description: 'ECS Task Definition Family'
    required: true
- **container-image-name**:
    description: 'Container Image Name'
    required: true
- **container-image-tag**:
    description: 'Container Image Tag'
    required: true

## Usage

```yml

...

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Deploy to ECS
      uses: Makinates/daniel-docker-ecs-action@main
      with:
        aws-region: us-east-1
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        docker-hub-username: ${{ secrets.DOCKER_HUB_USERNAME }}
        docker-hub-password: ${{ secrets.DOCKER_HUB_PASSWORD }}
        dockerfile-path: ./path/to/Dockerfile
        ecs-cluster-name: ${{ env.ECS_CLUSTER }}
        ecs-service-name: ${{ env.ECS_SERVICE }}
        ecs-task-definition-family: ${{ env.ECS_TASK_DEFINITION_FAMILY }}
        container-image-name: ${{ env.CONTAINER_IMAGE_NAME }}
        container-image-tag: ${{ github.sha }}
    

```
