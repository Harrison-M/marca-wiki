### Forms
Use the FormBuilder to make changes to labels, add attr. etc.  
Use form_errors,form_row(per field), and form_rest in templates.

`
<form class="form" action="{{ path('tag_update', { 'id': tag.id }) }}" method="post" {{ form_enctype(edit_form) }}>
     {{ form_errors(edit_form) }}
            {{ form_row(edit_form.name) }}
            {{ form_row(edit_form.color) }}
            {{ form_row(edit_form.tagset) }} 
            {{ form_row(edit_form.icon) }}
    {{ form_rest(edit_form) }}
    <div class="submit">
        <button class="btn btn-primary" type="submit">Update</button>
    </div>
</form>
`