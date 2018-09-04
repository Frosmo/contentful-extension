# Contentful UI extension for Frosmo
Allows Contentful users to select which Frosmo modification(s) are tied to the content they're editing. 
Code is only an example and is based on https://github.com/contentful/extensions/tree/master/samples/optimizely-audiences.


## Pre-requisites
-You need to have Contentful account & need to know your spaceId
-You need to have Graniitti token & siteId

## Install instructions
- Install contentful-cli `npm install -g contentful-cli``
- Edit extension.json and add (Graniitti) token & siteId
- run `contentful extension create --descriptor extension.json --srcdoc index.html --space-id [YOUR SPACE ID]`
- Extension should be added to your Contentful space

### Updating extension
Force update:
`contentful extension update --descriptor extension.json --srcdoc index.html --space-id [YOUR SPACE ID] --force`

## Usage in Contentful

### Add to content model
- Go to "Content model" -> add field 
- Select "JSON object" -> give field name (eg. Frosmo modification) -> Click "Create and configure" -> Select "Appearance" -> "Frosmo audiences"
- Go and edit content -> you should see "Frosmo modification" multi-select box listing all modifications for the site you configured in extension.json


## Usage in Frosmo
- Contentful API needs to be queried to match the modification field, eg. (fields.frosmo contains Frosmo modificationId):
https://cdn.contentful.com/spaces/[SPACE_ID]/entries?content_type=[CONTENT_TYPE]&fields.frosmo=[MODIFICATION_ID]&select=fields&access_token=[ACCESS_TOKEN]
- This query can be made eg. in custom renderer
