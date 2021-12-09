

import stage.Constants

@Library('lib-core@4.0.3') _
pipeline {
	agent {
        node {
            label "TAS_builder_10.2.45.27"
            customWorkspace "E:\\Jenkins\\testFile"
        }
    }
	
	options {
        skipDefaultCheckout(true)
    }
    
    triggers {
        cron "H 6 * * *"
    }
	
	environment {
		branchname = "main"
	}

    stages{
        stage('删除外链'){
            steps{
                script{
                    echo("删除外链")
                    Map parameters = [returnStatus:true]
                }
            }
        }
		stage('拉取代码'){
			steps{
				echo("拉取分支(${branchname})代码")
				script{
						echo("stageScm")
					}
			}
		}
		
		stage('切分支'){
			steps{
				echo("切分支")
				echo("branchname = ${branchname}")
			}
		}
		
		stage('创建外链'){
		    steps{
		        script{
		            echo("执行gclcopy")
		        }
		    }
		}
		
        stage('架构度量'){
            steps {
				echo("架构度量")
				script
				{
					echo "${branchname}"
				}
            }
        }
    }
	post{
	    success{
	        echo 'I will always say Hello again!'
			script{
			        echo("success")
				}
	    }
		failure{
	        echo 'run failure, please check!'
	    }
	}
}