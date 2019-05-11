Pipeline {
	
	any agent { 

		Stages 	{
			Stage ('SCM Checkout') {
			git 'https://github.com/prasadblad/maven-project.git'}
			
			Stage('compile source code'){
				Steps{
					withmaven(maven: 'LocalMaven'){
					sh 'mvn compile'
				}}
			Stage('test'){
				Steps{
					withmaven(maven: 'LocalMaven'){
					sh 'mvn test'
				}}
			Stage('package'){
				Steps{
					withmaven(maven: 'LocalMaven'){
					sh 'mvn package'
				}}
			Stage('Install'){
				Steps{
					withmaven(maven: 'LocalMaven'){
					sh 'mvn install
				}}		
		}}
