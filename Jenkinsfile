
node {
    stage('Build') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000'){
            checkout scm
            sh 'npm install'
        }
    }
    stage('Test') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000'){
           // sh './jenkins/scripts/test.sh'
           sh "chmod +x -R ${env.WORKSPACE}"
           sh './src/test/java/com/mycompany/app/AppTest.java'
        }
    }
}