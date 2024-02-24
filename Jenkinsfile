pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url:'https://github.com/NaveenGokavarapu19/SpringPetClinic.git'
            }
        }
            stage('Build'){
                steps{                
                    sh "mvn compile"
                    
                }
                    
                }
            stage('Test'){
                steps{                
                    sh "mvn test"
                    
                }
                    
                }
            stage('Packagae'){
                steps{                
                    sh "mvn package"
                    
                }
                    
                }
            stage('Deploy'){
                steps{                
                    sh "java -jar /var/lib/jenkins/workspace/petLClinicScriptedPipeline/target/*.jar"
                    
                }
                    
                }
            
                // Run Maven on a Unix agent.

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    


