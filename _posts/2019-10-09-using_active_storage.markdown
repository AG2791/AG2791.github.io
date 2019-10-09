---
layout: post
title:      "Using Active Storage"
date:       2019-10-09 22:57:21 +0000
permalink:  using_active_storage
---


Prior to Rails 5 storing and managing  user files relied heavily on the use of third party gems like Paperclip, but Rails 5 now comes prepacked with  Active Storage. 
“Active Storage facilitates uploading files to a cloud storage service like Amazon S3, Google Cloud Storage, or Microsoft Azure Storage and attaching those files to Active Record objects.”  It can also be easily configured to run on locally. Thanks to more Ruby “magic”, Active Storage is relatively easy to set up. 

**1)	Setting Up Active Storage** 

Once your app is created run the following:
```
$ rails active_storage:install
$ rails db:migrate
```


This will create two tables: active_storage_blobs and active_storage_attachments  

active_storage_blobs – a table to maintain Binary Large object(BLOB) files(e.g. images, video, etc)

active_storage_attachments  - acts like a join table between models and BLOB files.  This is a nice feature as it doesn’t require us to manually create another column to connect the BLOB to current models. 

**2)	config/storage.yml**

Head over to your config/storage.yml file. Here you can configure where your data is stored, local or whatever cloud service you wish. Also note that you can use the mirror configuration to save files to multiple cloud services. The below storage config shows a local environment set up.

```
test:
  service: Disk
  root: <%= Rails.root.join("tmp/storage") %>

local:
  service: Disk
  root: <%= Rails.root.join("storage") %>
  

# Use rails credentials:edit to set the AWS secrets (as aws:access_key_id|secret_access_key)
# amazon:
#   service: S3
#   access_key_id: <%= Rails.application.credentials.dig(:aws, :access_key_id) %>
#   secret_access_key: <%= Rails.application.credentials.dig(:aws, :secret_access_key) %>
#   region: us-east-1
#   bucket: your_own_bucket

# Remember not to checkin your GCS keyfile to a repository
# google:
#   service: GCS
#   project: your_project
#   credentials: <%= Rails.root.join("path/to/gcs.keyfile") %>
#   bucket: your_own_bucket

# Use rails credentials:edit to set the Azure Storage secret (as azure_storage:storage_access_key)
# microsoft:
#   service: AzureStorage
#   storage_account_name: your_account_name
#   storage_access_key: <%= Rails.application.credentials.dig(:azure_storage, :storage_access_key) %>
#   container: your_container_name

# mirror:
#   service: Mirror
#   primary: local
#   mirrors: [ amazon, google, microsoft ]
```


 

**3)	Setting up Active Storage inside models.**

Active storage comes with some powerful macros to connect file objects to models.  

The has_one _attached macro maps one loaded file to one instance of user, i.e. a user can only have one avatar

The has_many _attached macro maps many loaded file to one instance of user, i.e. a user can have multiple uploads. 
```
class User < ApplicationRecord
  has_one_attached :avatar
  has_many_attached :uploads  
end
```



**4)	Update  private params methods**

Notice when adding a has_many_attached  maping, like uploads, uploads should be placed as a key with an empty array so to allow multiple files in the array.
```
 private

    def user_params
        params.require(:user).permit(:email,:avatar, uploads: [])   
    end
```
   


**5)	Views upload file ** 
 
A little rails form helper magic to upload files. Note the “multiple: true”  helper which is needed for all has_many_attachment  relationships. 
```
 <%= f.file_field :uploads, multiple: true %>            
      <div class="actions">
         <%= f.submit %>     
    </div>
```
  



That’s pretty much it  for active storage. Now manipulating  the contents of the Blob files is whole another post for some other time. Happy coding. 
 



