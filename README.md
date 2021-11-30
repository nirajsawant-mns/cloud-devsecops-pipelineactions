# Cloud DevSecOps Composite actions repository
![Public repository attention](https://img.icons8.com/ios/32/000000/error--v1.png)
**Please note** this repository is **Public** and as such no sensitive data should be stored. 

## Summary :

This repository is used to store reusable composite actions that other product teams can use to enhance their github actions pipeline.

## List of Actions and link to use


### CI maven Build and Package Push:

#### call:  DigitalInnovation/cloud-devsecops-pipelineactions/workflows/CI@latest

inputs:
- **build\_tool: maven**  -- Required		`{` *build tools you are using, we support maven and gradle more tools will be added* `}`
- **pom\_path: .** 				 `{` *path to the pom file default = .* `}`
- **pom\_file\_name: pom.xml** `{` *Pom file name , default = pom.xml* `}`
- **settings\_file\_path: .** 	`{` *maven settings file path if you need push package, default *. `}`
- **settings\_file\_name: settings.xml** 	`{` *maven settings file name if you need push package, default settings.xml* `}`
- **build\_phases: clean deploy**  `{` *stages to run as part of the build* `}`
- **maven\_build\_arguments: "-Dkey1=value1 -Dkey2=value2 .." **  `{` *additional maven arguments to be passed for the build execution* `}`
- **az\_artifact\_repository\_pat: ${{secrets.AZURE\_ARTIFACT\_PAT}}** 	`{` *you repository token to use for connecting to Azure package repository* if not already in setting.xml`}`
- 
- **run\_code\_analysis:: true/false**  `{` *Flag to run Code Quality Scan* `}`
- **cq_project_key: CMTEST**  `{` *codeQulaity project key* `}`
- **cq_host_url: clean deploy**  `{` *Url of the Code Scanner Destination* `}`
- **cq_token: clean deploy**  `{` *Token to authenticate to the Project `}`

### Push Image built to ACR

#### call: DigitalInnovation/cloud-devsecops-pipelineactions/workflows/push\_image@latest

- **cr\_imagename: 'nginx'**  					`{` *docker image name* `}`
- **cr\_imagetag: ${{ github.run\_id }}** 		`{` *docker image tag* `}`
- **cr\_username: ${{ secrets.ACR\_USER }}** 		`{` *container registry user* `}`
- **cr\_password: ${{ secrets.ACR\_PASS }}** 		`{` *container registry password* `}`
- **cr\_servername: ${{ secrets.ACR\_SERVER }}** 	`{` *container registry servername* `}`
- **cr_dockerfile_name: Dockerfile** 	`{` *dockerfile name* `}`
- **cr_dockerfile_path: ci-helper/** 	`{` *relative path of the docker file* `}`
- **cr_subscription: ${{ secrets.ACR\_subscription }}** 	`{` *container registry subscription* `}`  
- **cr_tenant: ${{ secrets.ACR\_tenant }}** 	`{` *container registry tenant* `}`  

 

#### call: DigitalInnovation/cloud-devsecops-pipelineactions/workflows/appsec@latest

### Parameters for Dependency (SNYK) Scan

- **run_dependency_scan: true/false** 	`{` *flag to execute dependency scan* `}`
- **dependency\_scan\_token: ${{ secrets.SNYK\_TOKEN }}** 	`{` *snyk token * `}`
- **dependency\_scan\_arguments: -Dkey=value** 	`{` *snyk maven arguments to pass* `}`

### parameters for SAST (Fortify) Scan

- **run_sast_scan: true/false** 	`{` *flag to execute sast scan* `}`
- **sast\_release\_id: ${{ secrets.FOD\_RELEASE\_ID }}** 	`{` *your FOD project Release ID* `}`
- **sast\_api\_key: ${{ secrets.FOD\_API\_KEY}}** 			`{` *FOD key* `}`
- **sast\_api\_secret: ${{ secrets.FOD\_API\_SECRET}}** 	`{` *FOS secret* `}`
- **project\_name: sample**  							`{` *name of the project ( used to great the zip file)* `}`
- **project\_src\_path: ./src** 						`{` *location of source to Zip for FOS push* `}`

#### Parameters for Container(Prisma) Scan

- **run_container_scan: true/false** 	`{` *flag to execute container scan* `}`
- **container_scan_user: ${{ secrets.username}}** 			`{` *container scan url user* `}`
- **container_scan_password: ${{ secrets.password}}** 	`{` *container scan url password* `}`
- **container_scan_url: sample**  							`{` *url of the container scan tool* `}`
- **docker_image_name: ./src** 						`{` *docker image name to scan* `}`
- **docker_image_tag: ./src** 						`{` *docker image tag to scan* `}`


