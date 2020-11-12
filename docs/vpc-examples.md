# Virtual Private Cloud API
Examples for interacting with the IBM Cloud VPC API.

**Endpoints**
The endpoint is based on the region of the service and follows the convention https://REGION.iaas.cloud.ibm.com. For example, when IBM Cloud VPC is hosted in Dallas, the base URL is https://api.us-south.iaas.cloud.ibm.com. VPC Region Endpoints

**Versioning**
API requests require a major version in the path (/v1/) and a date-based version as a query parameter in the format version=YYYY-MM-DD. You can use any date-based version up to the current date. Start development of new applications with the current date as a fixed value. See the VPC API Change Log for API changes.

## Create a VPC
```
curl --location --request POST 'https://us-south.iaas.cloud.ibm.com/v1/vpcs?version=YYYY-MM-DD&generation=2' \
--header 'Authorization: IAM_TOKEN' \
--data-raw '{
    "address_prefix_management": "auto",
    "name": "VPC_NAME",
    "resource_group": {
        "id": "RESOURCE_GROUP_ID"
    }
}'
```