pipeline {

    agent any

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout Developement') {
            when {
                branch 'develop'
            }
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/develop']], 
                    userRemoteConfigs: [[url: 'https://github.com/torokur93/Jenkins-Multibranch-test.git']]
                ])
            }
        }


        stage('Build Deploy Code Developement') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact"
                """

                sh """
                cp -R ${WORKSPACE}/* /var/www/html/dev/
                """
            }
        }

        stage('Build Deploy Code Production') {
            when {
                branch 'master'
            }
            steps {
                sh """
                echo "Building Artifact"
                """

                sh """
                cp -R ${WORKSPACE}/* /var/www/html/prod/
                """
            }
        }

    }   
}