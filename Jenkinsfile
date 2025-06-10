pipeline {
    agent { label “mynode” }

    environment {
        S3_BUCKET = 'my-static-website-bucket'
    }

    stages {
        stage(‘code clone') {
            steps {
                git url: "https://github.com/BashOps/django-travel-app.git", branch: "master"
            }
        }
        stage('Deploy to S3') {
            steps {
                sh '''
                    aws s3 sync . s3://$S3_BUCKET --delete
                '''
            }
        }
    }
}

