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
- [NEWMAN](https://www.npmjs.com/package/newman)


## Setup and running the test suit
Here you can find env variables in `Dev.postman_environment.json` and tests in `DropboxTestingHT2.postman_collection.json`

1. Clone this repo
2. Assign CLIENT_ID, CLIENT_SECRET and REFRESH_TOKEN in `Dev.postman_environment.json`
The full instruction of getting refresh token is [here](https://www.dropboxforum.com/t5/Dropbox-API-Support-Feedback/Get-refresh-token-from-access-token/td-p/596739#:~:text=It's%20not%20possible%20to%20get,only%20returns%20an%20access%20token.))
3. Run these tests with `npm run test`

- POSTMAN Link:
This collection is available on Postman for import `https://www.getpostman.com/collections/1090c70eaed21acf3b54` without env variables
