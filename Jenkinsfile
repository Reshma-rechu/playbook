node {
	      try {
	              stage 'Checkout'
	                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Reshma-rechu/playbook.git']]])
	       
	              stage 'Syntax Check'
	                sh 'ansible-playbook --syntax-check ./playbook.yml' 
	       
	              stage 'Check for playbook'
	                if (fileExists('playbook.yml')) {
	                  echo 'Playbook exists'
	                } 
	                else 
	                {
	                  echo 'Playbook doesnot exists'
	                }
	       
	              stage 'Execute playbook'
	                sh 'ansible-playbook playbook.yml'
	              
	              currentBuild.result = 'SUCCESS'
	           }   catch (Exception err) {
	                currentBuild.result = 'FAILURE'
	            }
	              echo "BUILD RESULT: ${currentBuild.result}"       
}


