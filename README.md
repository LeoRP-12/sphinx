# Hello, people.

This repository is just a study of how to use the sphinx tool to document codes, the result of this study you can check at the link : [https://leorp-12.github.io/sphinx/](https://leorp-12.github.io/sphinx/)

# Workflow


![workflow](https://i.imgur.com/ANfdNDg.png)

You can generate html codes with the command:

``sphinx-build source docs``

the ``conf.py`` file has general configurations, this example uses ``sphinx-rtd-theme`` that's provide read the docs theme
and ``myst-parser`` to parse markdown files.

you can also use ``sphinx-multiversion`` to generate different versions of the documentation for each release


# Deploy

For this repository example I use github pages to deploy html files.

A deployment strategy is to generate the html files and copy them to a blob that makes the html available in a URL

for example using an Azure Cloud blob storage the `azure-pipeline.yaml` could be:

```yaml

 - job: Docs
        displayName: 'Deploy Docs'
        dependsOn: Test
        condition: and(succeeded('Test'), startsWith(variables['Build.SourceBranch'], 'refs/heads/master'))
        pool:
          vmImage: 'windows-latest'
        steps:
          - task: UsePythonVersion@0
            displayName: "Set python version to 3.7"
            inputs:
              versionSpec: '3.7'
              architecture: 'x64'
          - script: |
              pip install -r requirements.txt
              cd docs
              sphinx-multiversion source build
            displayName: 'Create HTML Files'
          - bash: |
              pip install python-semantic-release===7.16.1
              cp docs/source/_templates/redirect_index.html docs/build/index.html
              sed -i -- "s/master/v$(semantic-release print-version --current)/g" docs/build/index.html
            displayName: 'Add redirect_index file'
          - task: AzureFileCopy@4
            displayName: 'AzureBlob HTML Files Copy'
            inputs:
              SourcePath: 'docs/build/*'
              azureSubscription: 'blob_subscription_name'
              Destination: AzureBlob
              storage: 'blob_name'
              ContainerName: '$web'
              additionalArgumentsForBlobCopy: --recursive=true
```
