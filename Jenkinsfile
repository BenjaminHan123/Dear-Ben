pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Sleep') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        sleep(time: 1, unit: 'SECONDS')
      }
    }

    stage('LT_test') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        bat(script: '''
  echo "update got and pipeline data"
  set /a is_success_random=%random%
  echo %is_success_random%
  for /f "tokens=1 delims=/" %%i in (\'echo %JOB_NAME%\') do (
    echo %%i
    set job_name=%%i
  )

  echo %job_name%
  curl -X PUT --header "UWA-JENKINS-TOKEN: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsImV4cCI6MTY2MTU2Nzg3M30.W6Snzu1RgrmGl_xnU7saqlkKYrOoi4B8uS39yoyclFSwA5lDs8gFAVFwc1eMM-jYVx0rKl3TByK0-zvIVpeKMg" --data "{    \\"projectId\\": \\"2305\\",    \\"pipelineId\\": \\"8016f6ef-b572-403f-ab33-f8dceb061625\\",    \\"pipelineName\\": \\"%job_name%\\",    \\"branchName\\": \\"%BRANCH_NAME%\\",    \\"buildId\\": \\"%BUILD_ID%\\"  }" http://www.uwapipeline.com/atx/api/v2/task/got -o is_success_%is_success_random%.txt
  for /f "tokens=*" %%c in (is_success_%is_success_random%.txt) do (
    echo %%c
    set is_success=%%c
  )
  if "%is_success%" == "0" (
    echo "update data failed"
    exit
  ) else (
    echo "update data success: %is_success%"
  ) 
              curl -H "Content-Type:application/json" -X POST -d "{\\"exePath\\":\\"C:\\\\Users\\\\vip\\\\Desktop\\\\UWAProjectScan_Unity 2019.1-2021.1_Pipeline\\\\LOCALService.exe\\",\\"unityPath\\":\\"QzpcUHJvZ3JhbSBGaWxlc1xVbml0eVxIdWJcRWRpdG9yXDIwMTkuNC4yNmYxYzFcRWRpdG9yXFVuaXR5LmV4ZQ==\\",\\"projectPath\\":\\"RTpccHBsX0xUdGVzdA==\\",\\"projectName\\":\\"MjMwNQ==\\",\\"type\\":\\"LOCALUPLOAD\\",\\"buildId\\":\\"%BUILD_ID%\\",\\"pipelineName\\":\\"%JOB_NAME%\\",\\"branchName\\":\\"bWFzdGVy\\",\\"computerType\\":\\"MQ==\\"}" http://localhost:9898''', encoding: '', label: '', returnStatus: '', returnStdout: '')
      }
    }

  }
}