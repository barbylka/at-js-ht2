# AT_JS_HT2
**Testing Dropbox API with Postman**

This project was created in order to provide functional test automation of 3 scenarios (below) for [Dropbox API](https://www.dropbox.com/developers/documentation/http/documentation).


## Scenarios

* #1 scenario - Upload a file:
**precondition: script must authorize in the site with the credentials specified in the collection variables, the path to the file is defined (i.e. in collection variables).**

Scenario:

1. Upload the file (max size - 150MB) with POST request to `https://content.dropboxapi.com/2/files/upload`
2. Check the response status is 200 and the path from the request and the response are the same
3. Save a file hash in the collection variables from the response

*Comments: details of this API request are [here](https://www.dropbox.com/developers/documentation/http/documentation#files-upload)

* #2 scenario - Get metadata of a file:
**precondition: script must authorize in the site with the credentials specified in the collection variables, file hash of the uploaded file is saved (i.e. in collection variables), the path to the file is defined (i.e. in collection variables).**

Scenario:

1. GET request with path to the file to `https://api.dropboxapi.com/2/files/get_metadata`
2. Check the response status is 200 and file hash from the request and the response are the same

*Comments: details of this API request are [here](https://www.dropbox.com/developers/documentation/http/documentation#files-get_metadata)

* #3 scenario - Delete a file:
**precondition: script must authorize in the site with the credentials specified in the collection variables, the path to the file is saved (i.e. in collection variables).**

Scenario:

1. DELETE request to `https://api.dropboxapi.com/2/files/delete_v2` and path to the file in the body
2. Check the response status is 200

*Comments: details of this API request are [here](https://www.dropbox.com/developers/documentation/http/documentation#files-delete)


## Technology used

- [POSTMAN](https://www.postman.com/)


## Setup and running the test suit

**! Make sure: in collection or env variables you set CLIENT_ID and CLIENT_SECRET of your dropbox app**
**UPD!** 0. Set your AUTHORIZATION_CODE variable. Read below how to get it:

1. Make your OAuth app authorization URL like this: (plug in your app ID in place of "APPKEYHERE").
`https://www.dropbox.com/oauth2/authorize?client_id=APPKEYHERE&response_type=code&token_access_type=offline`
2. Browse to that page in your browser while signed in to your account and click "Allow" to authorize it.
3. Copy the resulting authorization code and add it as AUTHORIZATION_CODE collection or env variable. Note! This's a short life code data.

- To open these tests in POSTMAN:
1. Import to your workspace this collection via link `https://www.getpostman.com/collections/fab21276b8b04f2316f8` or open the file "DropboxTestingHT2_with_authCode.postman_collection" from your cloned version of this proj
2. Set your AUTHORIZATION_CODE variable
3. Run the collection

- If you have NEWMAN on your machine:
Run these tests with `newman run https://www.getpostman.com/collections/fab21276b8b04f2316f8`


In case of stuck: the full instruction of AUTHORIZATION_CODE is [here](https://www.dropboxforum.com/t5/Dropbox-API-Support-Feedback/Get-refresh-token-from-access-token/td-p/596739#:~:text=It's%20not%20possible%20to%20get,only%20returns%20an%20access%20token.))
