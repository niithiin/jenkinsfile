node {
    
    stage ('1-git') {
        git changelog: false, poll: false, url: 'https://github.com/niithiin/time_tracker.git'
    }
     stage ('2-mvn') {
         
         def mvn_var = tool name: 'm1', type: 'maven' 
         sh "${mvn_var}/bin/mvn clean package"
        
     }
     stage('3-Deploy to Tomcat'){
      
     sshagent(['9f7c7290-bdb2-411d-9734-f6d168f38fe5']) {
         sh " scp -o StrictHostKeyChecking=no web/target/*.war ec2-user@172.31.31.117:~"
         sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.31.117 sudo cp /home/ec2-user/*.war /opt/tom7/webapps"
      }
   }
}
