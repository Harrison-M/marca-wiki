**Notes on modal creation:**

Files for example:
* FileController
The modal actions are now called modal (i.e. newModalAction).  So, rename the action with the name modal to distinguish from the others.  
  
Add the modal to the route: @Route("/{courseid}/{resource}/{tag}/{type}/new_modal", name="file_new_modal")

Delete what we don't need in the modal (but - for example, in files we will need the returns because we need to know where to go when we're done).  

* in Marca/FileBundle/Resources/views/File/index.html.twig  
(Save-as the file that you're working on (i.e. new.html.twig) to new_modal.html.twig, but keep the new.html.twig b/c we'll still need it.  On the new_modal, we can delete the extend layout tag and the call on the javascript files.  See new_modal.html.twig in journal for example)


Add this div in the end to allow us to specify where we are and what we're working

```
{# Modal #}
<div id="file_modal" class="modal hide fade" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">     
</div>
```

 On line 85, you'll see how we have a class for the edit listing :

```
{% if file.isOwner(app.user.username) %}
<li><a class='edit_{{file.id}}' href="javascript:void(0);">Edit Listing</a></li>{% endif%}
```

In the jquery (line 13), you'll see the jquery click function:

```
$('.edit_{{file.id}}').click(function(){
  $('#file_modal').load('{{ course_path('file_edit_modal', { 'id': file.id, 'resource': app.request.get('resource'), 'tag': app.request.get('tag') }) }}');
  $('#file_modal').modal();
});
```

IN REVIEW
1. _**Change the naming convention in the action.**_
2. _**Create an id'd url instead of the url listing itself**_
3. _**Write the jquery to load that in the existing modal.  **_