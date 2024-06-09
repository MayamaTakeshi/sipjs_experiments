# sipjs_experiments

At the moment we cannot use typescript:
```
takeshi@takeshi-desktop:sipjs_experiments$ npx tsc
npm info using npm@10.2.3
npm info using node@v21.2.0
node_modules/sip.js/lib/api/session-description-handler.d.ts:53:26 - error TS2304: Cannot find name 'RTCSessionDescriptionInit'.

53     (sessionDescription: RTCSessionDescriptionInit): Promise<RTCSessionDescriptionInit>;
                            ~~~~~~~~~~~~~~~~~~~~~~~~~

node_modules/sip.js/lib/api/session-description-handler.d.ts:53:62 - error TS2304: Cannot find name 'RTCSessionDescriptionInit'.

53     (sessionDescription: RTCSessionDescriptionInit): Promise<RTCSessionDescriptionInit>;
                                                                ~~~~~~~~~~~~~~~~~~~~~~~~~


Found 2 errors in the same file, starting at: node_modules/sip.js/lib/api/session-description-handler.d.ts:53

```

But we should be able to use sip.js with node:
```
takeshi@takeshi-desktop:sipjs_experiments$ node a.mjs 
[class Invitation extends Session]
```
