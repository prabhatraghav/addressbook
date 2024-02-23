pipeline{
	agent any
      stages{
           stage('Git Checkout Stage'){
               steps{
		 echo 'Checkingout git for the code'
                 git 'https://github.com/prabhatraghav/addressbook.git'
		 echo 'Done: Checkingout the code'
                 }
           }
          stage('Maven Compile Stage'){
              steps{
		 echo 'Compiling the code'
                 sh 'mvn compile'
		 echo 'Done: Compiling the code'
	         }
           }
          stage('Maven Test Stage'){
              steps{
		 echo 'Testing the code'
                 sh 'mvn test'
		 echo 'Done: Testing the code'
	         }
           }
          stage('Maven QA Stage'){
              steps{
		 echo 'QA of the code'
                  sh 'mvn checkstyle:checkstyle'
		 echo 'Done: QA of the code'
                 }
           }
	     stage('Maven Clean Package Stage'){
		steps{
		 echo 'Packaging of the code'
                  sh 'mvn clean package'
		 echo 'Done: Packaging of the code'
    	         }
	   }
	     stage('Deploy to Tomcat9'){
		steps{
		  echo 'Deploying the *.war to Tomcat 9'
		  sh 'deploy adapters: [tomcat9(credentialsId: 'tomcat_cred', path: '', url: 'http://34.125.36.224:9090/')], contextPath: null, war: '**/*.war''
		}
	     }
        }
}
