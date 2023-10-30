pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from github webhook'
            }
        }
        stage('build') {
            steps {
                echo 'Building'
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying'
		withCredentials([[
		    $class: 'AmazonWebServicesCredentialsBinding',
		    credentialsId: 'MyAWS',
		    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
		    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                        sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html s3://test-env-jenkins-fer/')
		}
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}

