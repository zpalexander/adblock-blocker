# AdBlock Blocker

This app is a simple proof of concept that shows how to detect whether a user is using an AdBlocking browser extension.

***Technical disclaimer:*** The code included in this project is only meant to be a proof of concept. Loading a script with a `<script>` tag is an expensive operation in terms of website performance. This method is not recommended for production web applications.

***Moral disclaimer:*** My building this proof of concept has no relation to my personal moral views towards ad blocking software. This is only a technical exercise. Plz no hate.

## Installation

The project depends on Node v6. You can [use NVM](https://github.com/creationix/nvm#installation) to get it if you don't have it installed already.

Build the project by running `npm install` in the project's root directory. To view the demo in action, visit `http://localhost:3000` in your browser.

If you're running an AdBlocker extension in your browser, you should see the message `'You ARE using an ad blocker'` on the page. If you're not running an AdBlocker or you have whitelisted your localhost domain, you should see the message `You ARE NOT using an ad blocker`.

## Explanation

This demo uses a very simple method to demonstrate how a website might detect whether a user is employing a browser ad blocking extension. The action is all in the `/public` directory. `server.js` is just a simple web server to serve the HTML file.

On line 6 of `index.js`, a flag named `usingAdblock` is initialized to true. A script named `adframe.js` is then requested on line 9. Although `adframe.js` does not contain any actual advertising content, it is named that way in order to trigger the blocking mechanism of most ad blocking extensions.

`adframe.js` simply sets the `usingAdblock` flag from on to off. Assuming the user is not using an ad blocker, the script will load with no problem and set the flag to off. If the user ***is*** using ad blocking software, however, the script will not load and the `usingAdblock` flag will remain on.

To demonstrate how the `usingAdblock` flag might be used by a website, the demo only conditionally renders content depending on how the flag has been set. In a content-sensitive environment, a website might refuse to load site content if the `usingAdblock` flag is set to true.
