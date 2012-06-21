Please follow these recommendations unless you have a good reason not to

## Forms
most form adjustments should be made in the FormBuilder in Form/xxxType.php
Form displays should be kept simple and will rely on Twitter Bootstrap for style.  Use form_errors, form_row (per field), and form_rest.
Ex.:

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