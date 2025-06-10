pipeline {
    agent { label "mynode" }

    environment {
        S3_BUCKET = 'static-wesite-hosting-my-cicd'
    }

    stages {
        stage('Code Clone') {
            steps {
                git url: 'https://github.com/arunp-123/aws-s3-static-website-cicd.git', branch: 'master'
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
