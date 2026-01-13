pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
        BUCKET_NAME = 'jenkins-iam-s3-bucket-12345'
    }

    stages {
        stage('Create S3 Bucket') {
            steps {
                sh '''
                    aws --version
                    aws s3api create-bucket \
                      --bucket $BUCKET_NAME \
                      --region $AWS_DEFAULT_REGION
                '''
            }
        }
    }

    post {
        success {
            echo 'S3 bucket created using IAM Role'
        }
        failure {
            echo 'S3 bucket creation failed'
        }
    }
}
