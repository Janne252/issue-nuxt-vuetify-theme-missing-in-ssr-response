# Steps to reproduce the issue

1. Install dependencies from `package.json`
1. Build the app by running `npm run build`
1. Start the app by running `npm run start`
1. Navigate to the app's URL in a browser (defaults to http://localhost:3000)
1. In browser dev tools, disable javascript
    - This is used to make sure we're seeing the raw SSR response
    - e.g. in Google Chrome press `Ctrl+Shift+P` to open the command widget and search for `javascript`, select "Disable JavaScript" and press enter
    ![](/images/disable-javascript-chrome.png)
1. Reload the application
1. The visible element on the page has its styles missing because the Vuetify component CSS and Vuetify theme were not included in the SSR response.
    ![](/images/theme-missing.png)
1. It should look like this (And does with JavaScript enabled, but causes a FOAC. The FOAC is not very visible in this case as the app loads rather quickly. With larger applications the FOAC is noticeable.)
    ![](/images/theme-applied.png)
