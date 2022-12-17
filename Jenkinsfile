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