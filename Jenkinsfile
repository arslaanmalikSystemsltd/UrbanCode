node {
	stage ('Push to UCD...') {
		step([$class: 'UCDeployPublisher',     // Class name of the Jenkins pipeline
			siteName: 'demo2',                // Name of UrbanCode Deploy server
			component: [                      // Actions to perform
			    $class: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
                componentName: 'AppConnect',
                delivery: [                  //  Perform a component version input
                            $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
                            pushVersion: '${BUILD_NUMBER}',  //  Name toassign component version
                            baseDir: '/opt/urbancodegit',  // Base directory containing artifacts
                            fileIncludePatterns: '**/*',    // Files to include using Regex
                            fileExcludePatterns: '',         // Files to exclude using Regex
                            pushProperties: '', // Assign properties to new component version
                            pushDescription: 'Pushed from Jenkins'  //  Description for component version
                ]
			],
			    deploy: [                      //Deploy Action
                            $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeployHelper$DeployBlock',  //Deploy action
                            deployApp: 'AppConnect',      //Name of the application
                            deployEnv: 'New Server',         //Name of the environment
                            deployProc: 'AceappProcess new', //Name of the application process to run
                            deployVersions: 'AppConnect:${BUILD_NUMBER}', //Versions to deploy. Specify multiple on a new line in the format component:version
                            deployOnlyChanged: false
                ]
		])

	}
}
