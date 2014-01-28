# SLA Pressure Dashboard

TODO: description

## Hacking

You need the zendesk app tools -- `gem install zendesk_apps_tools`, and that's
about it.

To fiddle with changes without pushing them to the rest of the team, run:

    zat server

and add `?zat=true` right *before* the `#` in the URL in any zendesk page.
That'll force it to load your local copy, and all it takes to see changes is
a refresh.

NB: for **chrome users** you'll need to click the shield at the right of the
    address bar and allow insecure content for that session to see your local
    copy.


## Building

Zendesk insists on passing jslint as part of the packaging stage. If you want
to make sure your changes still validate before you package, run:

    echo 'http://basho.zendesk.com' | zat validate

If you just want to build a package, run

    echo 'http://basho.zendesk.com' | zat package

to produce a zipfile in tmp/ that you can upload to Zendesk. If you deploy
a new package to ZD, please bump the version and tag it, so we know what's
actually running and can roll back easily. Use semver, to the extent that
you can.

## Stuff that needs to be done:

 1. Anything in `todo.md`
 2. Anything marked with a todo in `app.js`
 3. Clean up the markup in the templates
 4. Move the SLA configuration bits to app settings instead of the top of app.js
 5. Clean up the CSS to match the cleaned-up markup from [3].
 6. Add a Makefile to manage all the project build bits, also add sass or less.
 7. Come up with a better way of managing multiple graphs and multiple views
    than the single `drawGraphics()` call used now.
