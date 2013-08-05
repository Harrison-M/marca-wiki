# Files Documentation


## Create
New links and new docs are created using the same controller with a parameter switch:  
* file_new_modal with type doc
* file_new_modal with type link

In the newModalAction in the FileController, there is an if statement based on the type parameter:
a link is created with only a file entity, but it uses the form type: LinkType.

A doc is created with the form type DocType; in addition a doc entity is created.

add note on createAction

Uploads are created with the uploadAction in the FileController.  The action creates a file entity with the UploadType and uses the Vich Uploader Bundle (annotations in the File entity)

***

## Edit

File listing editing and doc editing are separate.

* file_edit_modal
* doc_edit in the DocController

At this point, editing the file entity only distinguished between links and other files as the file entity and form type are the same for uploads and docs (both use the FileType (though we should refactor as DocType and Filetype are the same)).  Links again use the form type LinkType.

Doc editing works in a straight-forward way.


***

## Review

A Review duplicates the doc and creates a special file entity that is the child of the file that is being reviewed (a OneToMany self join in File).  The reviewAction is in the DocController (it may make more sense to move this action to the FileController as all other create functions are there.)  

Editing a review doc is no different than editing any other doc.  There is no editing of the Review File entity. 

DELETING a "parent" doc (one that has a review associated).  We think the best practice is to change the listing for the doc to "deleted" and keep the association.  

***

## To Be Done

* Add the functionality for deleting a parent doc as described above
* Good UI for files with related entities
* Cleanup controllers

Graded Doc
* Instructor Grade Doc with Graded label (and notifications)
* Lock editing of graded doc
* insert rubric (course based but easily changeable)
* feed essays next essay >

