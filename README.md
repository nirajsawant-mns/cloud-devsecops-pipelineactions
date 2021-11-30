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

Inputs:

- **cr\_imagename: 'nginx'**  					`{` *docker image name* `}`
- **cr\_imagetag: ${{ github.run\_id }}** 		`{` *docker image tag* `}`
- **cr\_username: ${{ secrets.ACR\_USER }}** 		`{` *containder registry user* `}`
- **cr\_password: ${{ secrets.ACR\_PASS }}** 		`{` *containder registry password* `}`
- **cr\_servername: ${{ secrets.ACR\_SERVER }}** 	`{` *containder registry servername* `}`

### SNYK Scan

#### call: gDigitalInnovation/cloud-devsecops-pipelineactions/workflows/appsec@latest

Input:

- **snyk\_token: ${{ secrets.SNYK\_TOKEN }}** 	`{` *snyk token to update the* `}`

### Fortify Scan

#### call: DigitalInnovation/cloud-devsecops-pipelineactions/workflows/Fortify@latest

Input:

- **fod\_release\_id: ${{ secrets.FOD\_RELEASE\_ID }}** 	`{` *your FOD project Release ID* `}`
- **fod\_api\_key: ${{ secrets.FOD\_API\_KEY}}** 			`{` *FOD key* `}`
- **fod\_api\_secret: ${{ secrets.FOD\_API\_SECRET}}** 	`{` *FOS secret* `}`
- **project\_name: sample**  							`{` *name of the project ( used to great the zip file)* `}`
- **project\_src\_path: ./src** 						`{` *location of source to Zip for FOS push* `}`

#### Prisma Scan

- **run_container_scan: ${{ secrets.FOD\_RELEASE\_ID }}** 	`{` *your FOD project Release ID* `}`
- **container_scan_user: ${{ secrets.FOD\_API\_KEY}}** 			`{` *FOD key* `}`
- ** container_scan_password: ${{ secrets.FOD\_API\_SECRET}}** 	`{` *FOS secret* `}`
- **container_scan_url: sample**  							`{` *name of the project ( used to great the zip file)* `}`
- **docker_image_name: ./src** 						`{` *location of source to Zip for FOS push* `}`
- **docker_image_tag: ./src** 						`{` *location of source to Zip for FOS push* `}`


