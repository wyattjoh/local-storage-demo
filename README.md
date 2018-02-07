# local-storage-demo

This is a demo showing the issues with Firefox 58 with localStorage handling when dealing with iFrames.

## Setup

You can run this demo using python:

```bash
python -m SimpleHTTPServer
```

and navigating to http://localhost:8000/.

## Reproducing the issue

1. Ensure that [about:preferences#privacy](about:preferences#privacy) has "Firefox will **Use custom settings for history**" and under "Accept cookies from websites", you have "Keep until **they expire**" set.
2. Open a tab to view the contents of the edit box. Click the "Edit with Popup" button.
3. Enter text in the popup.
4. Click "Save to Local Storage"
5. Close the window.
6. Duplicate the window.
7. Notice that your edited content is shown in the new tab.
8. On [about:preferences#privacy](about:preferences#privacy), change "Keep until **they expire**" to "Keep until **I close Firefox**"
9. Repeat steps 2-6, but notice that the content did not change to the newly edited content that you changed when you repeated step 3, instead, it is the previous content that you saw at step 7, before you changed the Firefox preference.