M&amp;S Internal GitHub composite actions

## Summary :

This repository is used to store reusable composite actions that other product teams can use to enhance their github actions pipeline.

## List of Actions and link to use


### CI maven Build and Package Push:

#### call:  DigitalInnovation/cloud-devsecops-pipelineactions/workflows/CI@v1

inputs:

- **pom\_path: .** 				 `{` *path to the pom file default = .* `}`
- **pom\_file\_name: pom.xml** `{` *Pom file name , default = pom.xml* `}`
- **pom\_file\_name: pom.xml** 	`{` *Pom file name , default = pom.xml* `}`
- **build\_tool: maven** 		`{` *build tools you are using, we support maven and gradle more tools will be added* `}`
- **settings\_file\_path: .** 	`{` *maven settings file path if you need push package, default *. `}`
- **settings\_file\_-name: settings.xml** 	`{` *maven settings file name if you need push package, default settings.xml* `}`
- **az\_artifact\_repository\_pat: ${{secrets.AZURE\_ARTIFACT\_PAT}}** 	`{` *you repository token to use for connecting to Azure package repository* `}`

### Push Image built to ACR

#### call: DigitalInnovation/cloud-devsecops-pipelineactions/workflows/push\_image@main

Inputs:

- **cr\_imagename: 'nginx'**  					`{` *docker image name* `}`
- **cr\_imagetag: ${{ github.run\_id }}** 		`{` *docker image tag* `}`
- **cr\_username: ${{ secrets.ACR\_USER }}** 		`{` *containder registry user* `}`
- **cr\_password: ${{ secrets.ACR\_PASS }}** 		`{` *containder registry password* `}`
- **cr\_servername: ${{ secrets.ACR\_SERVER }}** 	`{` *containder registry servername* `}`

### SNYK Scan

#### call: gDigitalInnovation/cloud-devsecops-pipelineactions/workflows/appsec@main

Input:

- **snyk\_token: ${{ secrets.SNYK\_TOKEN }}** 	`{` *snyk token to update the* `}`

### Fortify Scan

#### call: DigitalInnovation/cloud-devsecops-pipelineactions/workflows/Fortify@main

Input:

- **fod\_release\_id: ${{ secrets.FOD\_RELEASE\_ID }}** 	`{` *your FOD project Release ID* `}`
- **fod\_api\_key: ${{ secrets.FOD\_API\_KEY}}** 			`{` *FOD key* `}`
- **fod\_api\_secret: ${{ secrets.FOD\_API\_SECRET}}** 	`{` *FOS secret* `}`
- **project\_name: sample**  							`{` *name of the project ( used to great the zip file)* `}`
- **project\_src\_path: ./src** 						`{` *location of source to Zip for FOS push* `}`

### Coming Soon...

#### Prisma Scan
#### SonarQube
