# CBD
Cocos Creator Bundle Downloader (HMTL5!!11!!11 game archiver)

Automatically download assets from a **Cocos Creator** game, so you don't have to waste 1/2 of your life playing the entire game.

***I was going to make this tool gatekept for myself, since this is the first and probably last automatic HTML5 game archiver in the history of humanity, however my good soul decided to make this world a little fairer to you, so i decided to release it, the tool was originally made to help PvZ miniprograms archival easier to us scrappers.***

Please go to the "How to use?" section before using the tool, im horrible at explaining things so sorry if you can't understand nothing.

NOTE: This ONLY works in Cocos Creator games, i have not tested this in any other Cocos games... except Chinese miniprograms.

## How to use?

To use this tool, you need 2 things only: the main URL of the CC game (https://example.com/folder1/) and the Bundle configuration file.

To get a bundle config file is very simple, on the game URL, type `view-source:` *before* the HTTP indentier, this will open the page's source code.

Scroll down a little bit until you find somenthing like this:

`<script src="src/settings.RANDOMHASH.js" charset="utf-8"></script>`

If your browser is not dumbed down, you will see an hyperlink between the `src=` attribute, click it and it will open a json file like the one in the below image:

![image](https://github.com/user-attachments/assets/d99e719d-7120-459f-91fb-d37c35d230ef)

See the `bundleVars` key? well that's what we are searching for, copy the name of the bundle and the hash of the bundle you want to archive and put these in this link:

`{gamelinkhere}/assets/BUNDLENAMEHERE/config.BUNDLEHASHHERE.json`

Press enter and it will open another JSON file, this is exactly what we want, right click and click `Save as...` button and save it on the root of the tool directory.

Now you are ready to scrape those bundles! To initiate the tool, open a Terminal and type `node CBD.js`, the game's URL and the full name of the bundle config file, it will prob look like this:

`node CBD.js https://example.com/folder1/ config.e511f.json`

The tool will launch and will start scrapping the files, when it ends, you should see an little zip archive in the directory of the tool with the game assets!

## Requirements:

- node-fetch
- jszip

## How it works?

not bothered enough to explain it here sorry, have this instead:

`${serverName}/assets/${bundleData.name}/${base}/${firstTwoChars}/${decryptedUuid}.${hash}${ext}`

https://forum.cocos.org/t/uuid/96047

https://docs.cocos.com/creator/3.4/api/en/core/Function/decodeUuid

https://github.com/nmhung1210/cocos-creator/blob/1e1300bef05b8ab4a9e33944b7bcbe5e684d7eb6/engine/cocos2d/core/utils/decode-uuid.js#L4
