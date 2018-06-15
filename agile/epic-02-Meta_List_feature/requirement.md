# Meta List feature
Meta List is used for recording data storage information. Data can be any kind of file or folder. For example, We have a zip file of am album and save it somewhere on NAS1. We can record the infomation as:
* **Data Name**: 001.7z
* **Data Location**: nas1/data/album
* **Data Type**: zip
* **Data Content Title**: Lady Gaga's album
* **Tag**: album,lady gaga
* **Relate**: thumbnail:nas1/thumbnail/001.JPG,thumbnail:nas1/thumbnail/002.JPG

Later we can search data when needed. (This will be another feature.)

## UI
* UI must be stand to [General UI Rules]().
* There is action bar with buttons: Add, Delete.
* There is grid which is stand to [General Grid Behaviors]().
* There is footer which contains summary about total select and total data numbers. 

### UI Mock up
![PC]()

![Pad]()

![Smart Phone](/agile/epic-02-Meta_List_feature/images/ui-smart_phone.PNG)

## Files
Basically a data here should be a zip file which may be a folder contains some files or pictures, or a folder or just a file. The files can be related to each other.

## Fields
There are fields for a data, which contains the information for that data.

### Data Name
**Data Name** is used for indecating the target object we handle about. For example, 0001.7z is a file called 0001.7z.
* **Field Name**: Data Name
* **Field Type**: input text	
* **Validation**:
  * **Allowed Characters**: We want data name simple so restrict it to [-\w\_]{1,35}(\\.[\w]{1,4})?. If the real filename obeys this rule, it must be corrected in file system.
  * **Min Length**: 1
  * **Max Length**: 40
  * **Required**: Yes

### Data Location
**Data Location** is the location where the data is stored. It includes storage and full file system path. For example. nas1/data/001.
* **Field Name**: Data Location
* **Field Type**: input text, inform <storage>/<path>
  * storage := name of storage
  * path := full path of file
  * **Validation**: Currently we don't validate the content format, because it is just informational.
    * ** Allowed Characters**: No restriction
    * **Min Length**: 0
    * **Max Length**: TBD
    * **Required**: No

### Data Type
**Data Type** is used to describe the data format. It could be a reqular file, compressed file even a folder. Later we will add new feature to let this field selectable for existing values from other records.
* **Field Name**: Data Type
* **Field Type**: input text, it can be empty.
* **Validation**: N/A
  * **Min Length**: N/A
  * **Max Length**: N/A
  * **Required**: No

### Data Content Title
**Data Content Title** describes the summary of the file. Normally by blick user can know what data is it. For example, for a photo album it could be **Photo album of family. 1017**.
* **Field Name**: File Content Title	
* **Field Type**: input text
* **Validation**: N/A
  * **Min Length**: 0
  * **Max Length**: TBD, may depends on db column setting, or as the same as Jira
  * **Required**: No
	
### Tag
There will be another epic for **Tag** feature. Currently we just record tags seperated by comma. Latter it will be selectable from existing tags.
* **Field Name**: Tag
* **Field Type**: input text
* **Validation**: N/A
  * **Min Length**: 0
  * **Max Length**: TBD, may be just as the same as Jira
  * **Required**: No

### Data Content Description
**Data Content Description** describes more details about data.
* **Field Name**: Data Content Description
* **Field Type**: input text
* **Validation**: N/A
  * **Min Length**: 0
  * **Max Length**: TBD, consult Jira
  * **Required**: No

### Relate
There will be another epic for **Relate** feuture. Currently it is just informational text, for example, thumbnail:nas1/pic/thumbnail/v0001.jpg. Later will add features like link or image preview or sub-grid.
* **Field Name**: Relate
* **Field Type**: input text
* **Validation**: N/A
  * **Min Length**: 0
  * **Max Length**: TBD
  * **Required**: No

## Requirements
### User can add new meta data
* There is Add button on action bar. When user clicks it an empty row will append on the end of the grid.
* Once user mouse focuses on the input field, he can fill out the values.
* Once user mouse unfocuses from the input field the value will be validated (client side).
  * If value is invalid then user will be warned and it will not be saved.
  * If value is valid and all requred fields exist then it will be saved.
  * If value is valid but lacks any requred field then user will be warned and it will not be saved.

### User can edit meta data
* User can edit meta data directly on grid.
    * After mouse unfocuses from column the data is saved on server.
    * Validation of field
	

### User can delete meta data





### Note
* Although filename must be unique in location i.e. file system path but we don't constraint the uniqueness. (I want this system has tolerance for inaccurate information because I want the system simaple. This issue is not a big deal, at least not now.)


---------------------------------------
**this part is for test desgin**
This will be a new feature for BAssistant2, a new project which contains technics:
 developent principle		TDD
 developent control		agile
 OS				LINUX like
 server side			Node.js
 database			SQLite/(maybe also MongoDB? It depends on if it is available for Cygwin and Termux)
 client side			Angular.js + Bootstrap
 API				RestAPI

  * If value is valid then the field values will be sent to server.
  * If value is invalid then user will be warned and the value will not be saved.


