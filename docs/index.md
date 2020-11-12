# Welcome to IBM Cloud REST API Examples
In order to interact with the various IBM Cloud REST API's you will need to use an IAM Bearer Token. Tokens support authenticated requests without embedding service credentials in every call. In order to generate an IAM Bearer Token you will need your IBM Cloud [API Key](https://cloud.ibm.com/docs/account?topic=account-userapikey#userapikey). 

> It is recommended to install [jq](https://stedolan.github.io/jq/) in order to filter the output of various API calls.

## Generating a Bearer Token
```shell
export IBMCLOUD_API_KEY='Your API Key'

curl -s -k -X POST --header "Content-Type: application/x-www-form-urlencoded" \
--header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
--data-urlencode "apikey=${IBMCLOUD_API_KEY}" "https://iam.cloud.ibm.com/identity/token" \
| jq -r '(.token_type + " " + .access_token)'
```

## Set IAM Token as environmental variable
The following example will set the Bearer token as the environmental variable `iam_token`

```shell 
export IBMCLOUD_API_KEY='Your API Key'

iam_token=`curl -s -k -X POST --header "Content-Type: application/x-www-form-urlencoded" \
--header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
--data-urlencode "apikey=${IBMCLOUD_API_KEY}" "https://iam.cloud.ibm.com/identity/token"  \
| jq -r '(.token_type + " " + .access_token)'`
```