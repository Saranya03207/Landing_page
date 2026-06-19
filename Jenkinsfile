pipeline {
agent any

stages {

    stage('Deploy to S3') {
        steps {
            withCredentials([
                string(credentialsId: 'AWS_ACCESS_KEY_ID', variable: 'AWS_ACCESS_KEY_ID'),
                string(credentialsId: 'AWS_SECRET_ACCESS_KEY', variable: 'AWS_SECRET_ACCESS_KEY')
            ]) {
                sh '''
                export AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID
                aws configure set aws_secret_access_key %AWS_SECRET_ACCESS_KEY%
                export AWS_DEFAULT_REGION=ap-south-1

                aws s3 sync . s3://landingpage-03 --delete
                '''
            }
        }
    }
}


}
