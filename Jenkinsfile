node{
   stage ('Checkout')
     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Reshma-rechu/playbook.git']]])
 
  stage ('syntax check')
     sh 'ansible-playbook --syntax-check ./playbook.yml' 
 }
