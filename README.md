# CI/CD Pipeline Architecture

![CI/CD Pipeline](./cicd-pipeline.png)

GitHub → CodePipeline → CodeBuild → ECR → ECS → ALB.

Push to `main` triggers an automated build, test, image push, and
zero-downtime deploy — no manual steps. Secrets are pulled at build
time from Secrets Manager rather than stored in the repo; CloudWatch
watches the deploy stage and alerts on failure.

This diagram is the design behind [CineTrack](#), a movie watchlist
API I'm building to put this exact pipeline into practice.
