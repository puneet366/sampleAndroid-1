node {



    def isMainline = ["develop", "master"].contains(env.BRANCH_NAME)



    List environment = [

        "GOOGLE_APPLICATION_CREDENTIALS=/home/ubuntu/fqdemo-service-credentials-key.json"

    ]



    stage('Checkout') {

        // Pull the code from the repo

        checkout scm

    }



    stage('Clean') {

        sh "./gradlew clean"

    }



    



    stage 'Build Release'

        sh "./gradlew assemble"





   if (isMainline) {



       



          stage ('Distribute') {

              withEnv(environment) {

                  sh "./gradlew assemble appDistributionUpload"

              }

          }



    }



}
