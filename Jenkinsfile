pipeline{
    agent {label 'slave1'}
    //environment {
      //  PATH = "$PATH:/opt/apache-maven-3.8.2/bin"
    //}
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/devOpsvikasy/docker-app-two-vikas.git'
            }
         }        
        stage('Docker Build & Push'){
              steps {
                    sh '''
                    
                    echo " *********** Building the image **************"
                    docker build -t dockerapptwo . 
                    
                    echo " ********** Login to Nexus DTR ************* "
                    docker login -u admin -p admin@123 http://34.228.78.173:9001/repository/dockerdtr/
                    
                    echo " ********** Tagging the image ************"
                    docker tag dockerapptwo 34.228.78.173:9001/repository/dockerdtr/sharath-vikas-dtr/vikas-sharath:dockerapptwo.1.0                 
                    
                    echo "********** Push to Nexus DTR *************"
                    docker push 34.228.78.173:9001/repository/dockerdtr/sharath-vikas-dtr/vikas-sharath:dockerapptwo.1.0
                    
                    echo " ********** Logging out from  Nexus DTR *********** "
                    docker logout http://34.228.78.173:9001/repository/dockerdtr/
                    
                    echo "Image has been pushed to Nexus DTR"
                    
                    
                    
                    '''              }
         }
    }
}
