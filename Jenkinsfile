pipeline
{
   agent 
            {
               label 'agent2'
            }
    tools
       {
           maven 'Maven3.6'
          jdk 'Java1.8'
           
       }
 stages
     {
          stage ('GIT CHECKOUT')
                   {
                       steps
                            {
                                 step([$class: 'WsCleanup'])
                                 
                                 echo "Clonning the code"
                                 checkout([$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/Bkumar89/Sampledemoproject.git']]])
                             }
                     
                    }
          stage ('BUILD')
                   {
                       steps
                            {
                                 withEnv(["JAVA_HOME=${ tool 'Java1.8' }"])
                                  {
                                      script
                                       {
                                            def mavenhome=tool 'Maven3.6'
                                            def Java=tool 'Java1.8'
                                            sh "mvn -f ${WORKSPACE}/pom.xml clean install"
                                        }
                                        
                                   }
                             }
                     
                    }
          stage ('SONAR-SCAN')
                   {
                       steps
                            {
                              script
                              {
                                 echo('code scaning')
                              }
                            }
                     
                    }
      }
}
