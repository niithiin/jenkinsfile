node {
    
    stage('1-git') {
   
   git 'https://github.com/raghuk134/time-tracker.git'
 
}
stage('2-maven') {
    
    def mave = tool name: 'anish-maven', type: 'maven'
    sh "${mave}/bin/mvn clean package"
   }
stage('3-deploy2tomcat') {
    sshagent(['tomid']) {
        
        sh "scp -o StrictHostKeyChecking=no web/target/*.war ec2-user@172.31.17.117:~"
        sh "ssh -o StrictHostKeyChecking=no  ec2-user@13.233.166.35 sudo cp /home/ec2-user/*.war /opt/tom7/webapps"
  
}
    
}
    

}
