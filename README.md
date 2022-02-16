#  Export Amazon Cognito User Pool records into CSV

This project allows to export user records to CSV file from [Amazon Cognito User Pool](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-identity-pools.html)

## Instalation

In order to use this script you should have Python 2 or Python 3 installed on your platform
- run `pip install -r requirements.txt` (Python 2) or `pip3 install -r requirements.txt` (Python 3)

## Fetch user pool 
Configure the AWS access keys and run:

``` shell
aws cognito-idp list-users --user-pool-id "us-east-1_XXXXXXXXX"
```

It returns the list of users in JSON.

## Run export

To start export proccess you shout run next command (__Note__: use `python3` if you have Python 3 instaled)
- `$ python CognitoUserToCSV.py  --user-pool-id 'us-east-1_XXXXXXXXX' -attr Username email_verified given_name family_name UserCreateDate`
- Wait until you see output `INFO: End of Cognito User Pool reached`
- Find file `CognitoUsers.csv` that contains all exported users. [Example](https://github.com/hawkerfun/cognito-csv-exporter/blob/master/CognitoUsers.csv) 

### Script Arguments

- `--user-pool-id` [__Required__] - The user pool ID for the user pool on which the export should be performed
- `-attr` or `--export-attributes` [__Required__] - List of Attributes that will be saved in CSV file
- `--region` [_Optional_] - The user pool region the user pool on which the export should be performed _Default_: `us-east-1`
- `-f` or `--file-name` [_Optional_] - CSV File name or path. _Default_: `CognitoUsers.csv`
- `--num-records` [_Optional_] - Max Number of Cognito Records tha will be exported. _Default_: __0__ - All

###### Note:

If you need to Back up your intire cognito instance pool, take a look for this tool: https://www.npmjs.com/package/cognito-backup-restore
