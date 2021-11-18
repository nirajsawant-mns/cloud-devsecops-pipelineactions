# mns-central-actions
M&amp;S Internal GitHub composite actions

Summary :
This Repository is used to store all composite actions that other projects and applicaiton teams can use to enhance their github actions pipeline.

List of Actions and link to use


CI maven Build and Package Push:
call:  DigitalInnovation/mns-central-actions/workflows/CI@v1
inputs:
   pom_path: . # path to the pom file default = .
   pom_file_name: pom.xml # Pom file name , default = pom.xml
   build_tool: maven # build tools you are using, we support maven and gradle more tools will be added
   settings_file_path: . # maven settings file path if you need push package, default .
   settings_file_-name: settings.xml # maven settings file name if you need push package, default settings.xml
   az_artifact_repository_pat: ${{secrets.AZURE_ARTIFACT_PAT}} # you repository token to use for connecting to Azure package repository
 
 Push Image built to ACR
    call: DigitalInnovation/mns-central-actions/workflows/push_image@main
    Inputs:
      cr_imagename: 'nginx'  #docker image name
      cr_imagetag: ${{ github.run_id }} # docker image tag 
      cr_username: ${{ secrets.ACR_USER }} # containder registry user
      cr_password: ${{ secrets.ACR_PASS }} # containder registry password
      cr_servername: ${{ secrets.ACR_SERVER }} # containder registry servername

SNYC Scan
   call: gDigitalInnovation/mns-central-actions/workflows/appsec@main
   Input:
      snyk_token: ${{ secrets.SNYK_TOKEN }} # snyk token to update the 

Fortify Scan
   call: DigitalInnovation/mns-central-actions/workflows/Fortify@main
      with:
        fod_release_id: ${{ secrets.FOD_RELEASE_ID }} # your FOD project Release ID
        fod_api_key: ${{ secrets.FOD_API_KEY}} # FOD key
        fod_api_secret: ${{ secrets.FOD_API_SECRET}} # FOS secret
        project_name: sample  # name of the project ( used to great the zip file)
        project_src_path: ./src # location of source to Zip for FOS push
        
