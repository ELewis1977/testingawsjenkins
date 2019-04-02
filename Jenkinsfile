pipeline {
	agent any
	
	environment {
		GIT_REPO = "ssh://github.com/ELewis1977/testingawsjenkins/"
		PROJECT = "testingawsjenkins"
		EMAILLIST = "ewen@sky.com"
		USER = "ewen"		
		MSTEAM_WEBHOOK = "https://outlook.office.com/webhook/543299a8-9829-4f85-8af7-da4a4da93134@a7f35688-9c00-4d5e-ba41-29f146377ab0/IncomingWebhook/de5edbf54c8943c693291233fb8314a4/189f02ed-8c3d-41f9-af2e-e7aff6a7eeb0"
	}
	
	//Wildcards should not be used after this point in the templace this should be Grovey code and should use the global environment varibables
	stages {
	  stage ('GIT Test Project Checkout'){
		steps {
			git([url: "${env.GIT_REPO}", branch: 'master', credentialsId: '5cb2b674-9cbf-445b-b679-1b2f9943297c'])
			office365ConnectorSend message: "${env.STAGE_NAME}", webhookUrl: "${env.MSTEAM_WEBHOOK}";
		}
	  }
	  
	  stage ('Testing'){
		steps {
			echo "Start Testing ${env.PROJECT}"
			office365ConnectorSend message: "${env.STAGE_NAME}", webhookUrl: "${env.MSTEAM_WEBHOOK}";
		}
	  }
	  
		
	  stage ('Acceptance Testing'){
		steps {
			echo "Acceptance Testing "
			office365ConnectorSend message: "${env.STAGE_NAME}", webhookUrl: "${env.MSTEAM_WEBHOOK}";
		}
	  }
	  
	  stage ('Approval'){
		steps {
			echo "Approval ${env.EMAILLIST}"
			office365ConnectorSend message: "${env.STAGE_NAME}", webhookUrl: "${env.MSTEAM_WEBHOOK}";
		}
	  }
	  
	  stage ('Deployed'){
		steps { 
		  echo "Deploy Completed ${env.USER}"
		  office365ConnectorSend message: "${env.STAGE_NAME}", webhookUrl: "${env.MSTEAM_WEBHOOK}";
		 }
	  }
	}
}
