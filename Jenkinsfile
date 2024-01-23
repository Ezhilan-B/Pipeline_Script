pipeline{
    agent none
    
    stages{
        
        stage("git checkout"){
            parallel{
                stage('Git Checkout on windows_node'){
                    agent{
                        label 'windows_node'
                    }
                    steps{
                        echo "Checking out from git";
                        git 'https://github.com/simplilearn-github/Pipeline_Script.git'
                    }
                    post{
                        success{
                            echo "Checkout Success";
                        }
                        failure{
                            echo "Checkout failed";
                        }
                        unstable{
                         echo "Checkout unstable";
                        }
                    }
                }
                
                stage('Git Checkout on master node'){
                    agent{
                        label 'windows_node'
                    }
                    steps{
                        echo "Checking out from git";
                        git 'https://github.com/simplilearn-github/Pipeline_Script.git'
                    }
                    post{
                        success{
                            echo "Checkout Success";
                        }
                        failure{
                            echo "Checkout failed";
                        }
                        unstable{
                         echo "Checkout unstable";
                        }
                    }
                }
            }
            
            
        }
        stage('Parallel run 1'){
            parallel{
                stage('build on windows_node'){
                    agent{
                        label 'windows_node'
                    }
                    steps{
                        echo "Build Build.bat file";
                        bat 'Build.bat'
                    }
                    post{
                        success{
                            echo "Build Success";
                        }
                        failure{
                            echo "Build failed";
                        }
                        unstable{
                         echo "Build unstable";
                        }
                    }
                }
                    
                stage('Unit on built-in node'){
                    agent{
                        label 'master'
                    }
                    steps{
                        echo "Build Unit.bat file";
                        bat 'Unit.bat'
                    }
                    post{
                        success{
                            echo "Unit Success";
                        }
                        failure{
                            echo "Unit failed";
                        }
                        unstable{
                         echo "Unit unstable";
                        }
                    }
                }
            }
        }
        
        stage('Parallel run 2'){
            parallel{
                stage("Quality"){
                    agent{
                        label 'master'
                    }
                    steps{
                        echo "Build Quality.bat file";
                        bat "Quality.bat"
                    }
                    post{
                        success{
                            echo "Quality Success";
                        }
                        failure{
                            echo "Quality failed";
                        }
                        unstable{
                         echo "Quality unstable";
                        }
                    }
                }
                
                stage("Deploy"){
                    agent{
                        label 'windows_node'
                    }
                    steps{
                        echo "Build Deploy.bat file";
                        bat "Deploy.bat"
                    }
                    post{
                        success{
                            echo "Deploy Success";
                        }
                        failure{
                            echo "Deploy failed";
                        }
                        unstable{
                         echo "Deploy unstable";
                        }
                    }
                }
            }
        }
    }
    
    post{
        success{
            echo "All Stages Success";
        }
        failure{
            echo "Stages failed";
        }
        always{
            echo "run always";
        }
        unstable{
            echo "Stages unstable";
        }
    }
}
