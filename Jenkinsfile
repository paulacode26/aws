pipeline {
    agent any

    stages {
        
        stage('Deploy') {
            agent{
                docker{
                    
                    image 'amazon/aws-cli'
                    reuseNode true
                    args '--entrypoint=""'
                }
            }
            steps {
                withCredentials([usernamePassword(credentialsId: 'my-aws', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {

                    sh '''
                        aws --version
                        aws s3 ls
                        echo "Hello S3!" >index.html
                        aws s3 cp index.txt s3://aws-20250322paula/index.html
                    '''
                }
            }
        }
    }
}
