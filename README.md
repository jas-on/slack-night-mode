# Slack Night Mode
Forked from https://github.com/laCour/slack-night-mode

## Set-up

Add this JS to the bottom of `/Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js`

```javascript
document.addEventListener('DOMContentLoaded', function() {
    $.ajax({
      url: 'https://cdn.rawgit.com/jas-on/slack-solarized-theme/27ff066d/solarized-dark.css',
      success: function(css) {
      $("<style></style>").appendTo('head').html(css);
      $(".client_channels_list_container").hide();
    }
  });
});
```

The `url` is a pointer to the raw CSS generated from the SCSS. Couldn't get local `file://` and `http://localhost` AJAX calls to work so I'm hosting the file in a CDN.

## Create your style

Modify `scss/helpers/_variables.scss` with your preferred colors.

## Building the CSS

In the main directory, `make` will build your style and pop it out in `css/raw/`.

