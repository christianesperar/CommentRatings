CommentRatings
==============

Adds rating selection for ProcessWire comments field


Installation
============

Install the module and after that you should see new options on your field settings (details-tab) for each comments field.


Usage on templates
==================

```php
// Get average of all comments:
echo "Average rating: " . $page->comments->averageRating;

// Loop comments and display all the fields (includes the rating!):
foreach($page->comments as $comment) {
    if($comment->status < 1) continue; // skip unapproved or spam comments
    $cite = htmlentities($comment->cite);
    $text = htmlentities($comment->text);
    $rating = htmlentities($comment->rating);
    $date = date('m/d/y g:ia', $comment->created); // format the date
    echo "<p><strong>Posted by $cite on $date with rating $rating</strong><br />$text</p>";
}

// Render the form with rating dropdown (here you can use some js widget to make them stars):
echo $page->comments->renderFormWithRatings();
```

TODO
====

Since this (https://github.com/ryancramerdesign/ProcessWire/blob/master/wire/modules/Fieldtype/FieldtypeComments/InputfieldCommentsAdmin.module#L29) method is protected and not hookable (yet), it wasn't the cleanest solution to get rating visible to the admin view.


Credits
=======

Module development sponsored by: Ovi Savescu @ DVS Consulting Group
Thanks Ovi!
