pipeline {
    agent any
    tools {
        maven "mavenv3"
    }
    
    stages {
        stage("Checkout") {
            steps {
                git branch: "main", url: "https://github.com/nadertoti/SpringPetClinic.git"
            }
        }
        
        stage("Build") {
            steps {
                sh "mvn compile"
            }
        }
        
        stage("Test") {
            steps {
                sh "mvn test"
            }
        }
        
        stage("Package") {
            steps {
                sh "mvn package -DskipTests"
            }
        }
        
        stage("Deploy") {
            steps {
                sh "java -jar ./target/*.jar &"
            }
        }
    }
    
    post {
        always {
            echo "Pipeline execution completed"
        }
        success {
            echo "Pipeline succeeded!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
