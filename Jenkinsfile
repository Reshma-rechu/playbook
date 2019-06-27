node{
 try{
      stage ('Checkout')
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Reshma-rechu/playbook.git']]])
 
      stage ('syntax check')
        sh 'ansible-playbook --syntax-check ./playbook.yml' 
     
      stage ('Run a check for playbook')
        sh '[ -f /var/lib/jenkins/workspace/playbook_task/playbook.yml ] && echo "Found" || echo "Not found"'
  
      stage ('Executing playbook')
        sh 'ansible-playbook playbook.yml'

      echo "BUILD RESULT: ${currentBuild.result}"
    
      } catch (Exception err) {
      echo "BUILD RESULT: ${currentBuild.result}"
      }
} 
