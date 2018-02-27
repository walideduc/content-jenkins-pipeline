pipeline {
    agent any

    stages {
        stage('Say Hello'){
            steps {
                sayHello 'Awesome man!'
            }
        }
        stage('Git information'){
            steps {
                echo "My Branch Name: ${env.BRANCH_NAME}"

                script {
                    def myLib = new alyya.git.gitStuff();
                    echo "My Commit: ${myLib.gitCommit("${env.WORKSPACE}/.git")}"
                }
            }
        }
        stage('build'){
            steps {
                sh 'javac -d . src/*.java'
                sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
                sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
            }
        }
        stage('run'){
            steps {
                sh 'java -jar rectangle.jar 7 9'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'rectangle.jar' , fingerprint : true
        }
    }
}