pipeline {
   agent any
   environment
   {
       registry = "123456nish/nishanth"
       registryCredential = 'Docker123'
       dockerImage = ''
   }
    
   stages {
     stage('checkout') {
          steps {
            
               git branch: 'master', url: 'https://github.com/Nishanth-ctrl/Dockerfiles.git'
            
         }
       }
     stage('Image Build'){
          steps{
              script{
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
     stage('Deploy our image') {
         steps{
           script {
             docker.withRegistry( '', registryCredential ) {
             dockerImage.push()
           }
       }
           }
       }

}
}
