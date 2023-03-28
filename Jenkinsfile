  pipeline {
        
        agent any
        
        triggers {
            pollSCM 'H/5 * * * *' 
        }
        
        stages{
            stage("PayTonkawa checkout"){
                steps {
                    git branch: 'main', url: 'https://github.com/xonatis-academy/epsi-dev709-ci.git'
                }
            }
        
     
        
          
            stage("PayTonkawa Clean"){
                steps {
                    dir ('projects/erphrense'){
                        bat './mvnw clean'
                          
                    }
                }
            }
          
          
              stage("PayTonkawa dependncies"){
                steps {
                    dir ('projects/erphrense'){
                         bat './mvnw compile'
                          
                    }
                }
            }
          
          
            stage("PayTonkawa Test"){
                steps {
                    dir ('projects/erphrense'){
                          bat './mvnw test'
                          
                    }
                }
            }
          
          
           stage("PayTonkawa Package"){
                steps {
                    dir ('projects/erphrense'){
                         bat './mvnw package'
                          
                    }
                }
            }
          
          
             stage("PayTonkawa Archive"){
                steps {
                    dir ('projects/erphrense'){
                        bat 'rename target\\erphrense-0.0.1-SNAPSHOT.jar paytonkawa-%BUILD_NUMBER%.jar'
                        archiveArtifacts artifacts: 'target\\paytonkawa-*.jar', followSymlinks: false
                          
                    }
                }
            }
          
          
        }  
        
    }
