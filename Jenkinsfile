pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                echo "========executing A========"
            }
        }
        stage("Build"){
            steps{
                sh "mvn package"
                echo "========executing A========"
            }
        }
        stage("Deploy on test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://3.84.152.39:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
        stage("Deploy on prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://3.89.150.151:8080/')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
