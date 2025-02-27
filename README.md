# 'Order to Cash' process

## Create Sales Order (VA01)
### OData Service
* https://api.sap.com/api/OP_API_SALES_ORDER_SRV_0001/overview
* https://{host}:{port}/sap/opu/odata/sap/API_SALES_ORDER_SRV
* Sample Payload:
```http
# Fetch X-CSRF-Token
# @name FetchReply
GET https://server:port/sap/opu/odata/sap/API_SALES_ORDER_SRV/A_SalesOrder('1')?$format=json
Authorization: Basic {{username}}:{{password}}
X-CSRF-Token: Fetch

# Create Sales Order
POST https://server:port/sap/opu/odata/sap/API_SALES_ORDER_SRV/A_SalesOrder
Content-Type: application/json
Authorization: Basic {{username}}:{{password}}
X-CSRF-Token: {{FetchReply.response.headers.x-csrf-token}}

{
    "SalesOrder": "0005000006",
    "SalesOrderType": "OR",
    "SalesOrganization": "1010",
    "DistributionChannel": "10",
    "OrganizationDivision": "00",
    "SoldToParty": "10100001",
    "PurchaseOrderByCustomer": "Customer 123",
    "to_Item": [
    {
        "SalesOrderItem": "10",
        "SalesOrderItemCategory": "TAN",
        "Material": "TG11",
        "RequestedQuantity": "5"
      }
    ]
}
```

## Deliver the goods (VL01N)

## Billing The Sales Order (VF01)

## Release Billing Document to FI Accounting (VF02)

## Check The Invoice (FB03)

## Process Incoming Payment (F-28)