# Fix Hubspot custom action
In the rare case you use Hubspot and use it to send data to a custom url. You need this fix

The current implentation has changed to add an iframe to the build of the form. So you have to add $form.attr('target',''); to the onFormReady.
This changes the (now) default behaviour to post to an iFrame. Because X-Frame-Options will fire (which you must have enabled to be safer).

hbspt.forms.create({
  portalId: 'your portalId',
  formId: 'Your formId',
  target: '#yourtarget',
  onFormReady: function($form) {
    $form.attr('action', 'https://www.your-custom-url.com');
    $form.attr('target','');
  }
});
