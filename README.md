# -Track-Gravity-Forms-With-Google-Tag-Manager-and-GA4
 Track Gravity Forms With Google Tag Manager and GA4


#1.1. Gravity Forms Listener
Create a Custom HTML tag with the following code:

<script type="text/javascript">
  jQuery(document).ready(function() {
   jQuery(document).bind("gform_confirmation_loaded", function(event, formID) {
    window.dataLayer = window.dataLayer || [];
    window.dataLayer.push({
     'event': 'formSubmission',
     'formID': formID
    });
   });
  });
</script>

#1.1.1. What if my Gravity form refreshes the page or redirects a visitor to a ‘thank you’ page?
You’ve probably figured that the Gravity Form Listener given above does not work in these situations. Instead, you’ll need to log in to WordPress, find the form and add an additional code snippet so that the listener identifies a successful form submission.

In WordPress:

Go to Forms and open the one you wish to track.
Then go to Settings
Click Confirmations.
Usually, the Confirmation type is “Text” and what you’ll need to do is add a small JavaScript code there. It will create a Data Layer event, “formSubmission”, which we’ll use later as a trigger.

In this case, both forms should have different codes. The adjusted code of the first form could look like this:

<script>
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  'event': 'formSubmission',
  'formID': '1' // you can replace that 1 with anything you want. Just make sure it makes sense to you.
});
</script>
As for the 2nd form, its code should contain ‘formID’: ‘2’.

<script>
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
  'event': 'formSubmission',
  'formID': '2' // you can replace that 2 with anything you want. Just make sure it makes sense to you.
});
</script>

Details in Source: https://www.analyticsmania.com/post/track-gravity-forms-with-google-tag-manager/

