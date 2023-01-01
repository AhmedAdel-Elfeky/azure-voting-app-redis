pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker Build') {
         steps {
            sh(script: 'docker images -a')
            sh(script: """
               cd azure-vote/
               docker images -a
               docker build -t jenkins-pipeline .
               docker images -a
               cd ..
            """)
         }
      }
      
      stage('push container'){
      	  steps{
      	     echo "Workspace is $WORKSPACE"
      	     dir("$WORKSPACE/azure-vote"){
      	       script {

      	        docker.withRegistry('https://index.docker.io/v1/','DockerHub'){

      	         def image=docker.build('ahmedadel7elfeqy/jenkins-course:latest')
      	  	         image.push()
      	  	       	}
      	  	       	}
      	  	       }
      	  	      }	
      	  		
      
      }



     
    
     
     
     
   }
}
