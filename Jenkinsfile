pipeline {
    agent any 
    stages{
        stage ("checkout"){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'd62d92f5-64cc-4719-941c-3d89239dfe5b', url: 'https://github.com/prathamesh-1209/spring-petclinic-DevOps']])

                

            }
        }
        stage ("build cde"){
            steps{
                 sh './gradlew assemble --no-daemon -Dorg.gradle.jvmargs="-Xmx1024m -XX:MaxMetaspaceSize=512m"'
            }
        }
        
    }
}