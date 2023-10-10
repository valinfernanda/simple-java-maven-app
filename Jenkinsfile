node {
    // Menggunakan Docker sebagai agent
    def mydocker = docker.image('maven:3.9.0').inside('-v /root/.m2:/root/.m2')

    stage('Build') {
        steps {
            // Menjalankan perintah build dengan Maven
            mydocker.sh 'mvn -B -DskipTests clean package'
        }
    }

    stage('Test') {
        steps {
            // Menjalankan perintah test dengan Maven
            mydocker.sh 'mvn test'
        }
        
        post {
            always {
                // Melaporkan hasil pengujian dengan JUnit
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}
