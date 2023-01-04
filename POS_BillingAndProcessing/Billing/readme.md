# Point of Sale Data Processing Project

## Development of batch data processing application
* The data for products lookup is in `masterdata\products.csv`
* Source data is in 3 zip files about 100k files
    * `batch_1_bills.zip`
    * `batch_2_bills.zip`
    * `batch_3_bad_bills.zip`

### Project objectives
* Create Billing and Billing Details Tables
* Develop DB routines to bulk load the billing data to Billing and Billing Details Tables
* Develop Python application to load billing data to Billing and Billing Details Tables
* Develop all exception scenarios for bad_bills

## Development of realtime data processing application


1. Create a BillGenerator.py script
    Generate a JSON with the following structure
        - ProdID should be between 1 and 25
        - StoreID should be between 1 and 4
        - Qty should be between 1 and 20

    { "BillID":1
     ,"BillDate":"dd/mm/yyyy hh24:mi:ss"
     ,"StoreID":1
     ,"BillDetails": {1:2    # prod:qty
                     ,2:33}
                    ]
    }
    
    - Create a Prod Lookup
    [ {"ProdID":1,"ProdCategory":"Fruits","ProductName":"Apple","UnitPrice":2}
     ,{"ProdID":2,"ProdCategory":"Fruits","ProductName":"Banana","UnitPrice":1}
     ,{"ProdID":3,"ProdCategory":"Office","ProductName":"Paper","UnitPrice":5}
    . . . .
    ]

2. Save this JSON a file BillID.json
3. generate 1 File for every 3 seconds

4. Bill Processor
    2 CSV Files
        Bills.csv       File = BillID,BillDate,StoreID,BillTotal
        BillDetails.csv File = BillID,ProductName,Qty,LineTotal
