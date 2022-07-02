pipeline {
     agent any
     stages {
          stage("Compile") {
               steps {
                    sh "./gradlew compileJava"
               }
          }
          stage("Unit test") {
               steps {
                    sh "./gradlew test"
               }
          }
          stage("Package") {
               steps {
                    sh "./gradlew build"
               }
          }

          stage("Docker build") {
               steps {
                    sh "docker build -t shchoi8347/calculator:1 ."
               }
          }
          stage("Docker push") {
               steps {
                    sh "docker login --username shchoi8347 --password Impact33!!"
                    sh "docker push shchoi8347/calculator:1"
               }
          }
     }
}