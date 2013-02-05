# Files Documentation

## Current structure

New links and new docs are created using the same controller with a parameter switch:  
* file_new_modal with type doc
* file_new_modal with type link

in the newModalAction in the FileController, there is a if based on type
a link is created with only a file entity, but it uses a different form type: LinkType

similarly, a doc is created with the form type DocType; in addition a doc entity is created

Uploads are created with the uploadAction in the FileController.  The action creates a file entity with the UploadType and uses the Vich Uploader Bundle (annotations in the File entity)

