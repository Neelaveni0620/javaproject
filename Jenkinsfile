pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                git branch: 'main', credentialsId: 'declarativepipe', url: 'https://github.com/Neelaveni0620/javaproject.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('prod'){
            steps{
            sshagent(['declarativepipeline']) {
            sh 'scp -o StrictHostKeyChecking=false target/javaproject.war ec2-user@3.26.145.25:/opt/apache-tomcat-9.0.74/webapps/'
        }
        }
    }
}
}
