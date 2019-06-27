node {
	      try {
	              stage 'Checkout'
	                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Reshma-rechu/playbook.git']]])
	       
	              stage 'Syntax Check'
	                sh 'ansible-playbook --syntax-check ./playbook.yml' 
	       
	              stage ('Run a check for playbook')
                        sh '[ -f /var/lib/jenkins/workspace/playbook_task/playbook.yml ] && echo "Found" || echo "Not found"'
	       
	              stage 'Execute playbook'
	                sh 'ansible-playbook playbook.yml'
	              
	              currentBuild.result = 'SUCCESS'
	           }   catch (Exception err) {
	                currentBuild.result = 'FAILURE'
	            }
	              echo "BUILD : ${currentBuild.result}"       
}


