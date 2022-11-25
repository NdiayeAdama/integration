  pipeline {
        
        agent any
        
        triggers {
            pollSCM 'H/5 * * * *' 
        }
        
        stages{
            stage("checkout"){
                steps {
                    git branch: 'main', url: 'https://github.com/xonatis-academy/epsi-dev709-ci.git'
                }
            }
        
     
        
          
            stage("Clean"){
                steps {
                    dir ('projects/erphrense'){
                        bat './mvnw clean'
                          
                    }
                }
            }
          
          
              stage("Compile"){
                steps {
                    dir ('projects/erphrense'){
                         bat './mvnw compile'
                          
                    }
                }
            }
          
          
            stage("Test"){
                steps {
                    dir ('projects/erphrense'){
                          bat './mvnw test'
                          
                    }
                }
            }
          
          
           stage("Package"){
                steps {
                    dir ('projects/erphrense'){
                         bat './mvnw package'
                          
                    }
                }
            }
          
          
             stage("Archive"){
                steps {
                    dir ('projects/erphrense'){
                        bat 'rename target\\erphrense-0.0.1-SNAPSHOT.jar erphrense-%BUILD_NUMBER%.jar'
                        archiveArtifacts artifacts: 'target\\erphrense-*.jar', followSymlinks: false
                          
                    }
                }
            }
          
          
        }  
        
    }
