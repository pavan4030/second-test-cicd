pipeline {
agent any
stages {
stage(‘Build Application’) {
steps {
bat ‘mvn clean package -DmuleDeploy -Dusername=pavan4030 -Dpassword=gayiChittu@123 -Denv=dev -DworkerType=Micro -Dworkers=1 -DcloudHub.Environemnt=TEST -Dregion=us-east-1’
}
}
 stage ('Push Artifact') {
            steps {
                echo 'mkdir archive'
                echo 'echo test > archive/test.txt'
                archiveArtifacts artifacts: target/**/*, fingerprint: true
            }
        }
stage(‘Deploy CloudHub’) {
environment {
ANYPOINT_CREDENTIALS = credentials(‘anypointPlatform’)
}
steps {
echo ‘Deploying mule project’
echo ‘Deploying to the configured environment….’
bat ‘mvn package deploy -DmuleDeploy -Dusername=pavan4030 -Dpassword=gayiChittu@123 -Denv=dev -DworkerType=Micro -Dworkers=1 -DcloudHub.Environemnt=TEST -Dregion=us-east-1’ 
}
}
}
}