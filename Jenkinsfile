@Library('pipeline-library-demo@main') _

pipeline {

    agent any

    parameters {

        string(
            name: 'APP_NAME',
            defaultValue: 'my-java-app',
            description: 'Application name'
        )

        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'prod'],
            description: 'Deployment environment'
        )

        string(
            name: 'DOCKER_TAG',
            defaultValue: 'latest',
            description: 'Docker image tag'
        )

        booleanParam(
            name: 'DEPLOY',
            defaultValue: true,
            description: 'Deploy application?'
        )
    }

    stages {

        stage('Run Shared CI/CD') {

            steps {

                script {

                    cicdPipeline(
                        appName: params.APP_NAME,
                        environment: params.ENVIRONMENT,
                        dockerTag: params.DOCKER_TAG,
                        deploy: params.DEPLOY
                    )

                }
            }
        }
    }
}
