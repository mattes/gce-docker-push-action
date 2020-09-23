# Google Cloud Container Registry Docker Push

Github action to push a docker image to [Google Cloud's Container Registry](https://cloud.google.com/container-registry). 

## Prerequisites

Set up the following resources manually in the Cloud Console 
or use a tool like [Terraform](https://www.terraform.io).

* Enable Container Registry API
* Create Service Account with Role `Storage Admin` and export a new JSON key.


## Github Action Inputs

| Variable                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `creds`                          | ***Required*** Service Account JSON Key (not base64 encoded)                |
| `src`                            | ***Required*** Source Image                                                 |
| `dst`                            | ***Required*** Destination Image                                            |
| `registry`                       |  Registry host name (must match destination image), default: "gcr.io"       |


## Example Usage

```
uses: mattes/gce-docker-push-action@v1
with:
  creds: ${{ secrets.GOOGLE_APPLICATION_CREDENTIALS }}
  src: org/local-image:build
  dst: gcr.io/my-project/my-image:latest
```

