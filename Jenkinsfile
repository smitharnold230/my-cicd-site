pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS-ACCESS-KEY')      // Jenkins credential ID
        AWS_SECRET_ACCESS_KEY = credentials('AWS-SECRET-ACCESS-KEY') // Jenkins credential ID
        S3_BUCKET_NAME        = 'my-static-website-cicd-1234'
        AWS_REGION            = 'ap-south-1'
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Deploy to S3') {
            steps {
                echo 'Starting deployment to S3...'
                sh "aws s3 sync . s3://${S3_BUCKET_NAME} --region ${AWS_REGION} --delete"
                echo 'Deployment complete!'
            }
        }
    }
}
