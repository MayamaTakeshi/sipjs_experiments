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
takeshi@takeshi-desktop:sipjs_experiments$ node test.mjs 
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | Configuration:
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · allowLegacyNotifications: false
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · authorizationHa1: ""
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · authorizationPassword: NOT SHOWN
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · authorizationUsername: ""
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · delegate: {}
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · contactName: ""
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · contactParams: {"transport":"ws"}
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · displayName: ""
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · forceRport: false
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · gracefulShutdown: true
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · hackAllowUnregisteredOptionTags: false
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · hackIpInContact: false
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · hackViaTcp: false
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · instanceId: ""
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · instanceIdAlwaysAdded: false
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · logBuiltinEnabled: true
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · logConfiguration: true
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · logConnector: undefined
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · logLevel: "log"
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · noAnswerTimeout: 60
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · preloadedRouteSet: []
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · reconnectionAttempts: 0
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · reconnectionDelay: 4
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sendInitialProvisionalResponse: true
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sessionDescriptionHandlerFactory: (session, options) => {
        // provide a default media stream factory if need be
        if (mediaStreamFactory === undefined) {
            mediaStreamFactory = defaultMediaStreamFactory();
        }
        // make sure we allow `0` to be passed in so timeout can be disabled
        const iceGatheringTimeout = (options === null || options === void 0 ? void 0 : options.iceGatheringTimeout) !== undefined ? options === null || options === void 0 ? void 0 : options.iceGatheringTimeout : 5000;
        // merge passed factory options into default session description configuration
        const sessionDescriptionHandlerConfiguration = {
            iceGatheringTimeout,
            peerConnectionConfiguration: Object.assign(Object.assign({}, defaultPeerConnectionConfiguration()), options === null || options === void 0 ? void 0 : options.peerConnectionConfiguration)
        };
        const logger = session.userAgent.getLogger("sip.SessionDescriptionHandler");
        return new SessionDescriptionHandler(logger, mediaStreamFactory, sessionDescriptionHandlerConfiguration);
    }
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sessionDescriptionHandlerFactoryOptions: {}
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sipExtension100rel: "Unsupported"
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sipExtensionReplaces: "Unsupported"
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sipExtensionExtraSupported: []
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · sipjsId: "9u5g3"
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · transportConstructor: Transport
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · transportOptions: {"server":"wss://sip.example.com"}
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · uri: sip:alice@example.com
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · userAgentString: "SIP.js/0.21.1"
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | · viaHost: "uf7umeee230t.invalid"
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | Starting sip:alice@example.com
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.UserAgent | Transitioned from Stopped to Started
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.Transport | Connecting wss://sip.example.com
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.Transport | Transitioned from Disconnected to Connecting
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.Transport | WebSocket error occurred.
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.Transport | WebSocket closed unexpectedly
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.Transport | WebSocket closed wss://sip.example.com (code: 1006)
Sun Jun 09 2024 15:12:35 GMT+0900 (Japan Standard Time) | sip.Transport | Transitioned from Connecting to Disconnected
file:///home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/sip.js/lib/platform/web/transport/transport.js:337
        const error = !this.disconnectPromise ? new Error(message) : undefined;
                                                ^

Error: WebSocket closed wss://sip.example.com (code: 1006)
    at Transport.onWebSocketClose (file:///home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/sip.js/lib/platform/web/transport/transport.js:337:49)
    at WebSocket.<anonymous> (file:///home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/sip.js/lib/platform/web/transport/transport.js:199:55)
    at callListener (/home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/ws/lib/event-target.js:290:14)
    at WebSocket.onClose (/home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/ws/lib/event-target.js:220:9)
    at WebSocket.emit (node:events:519:28)
    at WebSocket.emitClose (/home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/ws/lib/websocket.js:255:12)
    at emitErrorAndClose (/home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/ws/lib/websocket.js:1034:13)
    at ClientRequest.<anonymous> (/home/takeshi/src/git/MayamaTakeshi/sipjs_experiments/node_modules/ws/lib/websocket.js:880:5)
    at ClientRequest.emit (node:events:519:28)
    at TLSSocket.socketErrorListener (node:_http_client:495:9)

Node.js v21.2.0

```
