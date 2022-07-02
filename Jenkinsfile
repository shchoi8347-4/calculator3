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
                    sh "docker build -t shchoi8347/calculator ."
               }
          }
          stage("Docker push") {
               steps {
                    sh "docker login --username shchoi8347 --password Impact33!!"
                    sh "docker push shchoi8347/calculator"
               }
          }
	stage("Deploy to staging") {
	     steps {
	          sh "docker run -d --rm -p 8765:8080 --name calculator shchoi8347/calculator"
    		 }
	}
          stage("Acceptance test") { 
               steps { 
                    sleep 60 
                    sh "./gradlew acceptanceTest -Dcalculator.url=http://localhost:8765"
               } 
          }
     }
     post { 
          always { 
               sh "docker stop calculator" 
          } 
     }
}