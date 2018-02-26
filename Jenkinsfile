pipeline {
    agent any

    stages {
        stage('build'){
            steps {
                sh 'javac -d . src/*.java'
                sh 'echo Main-Class: Rectangulator > MAINIFEST.MF'
                SH 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
            }
        }
    }
}