```bash
296|backoffice  |   stack: [
296|backoffice  |     {
296|backoffice  |       message: 'Request failed with status code 404',
296|backoffice  |       name: 'AxiosError',
296|backoffice  |       stack: 'AxiosError: Request failed with status code 404\n' +
296|backoffice  |         '    at settle (/app/smile/backend/node_modules/axios/dist/node/axios.cjs:1909:12)\n' +
296|backoffice  |         '    at IncomingMessage.handleStreamEnd (/app/smile/backend/node_modules/axios/dist/node/axios.cjs:2989:11)\n' +
296|backoffice  |         '    at /app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AbstractAsyncHooksContextManager.js:50:55\n' +
296|backoffice  |         '    at AsyncLocalStorage.run (node:async_hooks:335:14)\n' +
296|backoffice  |         '    at AsyncLocalStorageContextManager.with (/app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AsyncLocalStorageContextManager.js:33:40)\n' +
296|backoffice  |         '    at IncomingMessage.contextWrapper (/app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AbstractAsyncHooksContextManager.js:50:32)\n' +
296|backoffice  |         '    at IncomingMessage.emit (node:events:536:35)\n' +
296|backoffice  |         '    at endReadableNT (node:internal/streams/readable:1698:12)\n' +
296|backoffice  |         '    at process.processTicksAndRejections (node:internal/process/task_queues:82:21)',
296|backoffice  |       config: {
296|backoffice  |         transitional: {
296|backoffice  |           silentJSONParsing: true,
296|backoffice  |           forcedJSONParsing: true,
296|backoffice  |           clarifyTimeoutError: false
296|backoffice  |         },
296|backoffice  |         adapter: [ 'xhr', 'http' ],
296|backoffice  |         transformRequest: [ null ],
296|backoffice  |         transformResponse: [ null ],
296|backoffice  |         timeout: 30000,
296|backoffice  |         xsrfCookieName: 'XSRF-TOKEN',
296|backoffice  |         xsrfHeaderName: 'X-XSRF-TOKEN',
296|backoffice  |         maxContentLength: -1,
296|backoffice  |         maxBodyLength: -1,
296|backoffice  |         env: {},
296|backoffice  |         headers: {
296|backoffice  |           Accept: 'application/json, text/plain, */*',
296|backoffice  |           'Content-Type': 'application/json',
296|backoffice  |           'x-app-id': 'ETIQAPLUS',
296|backoffice  |           'x-country-code': 'MYS',
296|backoffice  |           'x-api-version': '1',
296|backoffice  |           'Accept-Language': 'en',
296|backoffice  |           'User-Agent': 'axios/1.4.0',
296|backoffice  |           'Content-Length': '81',
296|backoffice  |           'Accept-Encoding': 'gzip, compress, deflate, br'
296|backoffice  |         },
296|backoffice  |         httpsAgent: {
296|backoffice  |           _events: {},
296|backoffice  |           _eventsCount: 2,
296|backoffice  |           defaultPort: 443,
296|backoffice  |           protocol: 'https:',
296|backoffice  |           options: { rejectUnauthorized: false, noDelay: true, path: null },
296|backoffice  |           requests: {},
296|backoffice  |           sockets: {},
296|backoffice  |           freeSockets: {},
296|backoffice  |           keepAliveMsecs: 1000,
296|backoffice  |           keepAlive: false,
296|backoffice  |           maxSockets: null,
296|backoffice  |           maxFreeSockets: 256,
296|backoffice  |           scheduling: 'lifo',
296|backoffice  |           maxTotalSockets: null,
296|backoffice  |           totalSocketCount: 0,
296|backoffice  |           maxCachedSessions: 100,
296|backoffice  |           _sessionCache: { map: {}, list: [] }
296|backoffice  |         },
296|backoffice  |         method: 'post',
296|backoffice  |         url: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
296|backoffice  |         data: '{"client":{"idType":"001","idValue":"000522055323","ecif":"PIMYS2507WRA9DE92FE"}}'
296|backoffice  |       },
296|backoffice  |       code: 'ERR_BAD_REQUEST',
296|backoffice  |       status: 404
296|backoffice  |     }

```


cert:

```bash
P@ssw0rd


openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -nocerts -out private.key

openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -clcerts -nokeys -out 250804-appetqplus-gold.etiqa.com.my.cer

openssl rsa -in private.key -out 250804-appetqplus-gold.etiqa.com.my.key
```


after deployed:

in backoffice:
https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search

actual:
https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search


```Bash
 } +31ms
342|backoffice  | [backend] error       2025-08-04 17:48:47.925 retrieveCdhDataByDetails error - {
342|backoffice  |   stack: [
342|backoffice  |     {
342|backoffice  |       message: 'Request failed with status code 404',
342|backoffice  |       name: 'AxiosError',
342|backoffice  |       stack: 'AxiosError: Request failed with status code 404\n' +
342|backoffice  |         '    at settle (/app/smile/backend/node_modules/axios/dist/node/axios.cjs:1909:12)\n' +
342|backoffice  |         '    at IncomingMessage.handleStreamEnd (/app/smile/backend/node_modules/axios/dist/node/axios.cjs:2989:11)\n' +
342|backoffice  |         '    at /app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AbstractAsyncHooksContextManager.js:50:55\n' +
342|backoffice  |         '    at AsyncLocalStorage.run (node:async_hooks:335:14)\n' +
342|backoffice  |         '    at AsyncLocalStorageContextManager.with (/app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AsyncLocalStorageContextManager.js:33:40)\n' +
342|backoffice  |         '    at IncomingMessage.contextWrapper (/app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AbstractAsyncHooksContextManager.js:50:32)\n' +
342|backoffice  |         '    at IncomingMessage.emit (node:events:536:35)\n' +
342|backoffice  |         '    at endReadableNT (node:internal/streams/readable:1698:12)\n' +
342|backoffice  |         '    at process.processTicksAndRejections (node:internal/process/task_queues:82:21)',
342|backoffice  |       config: {
342|backoffice  |         transitional: {
342|backoffice  |           silentJSONParsing: true,
342|backoffice  |           forcedJSONParsing: true,
342|backoffice  |           clarifyTimeoutError: false
342|backoffice  |         },
342|backoffice  |         adapter: [ 'xhr', 'http' ],
342|backoffice  |         transformRequest: [ null ],
342|backoffice  |         transformResponse: [ null ],
342|backoffice  |         timeout: 30000,
342|backoffice  |         xsrfCookieName: 'XSRF-TOKEN',
342|backoffice  |         xsrfHeaderName: 'X-XSRF-TOKEN',
342|backoffice  |         maxContentLength: -1,
342|backoffice  |         maxBodyLength: -1,
342|backoffice  |         env: {},
342|backoffice  |         headers: {
342|backoffice  |           Accept: 'application/json, text/plain, */*',
342|backoffice  |           'Content-Type': 'application/json',
342|backoffice  |           'x-app-id': 'ETIQAPLUS',
342|backoffice  |           'x-country-code': 'MYS',
342|backoffice  |           'x-api-version': '1',
342|backoffice  |           'Accept-Language': 'en',
342|backoffice  |           'User-Agent': 'axios/1.4.0',
342|backoffice  |           'Content-Length': '81',
342|backoffice  |           'Accept-Encoding': 'gzip, compress, deflate, br'
342|backoffice  |         },
342|backoffice  |         httpsAgent: {
342|backoffice  |           _events: {},
342|backoffice  |           _eventsCount: 2,
342|backoffice  |           defaultPort: 443,
342|backoffice  |           protocol: 'https:',
342|backoffice  |           options: {
342|backoffice  |             pfx: {
342|backoffice  |               type: 'Buffer',
342|backoffice  |               data: [
342|backoffice  |                  48, 130,  19,  39,   2,   1,   3,  48, 130,  18, 224,   6,
342|backoffice  |                   9,  42, 134,  72, 134, 247,  13,   1,   7,   1, 160, 130,
342|backoffice  |                  18, 209,   4, 130,  18, 205,  48, 130,  18, 201,  48, 130,
342|backoffice  |                   5, 149,   6,   9,  42, 134,  72, 134, 247,  13,   1,   7,
342|backoffice  |                   1, 160, 130,   5, 134,   4, 130,   5, 130,  48, 130,   5,
342|backoffice  |                 126,  48, 130,   5, 122,   6,  11,  42, 134,  72, 134, 247,
342|backoffice  |                  13,   1,  12,  10,   1,   2, 160, 130,   4, 251,  48, 130,
342|backoffice  |                   4, 247,  48,  41,   6,  10,  42, 134,  72, 134, 247,  13,
342|backoffice  |                   1,  12,   1,   3,
342|backoffice  |                 ... 4807 more items
342|backoffice  |               ]
342|backoffice  |             },
342|backoffice  |             passphrase: 'P@ssw0rd',
342|backoffice  |             rejectUnauthorized: true,
342|backoffice  |             noDelay: true,
342|backoffice  |             path: null
342|backoffice  |           },
342|backoffice  |           requests: {},
342|backoffice  |           sockets: {},
342|backoffice  |           freeSockets: {},
342|backoffice  |           keepAliveMsecs: 1000,
342|backoffice  |           keepAlive: false,
342|backoffice  |           maxSockets: null,
342|backoffice  |           maxFreeSockets: 256,
342|backoffice  |           scheduling: 'lifo',
342|backoffice  |           maxTotalSockets: null,
342|backoffice  |           totalSocketCount: 0,
342|backoffice  |           maxCachedSessions: 100,
342|backoffice  |           _sessionCache: { map: {}, list: [] }
342|backoffice  |         },
342|backoffice  |         method: 'post',
342|backoffice  |         url: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
342|backoffice  |         data: '{"client":{"idType":"001","idValue":"950422050021","ecif":"PIMYS2507Q9JX596F2B"}}'
342|backoffice  |       },
342|backoffice  |       code: 'ERR_BAD_REQUEST',
342|backoffice  |       status: 404
342|backoffice  |     }
342|backoffice  |   ],
342|backoffice  |   trace_id: '52482ad1491d7888f93e03c48764706e',
342|backoffice  |   span_id: '4f0effc92a78d783',
342|backoffice  |   trace_flags: '01'
342|backoffice  | } +4ms

```

Now getting unsupported PCKS12 file
```bash
keytool -importkeystore -srckeystore 250804-appetqplus-gold.etiqa.com.my.p12 -srcstoretype PKCS12 -srcstorepass P@ssw0rd -destkeystore server-truststore.p12 -deststoretype PKCS12 -deststorepass P@ssw0rd -alias 250804-appetqplus-gold.etiqa.com.my
```


with new implementation:
```bash
stack: [
395|backoffice  |     {
395|backoffice  |       message: '4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42\n',
395|backoffice  |       name: 'Error',
395|backoffice  |       stack: 'Error: 4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42\n' +
395|backoffice  |         '\n' +
395|backoffice  |         '    at AxiosError.from (/app/smile/backend/node_modules/axios/dist/node/axios.cjs:836:14)\n' +
395|backoffice  |         '    at RedirectableRequest.handleRequestError (/app/smile/backend/node_modules/axios/dist/node/axios.cjs:3010:25)\n' +
395|backoffice  |         '    at RedirectableRequest.emit (node:events:536:35)\n' +
395|backoffice  |         '    at eventHandlers.<computed> (/app/smile/backend/node_modules/follow-redirects/index.js:49:24)\n' +
395|backoffice  |         '    at /app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AbstractAsyncHooksContextManager.js:50:55\n' +
395|backoffice  |         '    at AsyncLocalStorage.run (node:async_hooks:346:14)\n' +
395|backoffice  |         '    at AsyncLocalStorageContextManager.with (/app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AsyncLocalStorageContextManager.js:33:40)\n' +
395|backoffice  |         '    at ClientRequest.contextWrapper (/app/smile/backend/node_modules/@opentelemetry/context-async-hooks/build/src/AbstractAsyncHooksContextManager.js:50:32)\n' +
395|backoffice  |         '    at ClientRequest.emit (node:events:524:28)\n' +
395|backoffice  |         '    at emitErrorEvent (node:_http_client:101:11)\n' +
395|backoffice  |         '    at TLSSocket.socketErrorListener (node:_http_client:504:5)\n' +
395|backoffice  |         '    at TLSSocket.emit (node:events:524:28)\n' +
395|backoffice  |         '    at TLSSocket._emitTLSError (node:_tls_wrap:1032:10)\n' +
395|backoffice  |         '    at TLSWrap.onerror (node:_tls_wrap:473:11)\n' +
395|backoffice  |         '    at TLSWrap.callbackTrampoline (node:internal/async_hooks:130:17)',
395|backoffice  |       config: {
395|backoffice  |         transitional: {
395|backoffice  |           silentJSONParsing: true,
395|backoffice  |           forcedJSONParsing: true,
395|backoffice  |           clarifyTimeoutError: false
395|backoffice  |         },
395|backoffice  |         adapter: [ 'xhr', 'http' ],
395|backoffice  |         transformRequest: [ null ],
395|backoffice  |         transformResponse: [ null ],
395|backoffice  |         timeout: 30000,
395|backoffice  |         xsrfCookieName: 'XSRF-TOKEN',
395|backoffice  |         xsrfHeaderName: 'X-XSRF-TOKEN',
395|backoffice  |         maxContentLength: -1,
395|backoffice  |         maxBodyLength: -1,
395|backoffice  |         env: {},
395|backoffice  |         headers: {
395|backoffice  |           Accept: 'application/json, text/plain, */*',
395|backoffice  |           'Content-Type': 'application/json',
395|backoffice  |           'x-app-id': 'ETIQAPLUS',
395|backoffice  |           'x-country-code': 'MYS',
395|backoffice  |           'x-api-version': '1',
395|backoffice  |           'Accept-Language': 'en',
395|backoffice  |           'User-Agent': 'axios/1.4.0',
395|backoffice  |           'Content-Length': '62',
395|backoffice  |           'Accept-Encoding': 'gzip, compress, deflate, br'
395|backoffice  |         },
395|backoffice  |         httpsAgent: {
395|backoffice  |           _events: {},
395|backoffice  |           _eventsCount: 2,
395|backoffice  |           defaultPort: 443,
395|backoffice  |           protocol: 'https:',
395|backoffice  |           options: { rejectUnauthorized: false, noDelay: true, path: null },
395|backoffice  |           requests: {},
395|backoffice  |           sockets: {
395|backoffice  |             'apponboarding-gold.etiqa.com.my:11000::::::::false:::::::::::::': [
395|backoffice  |               {
395|backoffice  |                 _tlsOptions: {
395|backoffice  |                   pipe: false,
395|backoffice  |                   secureContext: { context: {} },
395|backoffice  |                   isServer: false,
395|backoffice  |                   requestCert: true,
395|backoffice  |                   rejectUnauthorized: false
395|backoffice  |                 },
395|backoffice  |                 _secureEstablished: true,
395|backoffice  |                 _securePending: false,
395|backoffice  |                 _newSessionPending: false,
395|backoffice  |                 _controlReleased: true,
395|backoffice  |                 secureConnecting: false,
395|backoffice  |                 _SNICallback: null,
395|backoffice  |                 servername: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                 alpnProtocol: false,
395|backoffice  |                 authorized: false,
395|backoffice  |                 authorizationError: 'SELF_SIGNED_CERT_IN_CHAIN',
395|backoffice  |                 encrypted: true,
395|backoffice  |                 _events: {
395|backoffice  |                   close: [ null, null, null, null ],
395|backoffice  |                   timeout: [ null, null ]
395|backoffice  |                 },
395|backoffice  |                 _eventsCount: 10,
395|backoffice  |                 connecting: false,
395|backoffice  |                 _hadError: true,
395|backoffice  |                 _parent: null,
395|backoffice  |                 _host: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                 _closeAfterHandlingError: false,
395|backoffice  |                 _readableState: {
395|backoffice  |                   highWaterMark: 16384,
395|backoffice  |                   buffer: [],
395|backoffice  |                   bufferIndex: 0,
395|backoffice  |                   length: 0,
395|backoffice  |                   pipes: [],
395|backoffice  |                   awaitDrainWriters: null
395|backoffice  |                 },
395|backoffice  |                 _writableState: {
395|backoffice  |                   highWaterMark: 16384,
395|backoffice  |                   length: 0,
395|backoffice  |                   corked: 0,
395|backoffice  |                   writelen: 0,
395|backoffice  |                   bufferedIndex: 0,
395|backoffice  |                   pendingcb: 0
395|backoffice  |                 },
395|backoffice  |                 allowHalfOpen: false,
395|backoffice  |                 _sockname: null,
395|backoffice  |                 _pendingData: null,
395|backoffice  |                 _pendingEncoding: '',
395|backoffice  |                 _server: null,
395|backoffice  |                 ssl: null,
395|backoffice  |                 _requestCert: true,
395|backoffice  |                 _rejectUnauthorized: false,
395|backoffice  |                 parser: null,
395|backoffice  |                 _httpMessage: {
395|backoffice  |                   _events: { response: [ null, null ] },
395|backoffice  |                   _eventsCount: 9,
395|backoffice  |                   outputData: [],
395|backoffice  |                   outputSize: 0,
395|backoffice  |                   writable: true,
395|backoffice  |                   destroyed: false,
395|backoffice  |                   _last: true,
395|backoffice  |                   chunkedEncoding: false,
395|backoffice  |                   shouldKeepAlive: false,
395|backoffice  |                   maxRequestsOnConnectionReached: false,
395|backoffice  |                   _defaultKeepAlive: true,
395|backoffice  |                   useChunkedEncodingByDefault: true,
395|backoffice  |                   sendDate: false,
395|backoffice  |                   _removedConnection: false,
395|backoffice  |                   _removedContLen: false,
395|backoffice  |                   _removedTE: false,
395|backoffice  |                   strictContentLength: false,
395|backoffice  |                   _contentLength: '62',
395|backoffice  |                   _hasBody: true,
395|backoffice  |                   _trailer: '',
395|backoffice  |                   finished: true,
395|backoffice  |                   _headerSent: true,
395|backoffice  |                   _closed: false,
395|backoffice  |                   socket: '[Circular]',
395|backoffice  |                   _header: 'POST /unity-onboarding-svc/api/parties/search HTTP/1.1\r\n' +
395|backoffice  |                     'Accept: application/json, text/plain, */*\r\n' +
395|backoffice  |                     'Content-Type: application/json\r\n' +
395|backoffice  |                     'x-app-id: ETIQAPLUS\r\n' +
395|backoffice  |                     'x-country-code: MYS\r\n' +
395|backoffice  |                     'x-api-version: 1\r\n' +
395|backoffice  |                     'Accept-Language: en\r\n' +
395|backoffice  |                     'User-Agent: axios/1.4.0\r\n' +
395|backoffice  |                     'Content-Length: 62\r\n' +
395|backoffice  |                     'Accept-Encoding: gzip, compress, deflate, br\r\n' +
395|backoffice  |                     'traceparent: 00-9e357bf806074249be90dc4dfbd7da86-faf76b959228c7ae-01\r\n' +
395|backoffice  |                     'Host: apponboarding-gold.etiqa.com.my:11000\r\n' +
395|backoffice  |                     'Connection: close\r\n' +
395|backoffice  |                     '\r\n',
395|backoffice  |                   _keepAliveTimeout: 0,
395|backoffice  |                   agent: '[Circular]',
395|backoffice  |                   method: 'POST',
395|backoffice  |                   path: '/unity-onboarding-svc/api/parties/search',
395|backoffice  |                   _ended: false,
395|backoffice  |                   res: null,
395|backoffice  |                   aborted: false,
395|backoffice  |                   timeoutCb: null,
395|backoffice  |                   upgradeOrConnect: false,
395|backoffice  |                   parser: null,
395|backoffice  |                   maxHeadersCount: null,
395|backoffice  |                   reusedSocket: false,
395|backoffice  |                   host: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                   protocol: 'https:',
395|backoffice  |                   _redirectable: {
395|backoffice  |                     _events: { socket: [ null, null ] },
395|backoffice  |                     _writableState: {
395|backoffice  |                       highWaterMark: 16384,
395|backoffice  |                       length: 0,
395|backoffice  |                       corked: 0,
395|backoffice  |                       writelen: 0,
395|backoffice  |                       bufferedIndex: 0,
395|backoffice  |                       pendingcb: 0
395|backoffice  |                     },
395|backoffice  |                     _options: {
395|backoffice  |                       maxRedirects: 21,
395|backoffice  |                       maxBodyLength: null,
395|backoffice  |                       protocol: 'https:',
395|backoffice  |                       path: '/unity-onboarding-svc/api/parties/search',
395|backoffice  |                       method: 'POST',
395|backoffice  |                       headers: {
395|backoffice  |                         Accept: 'application/json, text/plain, */*',
395|backoffice  |                         'Content-Type': 'application/json',
395|backoffice  |                         'x-app-id': 'ETIQAPLUS',
395|backoffice  |                         'x-country-code': 'MYS',
395|backoffice  |                         'x-api-version': '1',
395|backoffice  |                         'Accept-Language': 'en',
395|backoffice  |                         'User-Agent': 'axios/1.4.0',
395|backoffice  |                         'Content-Length': '62',
395|backoffice  |                         'Accept-Encoding': 'gzip, compress, deflate, br'
395|backoffice  |                       },
395|backoffice  |                       agents: { https: '[Circular]' },
395|backoffice  |                       beforeRedirects: {},
395|backoffice  |                       hostname: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                       port: '11000',
395|backoffice  |                       agent: '[Circular]',
395|backoffice  |                       nativeProtocols: {
395|backoffice  |                         'http:': {
395|backoffice  |                           METHODS: [
395|backoffice  |                             'ACL',         'BIND',       'CHECKOUT',
395|backoffice  |                             'CONNECT',     'COPY',       'DELETE',
395|backoffice  |                             'GET',         'HEAD',       'LINK',
395|backoffice  |                             'LOCK',        'M-SEARCH',   'MERGE',
395|backoffice  |                             'MKACTIVITY',  'MKCALENDAR', 'MKCOL',
395|backoffice  |                             'MOVE',        'NOTIFY',     'OPTIONS',
395|backoffice  |                             'PATCH',       'POST',       'PROPFIND',
395|backoffice  |                             'PROPPATCH',   'PURGE',      'PUT',
395|backoffice  |                             'REBIND',      'REPORT',     'SEARCH',
395|backoffice  |                             'SOURCE',      'SUBSCRIBE',  'TRACE',
395|backoffice  |                             'UNBIND',      'UNLINK',     'UNLOCK',
395|backoffice  |                             'UNSUBSCRIBE'
395|backoffice  |                           ],
395|backoffice  |                           STATUS_CODES: {
395|backoffice  |                             '100': 'Continue',
395|backoffice  |                             '101': 'Switching Protocols',
395|backoffice  |                             '102': 'Processing',
395|backoffice  |                             '103': 'Early Hints',
395|backoffice  |                             '200': 'OK',
395|backoffice  |                             '201': 'Created',
395|backoffice  |                             '202': 'Accepted',
395|backoffice  |                             '203': 'Non-Authoritative Information',
395|backoffice  |                             '204': 'No Content',
395|backoffice  |                             '205': 'Reset Content',
395|backoffice  |                             '206': 'Partial Content',
395|backoffice  |                             '207': 'Multi-Status',
395|backoffice  |                             '208': 'Already Reported',
395|backoffice  |                             '226': 'IM Used',
395|backoffice  |                             '300': 'Multiple Choices',
395|backoffice  |                             '301': 'Moved Permanently',
395|backoffice  |                             '302': 'Found',
395|backoffice  |                             '303': 'See Other',
395|backoffice  |                             '304': 'Not Modified',
395|backoffice  |                             '305': 'Use Proxy',
395|backoffice  |                             '307': 'Temporary Redirect',
395|backoffice  |                             '308': 'Permanent Redirect',
395|backoffice  |                             '400': 'Bad Request',
395|backoffice  |                             '401': 'Unauthorized',
395|backoffice  |                             '402': 'Payment Required',
395|backoffice  |                             '403': 'Forbidden',
395|backoffice  |                             '404': 'Not Found',
395|backoffice  |                             '405': 'Method Not Allowed',
395|backoffice  |                             '406': 'Not Acceptable',
395|backoffice  |                             '407': 'Proxy Authentication Required',
395|backoffice  |                             '408': 'Request Timeout',
395|backoffice  |                             '409': 'Conflict',
395|backoffice  |                             '410': 'Gone',
395|backoffice  |                             '411': 'Length Required',
395|backoffice  |                             '412': 'Precondition Failed',
395|backoffice  |                             '413': 'Payload Too Large',
395|backoffice  |                             '414': 'URI Too Long',
395|backoffice  |                             '415': 'Unsupported Media Type',
395|backoffice  |                             '416': 'Range Not Satisfiable',
395|backoffice  |                             '417': 'Expectation Failed',
395|backoffice  |                             '418': "I'm a Teapot",
395|backoffice  |                             '421': 'Misdirected Request',
395|backoffice  |                             '422': 'Unprocessable Entity',
395|backoffice  |                             '423': 'Locked',
395|backoffice  |                             '424': 'Failed Dependency',
395|backoffice  |                             '425': 'Too Early',
395|backoffice  |                             '426': 'Upgrade Required',
395|backoffice  |                             '428': 'Precondition Required',
395|backoffice  |                             '429': 'Too Many Requests',
395|backoffice  |                             '431': 'Request Header Fields Too Large',
395|backoffice  |                             '451': 'Unavailable For Legal Reasons',
395|backoffice  |                             '500': 'Internal Server Error',
395|backoffice  |                             '501': 'Not Implemented',
395|backoffice  |                             '502': 'Bad Gateway',
395|backoffice  |                             '503': 'Service Unavailable',
395|backoffice  |                             '504': 'Gateway Timeout',
395|backoffice  |                             '505': 'HTTP Version Not Supported',
395|backoffice  |                             '506': 'Variant Also Negotiates',
395|backoffice  |                             '507': 'Insufficient Storage',
395|backoffice  |                             '508': 'Loop Detected',
395|backoffice  |                             '509': 'Bandwidth Limit Exceeded',
395|backoffice  |                             '510': 'Not Extended',
395|backoffice  |                             '511': 'Network Authentication Required'
395|backoffice  |                           },
395|backoffice  |                           maxHeaderSize: 16384,
395|backoffice  |                           globalAgent: {
395|backoffice  |                             _events: {},
395|backoffice  |                             _eventsCount: 2,
395|backoffice  |                             defaultPort: 80,
395|backoffice  |                             protocol: 'http:',
395|backoffice  |                             options: {
395|backoffice  |                               keepAlive: true,
395|backoffice  |                               scheduling: 'lifo',
395|backoffice  |                               timeout: 5000,
395|backoffice  |                               noDelay: true,
395|backoffice  |                               path: null
395|backoffice  |                             },
395|backoffice  |                             requests: {},
395|backoffice  |                             sockets: {},
395|backoffice  |                             freeSockets: {},
395|backoffice  |                             keepAliveMsecs: 1000,
395|backoffice  |                             keepAlive: true,
395|backoffice  |                             maxSockets: null,
395|backoffice  |                             maxFreeSockets: 256,
395|backoffice  |                             scheduling: 'lifo',
395|backoffice  |                             maxTotalSockets: null,
395|backoffice  |                             totalSocketCount: 0
395|backoffice  |                           }
395|backoffice  |                         },
395|backoffice  |                         'https:': {
395|backoffice  |                           globalAgent: {
395|backoffice  |                             _events: {},
395|backoffice  |                             _eventsCount: 2,
395|backoffice  |                             defaultPort: 443,
395|backoffice  |                             protocol: 'https:',
395|backoffice  |                             options: {
395|backoffice  |                               keepAlive: true,
395|backoffice  |                               scheduling: 'lifo',
395|backoffice  |                               timeout: 5000,
395|backoffice  |                               noDelay: true,
395|backoffice  |                               path: null
395|backoffice  |                             },
395|backoffice  |                             requests: {},
395|backoffice  |                             sockets: {},
395|backoffice  |                             freeSockets: {},
395|backoffice  |                             keepAliveMsecs: 1000,
395|backoffice  |                             keepAlive: true,
395|backoffice  |                             maxSockets: null,
395|backoffice  |                             maxFreeSockets: 256,
395|backoffice  |                             scheduling: 'lifo',
395|backoffice  |                             maxTotalSockets: null,
395|backoffice  |                             totalSocketCount: 0,
395|backoffice  |                             maxCachedSessions: 100,
395|backoffice  |                             _sessionCache: {
395|backoffice  |                               map: {
395|backoffice  |                                 '10.230.21.116:8443:::::::::::::::::::::': {
395|backoffice  |                                   type: 'Buffer',
395|backoffice  |                                   data: [
395|backoffice  |                                      48, 130,   3, 217,   2,   1,   1,   2,   2,
395|backoffice  |                                       3,   4,   4,   2,  19,   2,   4,  32, 203,
395|backoffice  |                                     121,  28,  51, 206,  43, 173, 119, 179, 169,
395|backoffice  |                                      20, 123, 154,  10, 210,   5, 236, 106,   0,
395|backoffice  |                                     135,  98,  48, 165, 226,  18, 173,  78, 183,
395|backoffice  |                                     133,  29,   5,  94,   4,  48,  94,  28,  75,
395|backoffice  |                                     200,  23, 216, 139, 123, 213, 205,  63,  81,
395|backoffice  |                                     106, 210, 148, 101, 235, 214, 192, 226, 189,
395|backoffice  |                                     226,  45, 203, 238, 176,  27, 164, 173, 106,
395|backoffice  |                                      68, 226, 253, 165,  27, 243, 125, 180,  18,
395|backoffice  |                                     204, 120,  62,  43,  31, 128,  63, 110,  76,
395|backoffice  |                                     161,
395|backoffice  |                                     ... 889 more items
395|backoffice  |                                   ]
395|backoffice  |                                 },
395|backoffice  |                                 'appedp-gold.etiqa.com.my:4443:::::::::::::::::::::': {
395|backoffice  |                                   type: 'Buffer',
395|backoffice  |                                   data: [
395|backoffice  |                                      48, 130,   5, 173,   2,   1,   1,   2,   2,
395|backoffice  |                                       3,   4,   4,   2,  19,   2,   4,  32,  17,
395|backoffice  |                                     159,  34, 151, 181, 103, 102,  46, 172,  49,
395|backoffice  |                                     126, 203,  39,  59, 175, 235, 228,  70, 176,
395|backoffice  |                                     255, 101, 146, 113, 186, 189, 173, 222, 193,
395|backoffice  |                                       3,  11,  69, 107,   4,  48, 239, 106,  88,
395|backoffice  |                                     230,  28, 250, 126,  43, 192, 238,   1,  68,
395|backoffice  |                                       2,  63, 147, 234, 185, 151, 139,  29, 156,
395|backoffice  |                                       8,  64, 109,  45, 242,  73, 194,  39, 190,
395|backoffice  |                                     116, 134, 106,  26, 197, 154,   5, 127, 198,
395|backoffice  |                                     197,  21,  70, 204, 171,  88, 102,  38, 108,
395|backoffice  |                                     161,
395|backoffice  |                                     ... 1357 more items
395|backoffice  |                                   ]
395|backoffice  |                                 },
395|backoffice  |                                 'appmdm-gold.etiqa.com.my:5000:::::::::::::::::::::': {
395|backoffice  |                                   type: 'Buffer',
395|backoffice  |                                   data: [
395|backoffice  |                                      48, 130,  14, 109,   2,   1,   1,   2,   2,
395|backoffice  |                                       3,   4,   4,   2,  19,   1,   4,  32, 211,
395|backoffice  |                                      65, 123, 189, 201,  78,  70, 214,  26, 173,
395|backoffice  |                                     227,  76, 185,  93, 199,  17,  40, 109, 110,
395|backoffice  |                                     107,  92, 170, 228,  13,  97, 229,  25, 154,
395|backoffice  |                                     158,  40,  28, 138,   4,  32,  28, 228, 228,
395|backoffice  |                                     233,  87, 128, 170, 203,  44,  91,  74, 245,
395|backoffice  |                                     220,  31,  88, 242,  56,  80, 194, 210, 191,
395|backoffice  |                                     228,  76, 237,  48, 190, 175,  44, 114,  21,
395|backoffice  |                                     217, 196, 161,   6,   2,   4, 104, 145, 113,
395|backoffice  |                                     200, 162,   4,   2,   2,  28,  32, 163, 130,
395|backoffice  |                                       4,
395|backoffice  |                                     ... 3597 more items
395|backoffice  |                                   ]
395|backoffice  |                                 }
395|backoffice  |                               },
395|backoffice  |                               list: [
395|backoffice  |                                 '10.230.21.116:8443:::::::::::::::::::::',
395|backoffice  |                                 'appedp-gold.etiqa.com.my:4443:::::::::::::::::::::',
395|backoffice  |                                 'appmdm-gold.etiqa.com.my:5000:::::::::::::::::::::'
395|backoffice  |                               ]
395|backoffice  |                             }
395|backoffice  |                           }
395|backoffice  |                         }
395|backoffice  |                       },
395|backoffice  |                       pathname: '/unity-onboarding-svc/api/parties/search'
395|backoffice  |                     },
395|backoffice  |                     _ended: true,
395|backoffice  |                     _ending: true,
395|backoffice  |                     _redirectCount: 0,
395|backoffice  |                     _redirects: [],
395|backoffice  |                     _requestBodyLength: 62,
395|backoffice  |                     _requestBodyBuffers: [
395|backoffice  |                       {
395|backoffice  |                         data: {
395|backoffice  |                           type: 'Buffer',
395|backoffice  |                           data: [
395|backoffice  |                             123,  34,  99, 108, 105, 101, 110, 116,  34, 58,
395|backoffice  |                             123,  34, 105, 100,  84, 121, 112, 101,  34, 58,
395|backoffice  |                              34,  48,  48,  49,  34,  44,  34, 105, 100, 86,
395|backoffice  |                              97, 108, 117, 101,  34,  58,  34,  57,  53, 48,
395|backoffice  |                              52,  50,  50,  48,  53,  48,  48,  57,  48, 34,
395|backoffice  |                              44,  34, 101,  99, 105, 102,  34,  58,  34, 34,
395|backoffice  |                             125, 125
395|backoffice  |                           ]
395|backoffice  |                         }
395|backoffice  |                       }
395|backoffice  |                     ],
395|backoffice  |                     _eventsCount: 3,
395|backoffice  |                     _currentRequest: '[Circular]',
395|backoffice  |                     _currentUrl: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
395|backoffice  |                     _timeout: null
395|backoffice  |                   }
395|backoffice  |                 },
395|backoffice  |                 timeout: 30000,
395|backoffice  |                 _peername: {
395|backoffice  |                   address: '10.230.21.110',
395|backoffice  |                   family: 'IPv4',
395|backoffice  |                   port: 11000
395|backoffice  |                 }
395|backoffice  |               }
395|backoffice  |             ]
395|backoffice  |           },
395|backoffice  |           freeSockets: {},
395|backoffice  |           keepAliveMsecs: 1000,
395|backoffice  |           keepAlive: false,
395|backoffice  |           maxSockets: null,
395|backoffice  |           maxFreeSockets: 256,
395|backoffice  |           scheduling: 'lifo',
395|backoffice  |           maxTotalSockets: null,
395|backoffice  |           totalSocketCount: 1,
395|backoffice  |           maxCachedSessions: 100,
395|backoffice  |           _sessionCache: { map: {}, list: [] }
395|backoffice  |         },
395|backoffice  |         method: 'post',
395|backoffice  |         url: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
395|backoffice  |         data: '{"client":{"idType":"001","idValue":"950422050090","ecif":""}}'
395|backoffice  |       },
395|backoffice  |       code: 'ERR_SSL_SSLV3_ALERT_BAD_CERTIFICATE',
395|backoffice  |       status: null
395|backoffice  |     }
395|backoffice  |   ],
395|backoffice  |   trace_id: '9e357bf806074249be90dc4dfbd7da86',
395|backoffice  |   span_id: '1c455446c8dfb13e',
395|backoffice  |   trace_flags: '01'
395|backoffice  | } +3ms
395|backoffice  | [backend] error       2025-08-05 10:52:09.929 [CustomException] 4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42
395|backoffice  |  - {
395|backoffice  |   stack: [ null ],
395|backoffice  |   value: {
395|backoffice  |     statusCode: 500,
395|backoffice  |     message: '4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42\n',
395|backoffice  |     errorCode: '4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42\n'
395|backoffice  |   },
395|backoffice  |   statusCode: 500,
395|backoffice  |   errorCode: '4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42\n',
395|backoffice  |   trace_id: '9e357bf806074249be90dc4dfbd7da86',
395|backoffice  |   span_id: '1c455446c8dfb13e',
395|backoffice  |   trace_flags: '01'
395|backoffice  | } +4ms


```



```bash

395|backoffice  |   stack: [
395|backoffice  |     {
395|backoffice  |       error: {
395|backoffice  |         code: 'ERR_SSL_SSLV3_ALERT_BAD_CERTIFICATE',
395|backoffice  |         reason: 'sslv3 alert bad certificate',
395|backoffice  |         library: 'SSL routines',
395|backoffice  |         message: '4028BCA9777F0000:error:0A000412:SSL routines:ssl3_read_bytes:sslv3 alert bad certificate:../deps/openssl/openssl/ssl/record/rec_layer_s3.c:1605:SSL alert number 42\n',
395|backoffice  |         name: 'Error',
395|backoffice  |         config: {
395|backoffice  |           transitional: {
395|backoffice  |             silentJSONParsing: true,
395|backoffice  |             forcedJSONParsing: true,
395|backoffice  |             clarifyTimeoutError: false
395|backoffice  |           },
395|backoffice  |           adapter: [ 'xhr', 'http' ],
395|backoffice  |           transformRequest: [ null ],
395|backoffice  |           transformResponse: [ null ],
395|backoffice  |           timeout: 30000,
395|backoffice  |           xsrfCookieName: 'XSRF-TOKEN',
395|backoffice  |           xsrfHeaderName: 'X-XSRF-TOKEN',
395|backoffice  |           maxContentLength: -1,
395|backoffice  |           maxBodyLength: -1,
395|backoffice  |           env: {},
395|backoffice  |           headers: {
395|backoffice  |             Accept: 'application/json, text/plain, */*',
395|backoffice  |             'Content-Type': 'application/json',
395|backoffice  |             'x-app-id': 'ETIQAPLUS',
395|backoffice  |             'x-country-code': 'MYS',
395|backoffice  |             'x-api-version': '1',
395|backoffice  |             'Accept-Language': 'en',
395|backoffice  |             'User-Agent': 'axios/1.4.0',
395|backoffice  |             'Content-Length': '81',
395|backoffice  |             'Accept-Encoding': 'gzip, compress, deflate, br'
395|backoffice  |           },
395|backoffice  |           httpsAgent: {
395|backoffice  |             _events: {},
395|backoffice  |             _eventsCount: 2,
395|backoffice  |             defaultPort: 443,
395|backoffice  |             protocol: 'https:',
395|backoffice  |             options: { rejectUnauthorized: false, noDelay: true, path: null },
395|backoffice  |             requests: {},
395|backoffice  |             sockets: {
395|backoffice  |               'apponboarding-gold.etiqa.com.my:11000::::::::false:::::::::::::': [
395|backoffice  |                 {
395|backoffice  |                   _tlsOptions: {
395|backoffice  |                     pipe: false,
395|backoffice  |                     secureContext: { context: {} },
395|backoffice  |                     isServer: false,
395|backoffice  |                     requestCert: true,
395|backoffice  |                     rejectUnauthorized: false
395|backoffice  |                   },
395|backoffice  |                   _secureEstablished: true,
395|backoffice  |                   _securePending: false,
395|backoffice  |                   _newSessionPending: false,
395|backoffice  |                   _controlReleased: true,
395|backoffice  |                   secureConnecting: false,
395|backoffice  |                   _SNICallback: null,
395|backoffice  |                   servername: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                   alpnProtocol: false,
395|backoffice  |                   authorized: false,
395|backoffice  |                   authorizationError: 'SELF_SIGNED_CERT_IN_CHAIN',
395|backoffice  |                   encrypted: true,
395|backoffice  |                   _events: {
395|backoffice  |                     close: [ null, null, null, null ],
395|backoffice  |                     timeout: [ null, null ]
395|backoffice  |                   },
395|backoffice  |                   _eventsCount: 10,
395|backoffice  |                   connecting: false,
395|backoffice  |                   _hadError: true,
395|backoffice  |                   _parent: null,
395|backoffice  |                   _host: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                   _closeAfterHandlingError: false,
395|backoffice  |                   _readableState: {
395|backoffice  |                     highWaterMark: 16384,
395|backoffice  |                     buffer: [],
395|backoffice  |                     bufferIndex: 0,
395|backoffice  |                     length: 0,
395|backoffice  |                     pipes: [],
395|backoffice  |                     awaitDrainWriters: null
395|backoffice  |                   },
395|backoffice  |                   _writableState: {
395|backoffice  |                     highWaterMark: 16384,
395|backoffice  |                     length: 0,
395|backoffice  |                     corked: 0,
395|backoffice  |                     writelen: 0,
395|backoffice  |                     bufferedIndex: 0,
395|backoffice  |                     pendingcb: 0
395|backoffice  |                   },
395|backoffice  |                   allowHalfOpen: false,
395|backoffice  |                   _sockname: null,
395|backoffice  |                   _pendingData: null,
395|backoffice  |                   _pendingEncoding: '',
395|backoffice  |                   _server: null,
395|backoffice  |                   ssl: null,
395|backoffice  |                   _requestCert: true,
395|backoffice  |                   _rejectUnauthorized: false,
395|backoffice  |                   parser: null,
395|backoffice  |                   _httpMessage: {
395|backoffice  |                     _events: { response: [ null, null ] },
395|backoffice  |                     _eventsCount: 9,
395|backoffice  |                     outputData: [],
395|backoffice  |                     outputSize: 0,
395|backoffice  |                     writable: true,
395|backoffice  |                     destroyed: false,
395|backoffice  |                     _last: true,
395|backoffice  |                     chunkedEncoding: false,
395|backoffice  |                     shouldKeepAlive: false,
395|backoffice  |                     maxRequestsOnConnectionReached: false,
395|backoffice  |                     _defaultKeepAlive: true,
395|backoffice  |                     useChunkedEncodingByDefault: true,
395|backoffice  |                     sendDate: false,
395|backoffice  |                     _removedConnection: false,
395|backoffice  |                     _removedContLen: false,
395|backoffice  |                     _removedTE: false,
395|backoffice  |                     strictContentLength: false,
395|backoffice  |                     _contentLength: '81',
395|backoffice  |                     _hasBody: true,
395|backoffice  |                     _trailer: '',
395|backoffice  |                     finished: true,
395|backoffice  |                     _headerSent: true,
395|backoffice  |                     _closed: false,
395|backoffice  |                     socket: '[Circular]',
395|backoffice  |                     _header: 'POST /unity-onboarding-svc/api/parties/search HTTP/1.1\r\n' +
395|backoffice  |                       'Accept: application/json, text/plain, */*\r\n' +
395|backoffice  |                       'Content-Type: application/json\r\n' +
395|backoffice  |                       'x-app-id: ETIQAPLUS\r\n' +
395|backoffice  |                       'x-country-code: MYS\r\n' +
395|backoffice  |                       'x-api-version: 1\r\n' +
395|backoffice  |                       'Accept-Language: en\r\n' +
395|backoffice  |                       'User-Agent: axios/1.4.0\r\n' +
395|backoffice  |                       'Content-Length: 81\r\n' +
395|backoffice  |                       'Accept-Encoding: gzip, compress, deflate, br\r\n' +
395|backoffice  |                       'traceparent: 00-0661f3302bb9c16e6fcb4e84db224d3e-a6a4bd1cd52e0c12-01\r\n' +
395|backoffice  |                       'Host: apponboarding-gold.etiqa.com.my:11000\r\n' +
395|backoffice  |                       'Connection: close\r\n' +
395|backoffice  |                       '\r\n',
395|backoffice  |                     _keepAliveTimeout: 0,
395|backoffice  |                     agent: '[Circular]',
395|backoffice  |                     method: 'POST',
395|backoffice  |                     path: '/unity-onboarding-svc/api/parties/search',
395|backoffice  |                     _ended: false,
395|backoffice  |                     res: null,
395|backoffice  |                     aborted: false,
395|backoffice  |                     timeoutCb: null,
395|backoffice  |                     upgradeOrConnect: false,
395|backoffice  |                     parser: null,
395|backoffice  |                     maxHeadersCount: null,
395|backoffice  |                     reusedSocket: false,
395|backoffice  |                     host: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                     protocol: 'https:',
395|backoffice  |                     _redirectable: {
395|backoffice  |                       _events: { socket: [ null, null ] },
395|backoffice  |                       _writableState: {
395|backoffice  |                         highWaterMark: 16384,
395|backoffice  |                         length: 0,
395|backoffice  |                         corked: 0,
395|backoffice  |                         writelen: 0,
395|backoffice  |                         bufferedIndex: 0,
395|backoffice  |                         pendingcb: 0
395|backoffice  |                       },
395|backoffice  |                       _options: {
395|backoffice  |                         maxRedirects: 21,
395|backoffice  |                         maxBodyLength: null,
395|backoffice  |                         protocol: 'https:',
395|backoffice  |                         path: '/unity-onboarding-svc/api/parties/search',
395|backoffice  |                         method: 'POST',
395|backoffice  |                         headers: {
395|backoffice  |                           Accept: 'application/json, text/plain, */*',
395|backoffice  |                           'Content-Type': 'application/json',
395|backoffice  |                           'x-app-id': 'ETIQAPLUS',
395|backoffice  |                           'x-country-code': 'MYS',
395|backoffice  |                           'x-api-version': '1',
395|backoffice  |                           'Accept-Language': 'en',
395|backoffice  |                           'User-Agent': 'axios/1.4.0',
395|backoffice  |                           'Content-Length': '81',
395|backoffice  |                           'Accept-Encoding': 'gzip, compress, deflate, br'
395|backoffice  |                         },
395|backoffice  |                         agents: { https: '[Circular]' },
395|backoffice  |                         beforeRedirects: {},
395|backoffice  |                         hostname: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |                         port: '11000',
395|backoffice  |                         agent: '[Circular]',
395|backoffice  |                         nativeProtocols: {
395|backoffice  |                           'http:': {
395|backoffice  |                             METHODS: [
395|backoffice  |                               'ACL',         'BIND',       'CHECKOUT',
395|backoffice  |                               'CONNECT',     'COPY',       'DELETE',
395|backoffice  |                               'GET',         'HEAD',       'LINK',
395|backoffice  |                               'LOCK',        'M-SEARCH',   'MERGE',
395|backoffice  |                               'MKACTIVITY',  'MKCALENDAR', 'MKCOL',
395|backoffice  |                               'MOVE',        'NOTIFY',     'OPTIONS',
395|backoffice  |                               'PATCH',       'POST',       'PROPFIND',
395|backoffice  |                               'PROPPATCH',   'PURGE',      'PUT',
395|backoffice  |                               'REBIND',      'REPORT',     'SEARCH',
395|backoffice  |                               'SOURCE',      'SUBSCRIBE',  'TRACE',
395|backoffice  |                               'UNBIND',      'UNLINK',     'UNLOCK',
395|backoffice  |                               'UNSUBSCRIBE'
395|backoffice  |                             ],
395|backoffice  |                             STATUS_CODES: {
395|backoffice  |                               '100': 'Continue',
395|backoffice  |                               '101': 'Switching Protocols',
395|backoffice  |                               '102': 'Processing',
395|backoffice  |                               '103': 'Early Hints',
395|backoffice  |                               '200': 'OK',
395|backoffice  |                               '201': 'Created',
395|backoffice  |                               '202': 'Accepted',
395|backoffice  |                               '203': 'Non-Authoritative Information',
395|backoffice  |                               '204': 'No Content',
395|backoffice  |                               '205': 'Reset Content',
395|backoffice  |                               '206': 'Partial Content',
395|backoffice  |                               '207': 'Multi-Status',
395|backoffice  |                               '208': 'Already Reported',
395|backoffice  |                               '226': 'IM Used',
395|backoffice  |                               '300': 'Multiple Choices',
395|backoffice  |                               '301': 'Moved Permanently',
395|backoffice  |                               '302': 'Found',
395|backoffice  |                               '303': 'See Other',
395|backoffice  |                               '304': 'Not Modified',
395|backoffice  |                               '305': 'Use Proxy',
395|backoffice  |                               '307': 'Temporary Redirect',
395|backoffice  |                               '308': 'Permanent Redirect',
395|backoffice  |                               '400': 'Bad Request',
395|backoffice  |                               '401': 'Unauthorized',
395|backoffice  |                               '402': 'Payment Required',
395|backoffice  |                               '403': 'Forbidden',
395|backoffice  |                               '404': 'Not Found',
395|backoffice  |                               '405': 'Method Not Allowed',
395|backoffice  |                               '406': 'Not Acceptable',
395|backoffice  |                               '407': 'Proxy Authentication Required',
395|backoffice  |                               '408': 'Request Timeout',
395|backoffice  |                               '409': 'Conflict',
395|backoffice  |                               '410': 'Gone',
395|backoffice  |                               '411': 'Length Required',
395|backoffice  |                               '412': 'Precondition Failed',
395|backoffice  |                               '413': 'Payload Too Large',
395|backoffice  |                               '414': 'URI Too Long',
395|backoffice  |                               '415': 'Unsupported Media Type',
395|backoffice  |                               '416': 'Range Not Satisfiable',
395|backoffice  |                               '417': 'Expectation Failed',
395|backoffice  |                               '418': "I'm a Teapot",
395|backoffice  |                               '421': 'Misdirected Request',
395|backoffice  |                               '422': 'Unprocessable Entity',
395|backoffice  |                               '423': 'Locked',
395|backoffice  |                               '424': 'Failed Dependency',
395|backoffice  |                               '425': 'Too Early',
395|backoffice  |                               '426': 'Upgrade Required',
395|backoffice  |                               '428': 'Precondition Required',
395|backoffice  |                               '429': 'Too Many Requests',
395|backoffice  |                               '431': 'Request Header Fields Too Large',
395|backoffice  |                               '451': 'Unavailable For Legal Reasons',
395|backoffice  |                               '500': 'Internal Server Error',
395|backoffice  |                               '501': 'Not Implemented',
395|backoffice  |                               '502': 'Bad Gateway',
395|backoffice  |                               '503': 'Service Unavailable',
395|backoffice  |                               '504': 'Gateway Timeout',
395|backoffice  |                               '505': 'HTTP Version Not Supported',
395|backoffice  |                               '506': 'Variant Also Negotiates',
395|backoffice  |                               '507': 'Insufficient Storage',
395|backoffice  |                               '508': 'Loop Detected',
395|backoffice  |                               '509': 'Bandwidth Limit Exceeded',
395|backoffice  |                               '510': 'Not Extended',
395|backoffice  |                               '511': 'Network Authentication Required'
395|backoffice  |                             },
395|backoffice  |                             maxHeaderSize: 16384,
395|backoffice  |                             globalAgent: {
395|backoffice  |                               _events: {},
395|backoffice  |                               _eventsCount: 2,
395|backoffice  |                               defaultPort: 80,
395|backoffice  |                               protocol: 'http:',
395|backoffice  |                               options: {
395|backoffice  |                                 keepAlive: true,
395|backoffice  |                                 scheduling: 'lifo',
395|backoffice  |                                 timeout: 5000,
395|backoffice  |                                 noDelay: true,
395|backoffice  |                                 path: null
395|backoffice  |                               },
395|backoffice  |                               requests: {},
395|backoffice  |                               sockets: {},
395|backoffice  |                               freeSockets: {},
395|backoffice  |                               keepAliveMsecs: 1000,
395|backoffice  |                               keepAlive: true,
395|backoffice  |                               maxSockets: null,
395|backoffice  |                               maxFreeSockets: 256,
395|backoffice  |                               scheduling: 'lifo',
395|backoffice  |                               maxTotalSockets: null,
395|backoffice  |                               totalSocketCount: 0
395|backoffice  |                             }
395|backoffice  |                           },
395|backoffice  |                           'https:': {
395|backoffice  |                             globalAgent: {
395|backoffice  |                               _events: {},
395|backoffice  |                               _eventsCount: 2,
395|backoffice  |                               defaultPort: 443,
395|backoffice  |                               protocol: 'https:',
395|backoffice  |                               options: {
395|backoffice  |                                 keepAlive: true,
395|backoffice  |                                 scheduling: 'lifo',
395|backoffice  |                                 timeout: 5000,
395|backoffice  |                                 noDelay: true,
395|backoffice  |                                 path: null
395|backoffice  |                               },
395|backoffice  |                               requests: {},
395|backoffice  |                               sockets: {},
395|backoffice  |                               freeSockets: {},
395|backoffice  |                               keepAliveMsecs: 1000,
395|backoffice  |                               keepAlive: true,
395|backoffice  |                               maxSockets: null,
395|backoffice  |                               maxFreeSockets: 256,
395|backoffice  |                               scheduling: 'lifo',
395|backoffice  |                               maxTotalSockets: null,
395|backoffice  |                               totalSocketCount: 0,
395|backoffice  |                               maxCachedSessions: 100,
395|backoffice  |                               _sessionCache: {
395|backoffice  |                                 map: {
395|backoffice  |                                   '10.230.21.116:8443:::::::::::::::::::::': {
395|backoffice  |                                     type: 'Buffer',
395|backoffice  |                                     data: [
395|backoffice  |                                        48, 130,   3, 217,   2,   1,   1,   2,
395|backoffice  |                                         2,   3,   4,   4,   2,  19,   2,   4,
395|backoffice  |                                        32, 203, 121,  28,  51, 206,  43, 173,
395|backoffice  |                                       119, 179, 169,  20, 123, 154,  10, 210,
395|backoffice  |                                         5, 236, 106,   0, 135,  98,  48, 165,
395|backoffice  |                                       226,  18, 173,  78, 183, 133,  29,   5,
395|backoffice  |                                        94,   4,  48,  94,  28,  75, 200,  23,
395|backoffice  |                                       216, 139, 123, 213, 205,  63,  81, 106,
395|backoffice  |                                       210, 148, 101, 235, 214, 192, 226, 189,
395|backoffice  |                                       226,  45, 203, 238, 176,  27, 164, 173,
395|backoffice  |                                       106,  68, 226, 253, 165,  27, 243, 125,
395|backoffice  |                                       180,  18, 204, 120,  62,  43,  31, 128,
395|backoffice  |                                        63, 110,  76, 161,
395|backoffice  |                                       ... 889 more items
395|backoffice  |                                     ]
395|backoffice  |                                   },
395|backoffice  |                                   'appedp-gold.etiqa.com.my:4443:::::::::::::::::::::': {
395|backoffice  |                                     type: 'Buffer',
395|backoffice  |                                     data: [
395|backoffice  |                                        48, 130,   5, 173,   2,   1,   1,   2,
395|backoffice  |                                         2,   3,   4,   4,   2,  19,   2,   4,
395|backoffice  |                                        32, 238,  12,  18,  56, 244, 214, 123,
395|backoffice  |                                       171,  20, 152, 130, 127,  88, 196,  18,
395|backoffice  |                                       120,   7, 196,  53, 197, 201,  52, 222,
395|backoffice  |                                       210, 186, 195, 135, 117, 113, 129, 154,
395|backoffice  |                                        97,   4,  48, 191,  89,   6, 112, 198,
395|backoffice  |                                        68, 114,   3, 111,  40, 242, 190, 177,
395|backoffice  |                                        45, 227,  50, 204, 142, 171, 221, 227,
395|backoffice  |                                         8,   9, 193, 183, 210, 208,  86,  97,
395|backoffice  |                                       185,  46, 128, 217,  31,  56,  47, 213,
395|backoffice  |                                       203,  65, 192, 106,  74, 132, 197, 114,
395|backoffice  |                                       164, 245,  95, 161,
395|backoffice  |                                       ... 1357 more items
395|backoffice  |                                     ]
395|backoffice  |                                   },
395|backoffice  |                                   'appmdm-gold.etiqa.com.my:5000:::::::::::::::::::::': {
395|backoffice  |                                     type: 'Buffer',
395|backoffice  |                                     data: [
395|backoffice  |                                        48, 130,  14, 108,   2,   1,   1,   2,
395|backoffice  |                                         2,   3,   4,   4,   2,  19,   1,   4,
395|backoffice  |                                        32, 112, 243, 173,  61,  80, 254, 165,
395|backoffice  |                                       208, 247,  26,  52, 168,  51, 151,  46,
395|backoffice  |                                       165,  82,  93,  77, 244, 119, 163,  84,
395|backoffice  |                                        36, 143,  48, 100,  87, 125, 189, 254,
395|backoffice  |                                        64,   4,  32,  12, 175, 158, 151, 243,
395|backoffice  |                                       216, 149,   0, 179, 207, 232, 165,  91,
395|backoffice  |                                       214, 247, 197, 206, 217, 105, 221, 233,
395|backoffice  |                                       164,  60, 102,  91, 113,  72,  37, 170,
395|backoffice  |                                       179, 106, 179, 161,   6,   2,   4, 104,
395|backoffice  |                                       145, 121,  71, 162,   4,   2,   2,  28,
395|backoffice  |                                        32, 163, 130,   4,
395|backoffice  |                                       ... 3596 more items
395|backoffice  |                                     ]
395|backoffice  |                                   },
395|backoffice  |                                   '172.29.75.174:8093:::::::::::::::::::::': {
395|backoffice  |                                     type: 'Buffer',
395|backoffice  |                                     data: [
395|backoffice  |                                        48, 130,   5,  58,   2,   1,   1,   2,
395|backoffice  |                                         2,   3,   3,   4,   2, 192,  47,   4,
395|backoffice  |                                        32, 104, 145, 119,  15, 102,  55, 143,
395|backoffice  |                                       141, 195, 212,  77,  16, 181, 184, 176,
395|backoffice  |                                       221, 199,  58, 164, 138, 197, 193, 110,
395|backoffice  |                                        64, 159, 117, 248, 163, 233, 164, 142,
395|backoffice  |                                       190,   4,  48,  84,  57, 250,   2, 249,
395|backoffice  |                                       133, 126, 193, 174, 165, 114,  20, 244,
395|backoffice  |                                         0, 108, 228, 201,  69,  68,  45,   6,
395|backoffice  |                                        26, 126, 233,  21, 123,  32, 154, 173,
395|backoffice  |                                        59, 220, 241, 184, 185, 119,  80, 151,
395|backoffice  |                                       113,  46,  84, 192,   0, 246, 231,  33,
395|backoffice  |                                       159,  19, 201, 161,
395|backoffice  |                                       ... 1242 more items
395|backoffice  |                                     ]
395|backoffice  |                                   }
395|backoffice  |                                 },
395|backoffice  |                                 list: [
395|backoffice  |                                   '10.230.21.116:8443:::::::::::::::::::::',
395|backoffice  |                                   'appedp-gold.etiqa.com.my:4443:::::::::::::::::::::',
395|backoffice  |                                   'appmdm-gold.etiqa.com.my:5000:::::::::::::::::::::',
395|backoffice  |                                   '172.29.75.174:8093:::::::::::::::::::::'
395|backoffice  |                                 ]
395|backoffice  |                               }
395|backoffice  |                             }
395|backoffice  |                           }
395|backoffice  |                         },
395|backoffice  |                         pathname: '/unity-onboarding-svc/api/parties/search'
395|backoffice  |                       },
395|backoffice  |                       _ended: true,
395|backoffice  |                       _ending: true,
395|backoffice  |                       _redirectCount: 0,
395|backoffice  |                       _redirects: [],
395|backoffice  |                       _requestBodyLength: 81,
395|backoffice  |                       _requestBodyBuffers: [
395|backoffice  |                         {
395|backoffice  |                           data: {
395|backoffice  |                             type: 'Buffer',
395|backoffice  |                             data: [
395|backoffice  |                               123,  34,  99, 108, 105, 101, 110, 116,  34,  58,
395|backoffice  |                               123,  34, 105, 100,  84, 121, 112, 101,  34,  58,
395|backoffice  |                                34,  48,  48,  49,  34,  44,  34, 105, 100,  86,
395|backoffice  |                                97, 108, 117, 101,  34,  58,  34,  55,  55,  49,
395|backoffice  |                                49,  48,  54,  48,  49,  53,  53,  48,  54,  34,
395|backoffice  |                                44,  34, 101,  99, 105, 102,  34,  58,  34,  80,
395|backoffice  |                                73,  77,  89,  83,  50,  53,  48,  55,  51,  69,
395|backoffice  |                                80,  80,  69,  89,  51,  57,  70,  52,  34, 125,
395|backoffice  |                               125
395|backoffice  |                             ]
395|backoffice  |                           }
395|backoffice  |                         }
395|backoffice  |                       ],
395|backoffice  |                       _eventsCount: 3,
395|backoffice  |                       _currentRequest: '[Circular]',
395|backoffice  |                       _currentUrl: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
395|backoffice  |                       _timeout: null
395|backoffice  |                     }
395|backoffice  |                   },
395|backoffice  |                   timeout: 30000,
395|backoffice  |                   _peername: {
395|backoffice  |                     address: '10.230.21.110',
395|backoffice  |                     family: 'IPv4',
395|backoffice  |                     port: 11000
395|backoffice  |                   }
395|backoffice  |                 }
395|backoffice  |               ]
395|backoffice  |             },
395|backoffice  |             freeSockets: {},
395|backoffice  |             keepAliveMsecs: 1000,
395|backoffice  |             keepAlive: false,
395|backoffice  |             maxSockets: null,
395|backoffice  |             maxFreeSockets: 256,
395|backoffice  |             scheduling: 'lifo',
395|backoffice  |             maxTotalSockets: null,
395|backoffice  |             totalSocketCount: 1,
395|backoffice  |             maxCachedSessions: 100,
395|backoffice  |             _sessionCache: { map: {}, list: [] }
395|backoffice  |           },
395|backoffice  |           method: 'post',
395|backoffice  |           url: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
395|backoffice  |           data: '{"client":{"idType":"001","idValue":"771106015506","ecif":"PIMYS25073EPPEY39F4"}}'
395|backoffice  |         },
395|backoffice  |         request: {
395|backoffice  |           _events: { socket: [ null, null ] },
395|backoffice  |           _writableState: {
395|backoffice  |             highWaterMark: 16384,
395|backoffice  |             length: 0,
395|backoffice  |             corked: 0,
395|backoffice  |             writelen: 0,
395|backoffice  |             bufferedIndex: 0,
395|backoffice  |             pendingcb: 0
395|backoffice  |           },
395|backoffice  |           _options: {
395|backoffice  |             maxRedirects: 21,
395|backoffice  |             maxBodyLength: null,
395|backoffice  |             protocol: 'https:',
395|backoffice  |             path: '/unity-onboarding-svc/api/parties/search',
395|backoffice  |             method: 'POST',
395|backoffice  |             headers: {
395|backoffice  |               Accept: 'application/json, text/plain, */*',
395|backoffice  |               'Content-Type': 'application/json',
395|backoffice  |               'x-app-id': 'ETIQAPLUS',
395|backoffice  |               'x-country-code': 'MYS',
395|backoffice  |               'x-api-version': '1',
395|backoffice  |               'Accept-Language': 'en',
395|backoffice  |               'User-Agent': 'axios/1.4.0',
395|backoffice  |               'Content-Length': '81',
395|backoffice  |               'Accept-Encoding': 'gzip, compress, deflate, br'
395|backoffice  |             },
395|backoffice  |             agents: { https: '[Circular]' },
395|backoffice  |             beforeRedirects: {},
395|backoffice  |             hostname: 'apponboarding-gold.etiqa.com.my',
395|backoffice  |             port: '11000',
395|backoffice  |             agent: '[Circular]',
395|backoffice  |             nativeProtocols: {
395|backoffice  |               'http:': {
395|backoffice  |                 METHODS: [
395|backoffice  |                   'ACL',         'BIND',       'CHECKOUT',
395|backoffice  |                   'CONNECT',     'COPY',       'DELETE',
395|backoffice  |                   'GET',         'HEAD',       'LINK',
395|backoffice  |                   'LOCK',        'M-SEARCH',   'MERGE',
395|backoffice  |                   'MKACTIVITY',  'MKCALENDAR', 'MKCOL',
395|backoffice  |                   'MOVE',        'NOTIFY',     'OPTIONS',
395|backoffice  |                   'PATCH',       'POST',       'PROPFIND',
395|backoffice  |                   'PROPPATCH',   'PURGE',      'PUT',
395|backoffice  |                   'REBIND',      'REPORT',     'SEARCH',
395|backoffice  |                   'SOURCE',      'SUBSCRIBE',  'TRACE',
395|backoffice  |                   'UNBIND',      'UNLINK',     'UNLOCK',
395|backoffice  |                   'UNSUBSCRIBE'
395|backoffice  |                 ],
395|backoffice  |                 STATUS_CODES: {
395|backoffice  |                   '100': 'Continue',
395|backoffice  |                   '101': 'Switching Protocols',
395|backoffice  |                   '102': 'Processing',
395|backoffice  |                   '103': 'Early Hints',
395|backoffice  |                   '200': 'OK',
395|backoffice  |                   '201': 'Created',
395|backoffice  |                   '202': 'Accepted',
395|backoffice  |                   '203': 'Non-Authoritative Information',
395|backoffice  |                   '204': 'No Content',
395|backoffice  |                   '205': 'Reset Content',
395|backoffice  |                   '206': 'Partial Content',
395|backoffice  |                   '207': 'Multi-Status',
395|backoffice  |                   '208': 'Already Reported',
395|backoffice  |                   '226': 'IM Used',
395|backoffice  |                   '300': 'Multiple Choices',
395|backoffice  |                   '301': 'Moved Permanently',
395|backoffice  |                   '302': 'Found',
395|backoffice  |                   '303': 'See Other',
395|backoffice  |                   '304': 'Not Modified',
395|backoffice  |                   '305': 'Use Proxy',
395|backoffice  |                   '307': 'Temporary Redirect',
395|backoffice  |                   '308': 'Permanent Redirect',
395|backoffice  |                   '400': 'Bad Request',
395|backoffice  |                   '401': 'Unauthorized',
395|backoffice  |                   '402': 'Payment Required',
395|backoffice  |                   '403': 'Forbidden',
395|backoffice  |                   '404': 'Not Found',
395|backoffice  |                   '405': 'Method Not Allowed',
395|backoffice  |                   '406': 'Not Acceptable',
395|backoffice  |                   '407': 'Proxy Authentication Required',
395|backoffice  |                   '408': 'Request Timeout',
395|backoffice  |                   '409': 'Conflict',
395|backoffice  |                   '410': 'Gone',
395|backoffice  |                   '411': 'Length Required',
395|backoffice  |                   '412': 'Precondition Failed',
395|backoffice  |                   '413': 'Payload Too Large',
395|backoffice  |                   '414': 'URI Too Long',
395|backoffice  |                   '415': 'Unsupported Media Type',
395|backoffice  |                   '416': 'Range Not Satisfiable',
395|backoffice  |                   '417': 'Expectation Failed',
395|backoffice  |                   '418': "I'm a Teapot",
395|backoffice  |                   '421': 'Misdirected Request',
395|backoffice  |                   '422': 'Unprocessable Entity',
395|backoffice  |                   '423': 'Locked',
395|backoffice  |                   '424': 'Failed Dependency',
395|backoffice  |                   '425': 'Too Early',
395|backoffice  |                   '426': 'Upgrade Required',
395|backoffice  |                   '428': 'Precondition Required',
395|backoffice  |                   '429': 'Too Many Requests',
395|backoffice  |                   '431': 'Request Header Fields Too Large',
395|backoffice  |                   '451': 'Unavailable For Legal Reasons',
395|backoffice  |                   '500': 'Internal Server Error',
395|backoffice  |                   '501': 'Not Implemented',
395|backoffice  |                   '502': 'Bad Gateway',
395|backoffice  |                   '503': 'Service Unavailable',
395|backoffice  |                   '504': 'Gateway Timeout',
395|backoffice  |                   '505': 'HTTP Version Not Supported',
395|backoffice  |                   '506': 'Variant Also Negotiates',
395|backoffice  |                   '507': 'Insufficient Storage',
395|backoffice  |                   '508': 'Loop Detected',
395|backoffice  |                   '509': 'Bandwidth Limit Exceeded',
395|backoffice  |                   '510': 'Not Extended',
395|backoffice  |                   '511': 'Network Authentication Required'
395|backoffice  |                 },
395|backoffice  |                 maxHeaderSize: 16384,
395|backoffice  |                 globalAgent: {
395|backoffice  |                   _events: {},
395|backoffice  |                   _eventsCount: 2,
395|backoffice  |                   defaultPort: 80,
395|backoffice  |                   protocol: 'http:',
395|backoffice  |                   options: {
395|backoffice  |                     keepAlive: true,
395|backoffice  |                     scheduling: 'lifo',
395|backoffice  |                     timeout: 5000,
395|backoffice  |                     noDelay: true,
395|backoffice  |                     path: null
395|backoffice  |                   },
395|backoffice  |                   requests: {},
395|backoffice  |                   sockets: {},
395|backoffice  |                   freeSockets: {},
395|backoffice  |                   keepAliveMsecs: 1000,
395|backoffice  |                   keepAlive: true,
395|backoffice  |                   maxSockets: null,
395|backoffice  |                   maxFreeSockets: 256,
395|backoffice  |                   scheduling: 'lifo',
395|backoffice  |                   maxTotalSockets: null,
395|backoffice  |                   totalSocketCount: 0
395|backoffice  |                 }
395|backoffice  |               },
395|backoffice  |               'https:': {
395|backoffice  |                 globalAgent: {
395|backoffice  |                   _events: {},
395|backoffice  |                   _eventsCount: 2,
395|backoffice  |                   defaultPort: 443,
395|backoffice  |                   protocol: 'https:',
395|backoffice  |                   options: {
395|backoffice  |                     keepAlive: true,
395|backoffice  |                     scheduling: 'lifo',
395|backoffice  |                     timeout: 5000,
395|backoffice  |                     noDelay: true,
395|backoffice  |                     path: null
395|backoffice  |                   },
395|backoffice  |                   requests: {},
395|backoffice  |                   sockets: {},
395|backoffice  |                   freeSockets: {},
395|backoffice  |                   keepAliveMsecs: 1000,
395|backoffice  |                   keepAlive: true,
395|backoffice  |                   maxSockets: null,
395|backoffice  |                   maxFreeSockets: 256,
395|backoffice  |                   scheduling: 'lifo',
395|backoffice  |                   maxTotalSockets: null,
395|backoffice  |                   totalSocketCount: 0,
395|backoffice  |                   maxCachedSessions: 100,
395|backoffice  |                   _sessionCache: {
395|backoffice  |                     map: {
395|backoffice  |                       '10.230.21.116:8443:::::::::::::::::::::': {
395|backoffice  |                         type: 'Buffer',
395|backoffice  |                         data: [
395|backoffice  |                            48, 130,   3, 217,   2,   1,   1,   2,   2,   3,   4,
395|backoffice  |                             4,   2,  19,   2,   4,  32, 203, 121,  28,  51, 206,
395|backoffice  |                            43, 173, 119, 179, 169,  20, 123, 154,  10, 210,   5,
395|backoffice  |                           236, 106,   0, 135,  98,  48, 165, 226,  18, 173,  78,
395|backoffice  |                           183, 133,  29,   5,  94,   4,  48,  94,  28,  75, 200,
395|backoffice  |                            23, 216, 139, 123, 213, 205,  63,  81, 106, 210, 148,
395|backoffice  |                           101, 235, 214, 192, 226, 189, 226,  45, 203, 238, 176,
395|backoffice  |                            27, 164, 173, 106,  68, 226, 253, 165,  27, 243, 125,
395|backoffice  |                           180,  18, 204, 120,  62,  43,  31, 128,  63, 110,  76,
395|backoffice  |                           161,
395|backoffice  |                           ... 889 more items
395|backoffice  |                         ]
395|backoffice  |                       },
395|backoffice  |                       'appedp-gold.etiqa.com.my:4443:::::::::::::::::::::': {
395|backoffice  |                         type: 'Buffer',
395|backoffice  |                         data: [
395|backoffice  |                            48, 130,   5, 173,   2,   1,   1,   2,   2,   3,   4,
395|backoffice  |                             4,   2,  19,   2,   4,  32, 238,  12,  18,  56, 244,
395|backoffice  |                           214, 123, 171,  20, 152, 130, 127,  88, 196,  18, 120,
395|backoffice  |                             7, 196,  53, 197, 201,  52, 222, 210, 186, 195, 135,
395|backoffice  |                           117, 113, 129, 154,  97,   4,  48, 191,  89,   6, 112,
395|backoffice  |                           198,  68, 114,   3, 111,  40, 242, 190, 177,  45, 227,
395|backoffice  |                            50, 204, 142, 171, 221, 227,   8,   9, 193, 183, 210,
395|backoffice  |                           208,  86,  97, 185,  46, 128, 217,  31,  56,  47, 213,
395|backoffice  |                           203,  65, 192, 106,  74, 132, 197, 114, 164, 245,  95,
395|backoffice  |                           161,
395|backoffice  |                           ... 1357 more items
395|backoffice  |                         ]
395|backoffice  |                       },
395|backoffice  |                       'appmdm-gold.etiqa.com.my:5000:::::::::::::::::::::': {
395|backoffice  |                         type: 'Buffer',
395|backoffice  |                         data: [
395|backoffice  |                            48, 130,  14, 108,   2,   1,   1,   2,   2,   3,   4,
395|backoffice  |                             4,   2,  19,   1,   4,  32, 112, 243, 173,  61,  80,
395|backoffice  |                           254, 165, 208, 247,  26,  52, 168,  51, 151,  46, 165,
395|backoffice  |                            82,  93,  77, 244, 119, 163,  84,  36, 143,  48, 100,
395|backoffice  |                            87, 125, 189, 254,  64,   4,  32,  12, 175, 158, 151,
395|backoffice  |                           243, 216, 149,   0, 179, 207, 232, 165,  91, 214, 247,
395|backoffice  |                           197, 206, 217, 105, 221, 233, 164,  60, 102,  91, 113,
395|backoffice  |                            72,  37, 170, 179, 106, 179, 161,   6,   2,   4, 104,
395|backoffice  |                           145, 121,  71, 162,   4,   2,   2,  28,  32, 163, 130,
395|backoffice  |                             4,
395|backoffice  |                           ... 3596 more items
395|backoffice  |                         ]
395|backoffice  |                       },
395|backoffice  |                       '172.29.75.174:8093:::::::::::::::::::::': {
395|backoffice  |                         type: 'Buffer',
395|backoffice  |                         data: [
395|backoffice  |                            48, 130,   5,  58,   2,   1,   1,   2,   2,   3,   3,
395|backoffice  |                             4,   2, 192,  47,   4,  32, 104, 145, 119,  15, 102,
395|backoffice  |                            55, 143, 141, 195, 212,  77,  16, 181, 184, 176, 221,
395|backoffice  |                           199,  58, 164, 138, 197, 193, 110,  64, 159, 117, 248,
395|backoffice  |                           163, 233, 164, 142, 190,   4,  48,  84,  57, 250,   2,
395|backoffice  |                           249, 133, 126, 193, 174, 165, 114,  20, 244,   0, 108,
395|backoffice  |                           228, 201,  69,  68,  45,   6,  26, 126, 233,  21, 123,
395|backoffice  |                            32, 154, 173,  59, 220, 241, 184, 185, 119,  80, 151,
395|backoffice  |                           113,  46,  84, 192,   0, 246, 231,  33, 159,  19, 201,
395|backoffice  |                           161,
395|backoffice  |                           ... 1242 more items
395|backoffice  |                         ]
395|backoffice  |                       }
395|backoffice  |                     },
395|backoffice  |                     list: [
395|backoffice  |                       '10.230.21.116:8443:::::::::::::::::::::',
395|backoffice  |                       'appedp-gold.etiqa.com.my:4443:::::::::::::::::::::',
395|backoffice  |                       'appmdm-gold.etiqa.com.my:5000:::::::::::::::::::::',
395|backoffice  |                       '172.29.75.174:8093:::::::::::::::::::::'
395|backoffice  |                     ]
395|backoffice  |                   }
395|backoffice  |                 }
395|backoffice  |               }
395|backoffice  |             },
395|backoffice  |             pathname: '/unity-onboarding-svc/api/parties/search'
395|backoffice  |           },
395|backoffice  |           _ended: true,
395|backoffice  |           _ending: true,
395|backoffice  |           _redirectCount: 0,
395|backoffice  |           _redirects: [],
395|backoffice  |           _requestBodyLength: 81,
395|backoffice  |           _requestBodyBuffers: [
395|backoffice  |             {
395|backoffice  |               data: {
395|backoffice  |                 type: 'Buffer',
395|backoffice  |                 data: [
395|backoffice  |                   123,  34, 99, 108, 105, 101, 110, 116,  34,  58, 123, 34,
395|backoffice  |                   105, 100, 84, 121, 112, 101,  34,  58,  34,  48,  48, 49,
395|backoffice  |                    34,  44, 34, 105, 100,  86,  97, 108, 117, 101,  34, 58,
395|backoffice  |                    34,  55, 55,  49,  49,  48,  54,  48,  49,  53,  53, 48,
395|backoffice  |                    54,  34, 44,  34, 101,  99, 105, 102,  34,  58,  34, 80,
395|backoffice  |                    73,  77, 89,  83,  50,  53,  48,  55,  51,  69,  80, 80,
395|backoffice  |                    69,  89, 51,  57,  70,  52,  34, 125, 125
395|backoffice  |                 ]
395|backoffice  |               }
395|backoffice  |             }
395|backoffice  |           ],
395|backoffice  |           _eventsCount: 3,
395|backoffice  |           _currentRequest: '[Circular]',
395|backoffice  |           _currentUrl: 'https://apponboarding-gold.etiqa.com.my:11000/unity-onboarding-svc/api/parties/search',
395|backoffice  |           _timeout: null
395|backoffice  |         },
395|backoffice  |         cause: {
395|backoffice  |           library: 'SSL routines',
395|backoffice  |           reason: 'sslv3 alert bad certificate',
395|backoffice  |           code: 'ERR_SSL_SSLV3_ALERT_BAD_CERTIFICATE'
395|backoffice  |         }
395|backoffice  |       }
395|backoffice  |     }
395|backoffice  |   ],
395|backoffice  |   trace_id: '0661f3302bb9c16e6fcb4e84db224d3e',
395|backoffice  |   span_id: 'd6d3cec399507a9d',
395|backoffice  |   trace_flags: '01'
395|backoffice  | } +1ms
395|backoffice  | [backend] error       2025-08-05 11:24:10.987 PortalUserService: retrieveCdhDataDirectly - {
395|backoffice  
```


test on server:
```bash
openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -info -noout -passin pass:P@ssw0rd
```

## Common Server-Side Issues

| Issue                                   | Symptoms                            | Diagnostic Command           |
| --------------------------------------- | ----------------------------------- | ---------------------------- |
| Certificate not in server's trust store | ERR_SSL_SSLV3_ALERT_BAD_CERTIFICATE | Check server logs            |
| Wrong certificate domain                | ERR_SSL_SSLV3_ALERT_BAD_CERTIFICATE | openssl x509 -noout -subject |
| Certificate expired                     | ERR_SSL_SSLV3_ALERT_BAD_CERTIFICATE | openssl x509 -noout -dates   |
| Server requires different CA            | Connection fails                    | Check server documentation   |
| Server not configured for client certs  | Connection fails                    | Contact CDH team             |


1. Use -cert parameter

```
# Try this alternative syntax for P12 files

openssl s_client -connect apponboarding-gold.etiqa.com.my:11000 \

-cert 250804-appetqplus-gold.etiqa.com.my.p12 \

-certform DER \

-pass pass:P@ssw0rd \

-servername apponboarding-gold.etiqa.com.my
```
Response
```bash

[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl s_client -connect apponboarding-gold.etiqa.com.my:11000 \
>   -cert 250804-appetqplus-gold.etiqa.com.my.p12 \
>   -certform DER \
>   -pass pass:P@ssw0rd \
>   -servername apponboarding-gold.etiqa.com.my
unable to load client certificate private key file
140331774121792:error:0909006C:PEM routines:get_name:no start line:crypto/pem/pem_lib.c:745:Expecting: ANY PRIVATE KEY
[srv_etqsml@ETQSMLUATAPP001 cdh]$

```


```
140351991551808:error:28078065:UI routines:UI_set_result_ex:result too small:crypto/ui/ui_lib.c:905:You must type in 4 to 1024 characters
140351991551808:error:2807106B:UI routines:UI_process:processing error:crypto/ui/ui_lib.c:545:while reading strings
140351991551808:error:0906406D:PEM routines:PEM_def_callback:problems getting password:crypto/pem/pem_lib.c:59:
140351991551808:error:0907E06F:PEM routines:do_pk8pkey:read key:crypto/pem/pem_pk8.c:83:
[srv_etqsml@ETQSMLUATAPP001 cdh]$ # First, extract the certificate and private key from P12
openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -clcerts -nokeys -passin pass:P@ssw0rd > client_cert.pem
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -clcerts -nokeys -passin pass:P@ssw0rd > client_cert.pem
openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -nocerts -passin pass:P@ssw0rd > private_key.pem
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -nocerts -passin pass:P@ssw0rd > private_key.pem
Enter PEM pass phrase:
Error outputting keys and certificates
139780505421632:error:28078065:UI routines:UI_set_result_ex:result too small:crypto/ui/ui_lib.c:905:You must type in 4 to 1024 characters
139780505421632:error:2807106B:UI routines:UI_process:processing error:crypto/ui/ui_lib.c:545:while reading strings
139780505421632:error:0906406D:PEM routines:PEM_def_callback:problems getting password:crypto/pem/pem_lib.c:59:
139780505421632:error:0907E06F:PEM routines:do_pk8pkey:read key:crypto/pem/pem_pk8.c:83:
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -clcerts -nokeys -passin pass:P@ssw0rd > client_cert.pem
[srv_etqsml@ETQSMLUATAPP001 cdh]$
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -nocerts -nodes -passin pass:P@ssw0rd > private_key.pem
[srv_etqsml@ETQSMLUATAPP001 cdh]$
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl pkcs12 -in 250804-appetqplus-gold.etiqa.com.my.p12 -cacerts -nokeys -passin pass:P@ssw0rd > ca_certs.pem
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl s_client -connect apponboarding-gold.etiqa.com.my:11000 \
>   -cert client_cert.pem \
>   -key private_key.pem \
>   -CAfile ca_certs.pem \
>   -servername apponboarding-gold.etiqa.com.my \
>   -verify_return_error
CONNECTED(00000003)
depth=1 CN = Maybank Group Internal CA V2
verify return:1
depth=0 C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my
verify return:1
---
Certificate chain
 0 s:C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my
   i:CN = Maybank Group Internal CA V2
 1 s:CN = Maybank Group Internal CA V2
   i:CN = Maybank Group Internal CA V2
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIE8DCCA9igAwIBAgITIwAAEcvBmJepy5vzqAAAAAARyzANBgkqhkiG9w0BAQsF
ADAnMSUwIwYDVQQDExxNYXliYW5rIEdyb3VwIEludGVybmFsIENBIFYyMCAXDTI1
MDYwNDA4MjUyN1oYDzIwNzAwMzA2MDMxODIyWjCBmzELMAkGA1UEBhMCTVkxHDAa
BgNVBAgTE1dpbGF5YWggUGVyc2VrdXR1YW4xFTATBgNVBAcTDEt1YWxhIEx1bXB1
cjEfMB0GA1UEChMWTWFsYXlhbiBCYW5raW5nIEJlcmhhZDEMMAoGA1UECxMDTVNT
MSgwJgYDVQQDEx9hcHBvbmJvYXJkaW5nLWdvbGQuZXRpcWEuY29tLm15MIIBIjAN
BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAoI4vNH2rC3yxjLVEm2nUsoqVPkXY
WRHI5K88gfQK6G8aAwYpQeoBp3KpC5zYQD0gupmxzJV6NkhbmAFDRgOIwlH+PsQf
YV06K5uPZ4vvxBxETb4mKVX2kFx1Bb20cne/CmwXwEheItzopS9U0gh+d9Jk8xOq
3BHI4DdVWAOZKiItFp+cvy7oGCzln4h0yDWTp3+9OWaUVzpoWmoq4fDOcy+qdpY9
h5o8bAT+qaq/81fS4omo6iAAU5mZw9q22kedr5ordROKsmx06cIpr5FG86kN+XYo
6wDNAZHeGJGtdv7QR/mEJfYQIna09ykvOaM8+aJAagLa2dCSrPZQKPFTJwIDAQAB
o4IBnDCCAZgwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMAsGA1UdDwQE
AwIEsDAdBgNVHQ4EFgQU/1h24JMxkdlaZItDO0ywJQS8qLAwTwYDVR0RBEgwRoIf
YXBwb25ib2FyZGluZy1nb2xkLmV0aXFhLmNvbS5teYIjd3d3LmFwcG9uYm9hcmRp
bmctZ29sZC5ldGlxYS5jb20ubXkwHwYDVR0jBBgwFoAUR0sClxmYfv4cfUKAcy0l
t3NDBwUwWQYDVR0fBFIwUDBOoEygSoZIZmlsZTovLy8vTUJCQ0FQUkQwMDEvQ2Vy
dEVucm9sbC9NYXliYW5rJTIwR3JvdXAlMjBJbnRlcm5hbCUyMENBJTIwVjIuY3Js
MHAGCCsGAQUFBwEBBGQwYjBgBggrBgEFBQcwAoZUZmlsZTovLy8vTUJCQ0FQUkQw
MDEvQ2VydEVucm9sbC9NQkJDQVBSRDAwMV9NYXliYW5rJTIwR3JvdXAlMjBJbnRl
cm5hbCUyMENBJTIwVjIuY3J0MAwGA1UdEwEB/wQCMAAwDQYJKoZIhvcNAQELBQAD
ggEBAD1p4fLCgJaBHlTa7ofR45gC07XAua3iJAWyZjL1zNDnR00eGpLKxQcjDgqe
aGO/PF8/ic9Gs0D6prIknzS7SHGpn3uaE23sUF4z7fyXBEItfCwkXwQRvnrXjAUM
DxNif9QtWOt0UF5oNRH3gctOA/nc8q+OlTJ2ZPOq1LqGufAOP4Uo7LbHhUtVqgAS
efnbQaTfxxmUfl9qUPEMEi5OBMQnRXInannElasSyl7vFrBFn7SOaB9rkEdXHauV
zcXFfyBYDhn1rwOC00grHReDmAp3QU868jgAZ1qiiiWfNyPxzHjdp3uAQVLL3DdB
Yt9wY96Q2LNq7erQyc1th4Mp2pE=
-----END CERTIFICATE-----
subject=C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my

issuer=CN = Maybank Group Internal CA V2

---
Acceptable client certificate CA names
C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apppartner-gold.etiqa.com.my
C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my
C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = appetqplus-gold.etiqa.com.my
Requested Signature Algorithms: ECDSA+SHA256:ECDSA+SHA384:ECDSA+SHA512:Ed25519:Ed448:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA+SHA256:RSA+SHA384:RSA+SHA512
Shared Requested Signature Algorithms: ECDSA+SHA256:ECDSA+SHA384:ECDSA+SHA512:Ed25519:Ed448:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA+SHA256:RSA+SHA384:RSA+SHA512
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 3159 bytes and written 2781 bytes
Verification: OK
---
New, TLSv1.3, Cipher is TLS_AES_128_GCM_SHA256
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_128_GCM_SHA256
    Session-ID: FCB47047704B56DF90863688F54EDDECFA6760417E9B35C2AC7EF6A84D5A7E8F
    Session-ID-ctx:
    Resumption PSK: BFE79870F789B9CBAA09FDD51A58CC07375A5A540CEE3BD8E9A57F9D70A9FDB3
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 86400 (seconds)
    TLS session ticket:
    0000 - bc d4 e4 6b 5f ed 96 89-cf 46 07 c5 d6 d1 e0 33   ...k_....F.....3
    0010 - a1 17 66 18 6f 62 60 6f-9f a3 9b b0 22 f5 c0 ae   ..f.ob`o...."...
    0020 - be dc e3 0a 68 88 2b cd-f5 81 d0 45 89 b9 25 35   ....h.+....E..%5
    0030 - 9c c6 42 4c 6a 36 8a 73-c5 7b ee 04 22 ad cb 4d   ..BLj6.s.{.."..M
    0040 - c7 20 dc fa 15 6e 63 1e-60 ad c1 6e 29 ca 24 98   . ...nc.`..n).$.
    0050 - 63 65 2a 01 04 c6 0f e8-2f e5 d9 73 fb e1 af 4d   ce*...../..s...M
    0060 - dc 98 b9 cb ee 30 75 c4-ad 62 53 09 4f d4 43 e7   .....0u..bS.O.C.
    0070 - 7c 3f df 06 0c fd b8 20-f6 ec 64 43 57 fe ab eb   |?..... ..dCW...
    0080 - 2e d0 db 03 f2 09 fe 30-05 19 60 43 3c 59 d0 43   .......0..`C<Y.C
    0090 - 0e 03 45 fc 38 4c 7c 36-c4 cf e8 0a fd c2 11 2e   ..E.8L|6........
    00a0 - bf e2 4b 62 67 71 1a eb-d7 49 6a b9 57 73 c2 43   ..Kbgq...Ij.Ws.C
    00b0 - 9d c5 c2 52 e2 af 06 bb-f2 55 cd d8 13 aa 8f 66   ...R.....U.....f
    00c0 - d0 f5 db 0d 05 42 6f cb-7a 99 78 cc bf 82 7d 46   .....Bo.z.x...}F
    00d0 - 9f de a6 08 82 53 11 97-88 b5 71 23 99 4f ed 5a   .....S....q#.O.Z
    00e0 - ac 08 83 1a ac dc 44 e1-a2 e0 f2 51 dc 79 2a 8a   ......D....Q.y*.
    00f0 - b1 f3 86 ed 1a c4 bf c3-24 1e 0e 81 86 e6 5e 14   ........$.....^.
    0100 - 4b 03 4c cd fb 1a c1 48-69 6d 2d 67 0e ac 2b d0   K.L....Him-g..+.
    0110 - 02 6b 04 4d de 12 f8 fc-72 49 d0 68 24 80 36 dc   .k.M....rI.h$.6.
    0120 - dd 95 a3 b4 75 0d f1 0b-51 c3 1a 35 e4 a6 fe 40   ....u...Q..5...@
    0130 - 37 a8 9c 39 be 81 9c f7-c5 3f 35 63 9e 68 a4 3e   7..9.....?5c.h.>
    0140 - e3 ff dd 2e f5 d9 66 e9-72 a3 3c db ef 54 2e c5   ......f.r.<..T..
    0150 - c4 47 28 ae 22 6c f7 b2-c4 13 20 ea 36 a0 34 37   .G(."l.... .6.47
    0160 - ed 0f ab 32 5e f8 14 4d-94 47 fd 57 92 1f 9e 08   ...2^..M.G.W....
    0170 - c5 24 10 f6 0f 12 f8 dd-0e 26 90 a4 da 0c 34 14   .$.......&....4.
    0180 - 93 bb 6e 2e 45 c5 97 09-ef 6e cc d5 d5 60 e6 94   ..n.E....n...`..
    0190 - e0 5c 1c 1e 87 8c a2 b3-65 3d 52 1e 4c e4 af 17   .\......e=R.L...
    01a0 - 44 61 25 79 f1 bc 89 37-7d 94 95 d8 a0 60 05 fa   Da%y...7}....`..
    01b0 - d2 53 fd 15 3e 56 1d ae-24 f0 3d 32 a4 98 e2 67   .S..>V..$.=2...g
    01c0 - 3a a4 69 5e 37 c8 c7 51-33 e0 a0 e9 30 62 43 ef   :.i^7..Q3...0bC.
    01d0 - d9 cb 4b a5 44 c3 ea 06-69 b5 8b 94 1e 1d 22 68   ..K.D...i....."h
    01e0 - de f5 a1 82 ef 3f fd 18-fd a1 6c 6c 13 1c d1 fd   .....?....ll....
    01f0 - 03 14 fe ae ce e1 9a 30-79 69 46 d7 8d 78 a1 49   .......0yiF..x.I
    0200 - dd ff 3b 16 50 e0 ac b2-18 0c 94 2c 7e 6c 1e 6a   ..;.P......,~l.j
    0210 - 38 89 2c 8e 83 db 58 5d-47 56 45 f8 10 e7 1d 66   8.,...X]GVE....f
    0220 - 8c 81 1f 2e 2b 66 76 0b-7f 33 c3 16 88 85 a1 45   ....+fv..3.....E
    0230 - 05 84 f7 8a 06 85 7b 94-18 f2 e2 59 93 07 cd ed   ......{....Y....
    0240 - b8 1d 22 9f 18 10 0a 34-74 d4 9f 94 1f f8 39 30   .."....4t.....90
    0250 - a0 98 78 e4 2e 0b ed d9-b3 59 5f b4 dc 5e ab b2   ..x......Y_..^..
    0260 - b0 df 59 4c df f3 04 a5-d5 37 cb 09 02 5d 55 48   ..YL.....7...]UH
    0270 - 1f 7d c6 49 f8 48 0b ac-d4 bf 51 ea 9c a5 be 11   .}.I.H....Q.....
    0280 - 25 f5 a5 d3 96 13 1a 0c-6d ee 13 c0 ea 84 94 eb   %.......m.......
    0290 - df f7 36 cc ad b1 0c ba-39 c7 ff ba 2f 89 bd a2   ..6.....9.../...
    02a0 - d1 3e ad 05 ed 7d f0 77-6c 19 b1 ab f5 5f 67 be   .>...}.wl...._g.
    02b0 - 40 09 52 72 0e 25 01 49-fe 04 f8 e5 3a 91 4b d2   @.Rr.%.I....:.K.
    02c0 - 72 58 e4 c1 56 8a 9b b4-9c 29 1e 23 44 37 3b 10   rX..V....).#D7;.
    02d0 - 02 e1 c7 e6 15 4e ee 1e-72 fb d4 32 bc 91 fe 7d   .....N..r..2...}
    02e0 - e3 23 38 4f 96 e9 df de-4f 05 07 ec 27 01 5c 34   .#8O....O...'.\4
    02f0 - 5e 0a 86 9f 8a f4 37 ca-ad d9 24 05 c5 b0 cd d0   ^.....7...$.....
    0300 - a8 99 40 de a3 3f 6f d2-0f 17 58 d2 dd ac 0f a0   ..@..?o...X.....
    0310 - e8 21 bf 56 05 4e 3f da-36 71 ca ed 82 88 49 48   .!.V.N?.6q....IH
    0320 - b7 b4 1f 44 c1 c8 5c 40-02 44 e1 0e 2a ac ad 48   ...D..\@.D..*..H
    0330 - 6c f9 b1 9e e8 a7 b6 b5-fe a6 fc fe 27 dc fb a7   l...........'...
    0340 - 8d 0c b2 a1 57 8e bd b2-5c e2 7b de 93 e8 92 d6   ....W...\.{.....
    0350 - 61 7e b6 47 af 2f 04 03-7b dc 7f 1a 7b 84 01 43   a~.G./..{...{..C
    0360 - bd c6 bc 4f c1 3d c0 a0-1a 98 20 ab 26 c7 22 7c   ...O.=.... .&."|
    0370 - e2 99 f6 2b 32 e3 19 5d-5c 1f 53 ef a1 d8 16 f6   ...+2..]\.S.....
    0380 - f3 ff 52 99 9f b8 5c 87-9b e7 c2 61 18 27 cb 90   ..R...\....a.'..
    0390 - 74 d8 98 4b 2b ee 44 df-06 23 b9 4f ed 8d 53 4b   t..K+.D..#.O..SK
    03a0 - 67 f7 4a 7f 90 c2 18 46-77 4d 55 c5 89 d3 be b0   g.J....FwMU.....
    03b0 - 55 c7 18 5f 04 7b 31 23-cc 62 a0 62 9b 9b db dd   U.._.{1#.b.b....
    03c0 - df 8e 42 33 74 ba 09 25-10 ba 94 41 73 91 86 d3   ..B3t..%...As...
    03d0 - 67 c7 f8 d0 0b e5 e0 ed-bf bb 09 b0 d1 90 8c 40   g..............@
    03e0 - 99 bb 04 38 c1 ba 77 5e-ff c5 0e 90 0e c0 58 26   ...8..w^......X&
    03f0 - 8c f3 a3 7e 8a 42 59 b2-f4 01 a2 57 76 21 fb e8   ...~.BY....Wv!..
    0400 - 03 79 85 a7 ff 39 ab ac-5d ce f0 e8 59 7b ee ac   .y...9..]...Y{..
    0410 - 27 82 04 45 2d 19 dd df-5d 78 d6 6d eb 09 68 db   '..E-...]x.m..h.
    0420 - f0 47 e1 c6 9b c1 b7 6a-04 2d c3 66 8f b8 8e ab   .G.....j.-.f....
    0430 - b2 a3 58 c7 2b c6 6b 29-13 be 66 93 8c e4 0c de   ..X.+.k)..f.....
    0440 - 75 64 da e3 56 e3 df 62-e7 5a c4 56 e0 37 53 37   ud..V..b.Z.V.7S7
    0450 - e0 be 30 7a 12 5f be c0-46 ca 93 17 83 74 52 bb   ..0z._..F....tR.
    0460 - 2a a0 f9 0f 56 00 45 38-d4 7b f1 9f e9 e9 a6 70   *...V.E8.{.....p
    0470 - 40 d5 5d 0c 26 a9 21 07-a4 66 f0 a0 78 af ea 93   @.].&.!..f..x...
    0480 - 67 71 88 93 42 0d 1f 76-16 e9 8d 0e e8 3a 1d 33   gq..B..v.....:.3
    0490 - b3 c4 89 ae a8 b1 c7 c3-e5 d3 56 f2 b9 ce fa 6f   ..........V....o
    04a0 - 53 3b 17 5d 1c 00 78 a0-0d eb 34 60 7d 8b 13 89   S;.]..x...4`}...
    04b0 - 9a f3 f0 ef b7 c2 f5 b1-ee 79 c9 9d cf b6 c1 c8   .........y......
    04c0 - 58 eb 27 6c 61 1f df a9-7d 9c fa 2f 4c 07 70 48   X.'la...}../L.pH
    04d0 - 48 c0 7f bd 5f 91 bf 95-ca 79 41 94 1c 08 51 3c   H..._....yA...Q<
    04e0 - b6 1e 40 95 b4 e3 1b 65-ca a7 5c 0b 5e e9 cf 43   ..@....e..\.^..C
    04f0 - 16 d5 a9 e8 6a 23 4d dd-8a c2 cb 8d 48 ac 85 0b   ....j#M.....H...
    0500 - 80 62 54 72 42 f4 c7 0d-0e 05 5a c3 5d 3a aa e7   .bTrB.....Z.]:..
    0510 - b6 d2 fe 1d 00 24 59 1a-b0 36 a4 56 fb cd 50 b0   .....$Y..6.V..P.
    0520 - 45 92 c8 84 f8 8f ac 1e-99 6b 83 cd 5c be 3a e7   E........k..\.:.
    0530 - 8d c9 ff 6d b9 12 6f 01-e5 78 03 3e 61 27 c7 1a   ...m..o..x.>a'..
    0540 - 50 6c fd 0e 42 f0 25 99-6e d3 5f da bd 06 7b 13   Pl..B.%.n._...{.
    0550 - 16 a8 11 87 31 f6 a7 b0-89 ec 76 ff 94 6b 79 98   ....1.....v..ky.
    0560 - be 70 13 97 72 f4 12 5c-e2 07 35 6c d3 41 a9 10   .p..r..\..5l.A..
    0570 - ea 77 9e 2a fe 94 e6 b6-d0 77 84 04 00 7f 51 11   .w.*.....w....Q.
    0580 - 42 ae 14 61 e9 6b 4e 40-b7 49 26 17 cc 4d d4 30   B..a.kN@.I&..M.0
    0590 - b4 89 5a 6d 5b 04 b7 c1-af 29 e8 46 28 24 2b 10   ..Zm[....).F($+.
    05a0 - 44 4d 47 c7 8b b8 91 49-c6 84 5d 3f e4 3b 47 34   DMG....I..]?.;G4
    05b0 - 65 79 00 d6 c7 12 9e 1d-8c 47 84 98 e1 e6 e0 f2   ey.......G......
    05c0 - 06 a7 ac c8 d5 af ae 83-70 55 32 b7 89 0b 92 aa   ........pU2.....
    05d0 - e9 86 e4 f8 9b 87 aa 13-7f af 76 f0 e1 1b b6 24   ..........v....$
    05e0 - cd e2 35 93 7c 4c 80 90-ff 7f 8f 5e 6d d9 30 14   ..5.|L.....^m.0.
    05f0 - 96 ab 6e 7f f1 95 62 ad-89 07 d0 63 30 df b9 54   ..n...b....c0..T
    0600 - f4 3d 9f 47 32 da 8e 40-05 e1 a7 99 c1 8e 8b 3a   .=.G2..@.......:
    0610 - 50 41 46 f7 12 d0 9c 12-73 1f cf 5f 99 16 8b 79   PAF.....s.._...y
    0620 - e1 e5 b9 a6 e1 9a aa 7a-78 cd fa 13 8b bb 7b 98   .......zx.....{.
    0630 - f1 83 83 18 0f 6b 2d bf-43 6e b2 ce 42 c0 b0 9d   .....k-.Cn..B...
    0640 - cd 2b 3c 46 99 a5 28 f1-d3 b6 2c 94 48 51 7d c4   .+<F..(...,.HQ}.
    0650 - 17 d5 12 b1 cd b8 6d 30-38 54 bf 42 10 1f 52 e5   ......m08T.B..R.
    0660 - ab a9 a3 85 3d fe 89 f6-e4 32 52 f7 0d 08 1e 8d   ....=....2R.....
    0670 - 3b df 58 4f 11 2c d1 e1-6b 5c c9 4a 48 e0 1d 2d   ;.XO.,..k\.JH..-
    0680 - d3 94 8e 8f d8 21 be 4e-9c 8e 56 ee 90 dc a8 9c   .....!.N..V.....
    0690 - 56 11 bc 25 53 1c ee 97-0b cf 74 0b 2d 30 f5 9b   V..%S.....t.-0..
    06a0 - fc 4c 69 50 0a d2 22 e1-2c 5c b7 0b d0 b3 dc 2c   .LiP..".,\.....,
    06b0 - 53 28 4f 17 0e d2 d5 26-3d 9e a1 39 11 77 11 ea   S(O....&=..9.w..
    06c0 - 9b 69 71 e0 3a 8f cf 7c-26 65 38 75 12 47 9b 8d   .iq.:..|&e8u.G..
    06d0 - 3a 52 c8 f2 29 7e 21 c9-93 22 9b e7 41 82 6e d7   :R..)~!.."..A.n.
    06e0 - a8 f7 9d b7 b9 9f b4 1d-31 7f 96 a3 d7 82 ce e4   ........1.......
    06f0 - c9 54 41 39 1a af 45 08-4f 7b d4 5f 56 08 c6 6e   .TA9..E.O{._V..n
    0700 - ae 99 d5 55 54 79 fa 51-98 24 a0 ed d3 ff 0f a3   ...UTy.Q.$......
    0710 - e0 ae 14 d5 23 48 1c b5-07 4c 99 27 7b 47 73 c9   ....#H...L.'{Gs.
    0720 - 4f 60 8c eb 0a 80 56 6c-94 52 56 5d f3 f1 1c 68   O`....Vl.RV]...h
    0730 - 67 1f 6e ab 40 d0 0c 1f-b3 f2 fc 32 9c f9 64 16   g.n.@......2..d.
    0740 - 38 fa 65 7d d5 f5 0d fc-c1 a7 03 d3 98 af 45 45   8.e}..........EE
    0750 - a1 03 d1 b7 ce 82 52 e2-eb 38 c3 a6 fd 7c 0b 6c   ......R..8...|.l
    0760 - 49 df 6b 3f d6 3b 0f 9c-9c f5 3f 9d 80 49 71 16   I.k?.;....?..Iq.
    0770 - ff 11 5b bf ed b4 fc 31-7f bf 2f 17 bf ec 37 83   ..[....1../...7.
    0780 - 9a 5b e0 73 80 c3 cc 6b-29 d7 33 7f aa c6 57 a7   .[.s...k).3...W.
    0790 - 8f c1 7b 1f a4 d2 fc b2-13 f6 9c 98 07 37 a9 70   ..{..........7.p
    07a0 - cb de 14 65 46 f7 50 72-a6 23 4f 35 9d 57 76 97   ...eF.Pr.#O5.Wv.
    07b0 - b1 ab f9 15 1b a6 83 a0-df 6b 24 07 72 32 e2 4b   .........k$.r2.K
    07c0 - 91 49 a2 90 82 b7 93 9d-e6 fc d1 44 08 ad d5 6c   .I.........D...l
    07d0 - 64 10 12 e8 4f 21 0b 28-8c 3e c6 04 4e 5e 27 7a   d...O!.(.>..N^'z
    07e0 - 13 b5 ba f5 2f a2 45 fd-25 a9 03 ae 7f cd 0d ee   ..../.E.%.......
    07f0 - 68 89 15 04 21 01 78 10-0d 60 eb 42 e9 d2 d9 fa   h...!.x..`.B....
    0800 - 9b 9f ce 52 f8 9a b5 be-db 7b 4d 1b 68 68 4f f5   ...R.....{M.hhO.
    0810 - f5 3f 35 a9 92 52 e8 20-fd 05 8c 9b 39 7e 54 ab   .?5..R. ....9~T.
    0820 - 20 cf 6a c6 03 ba 64 0d-42 d2 6b cd eb 7e 17 09    .j...d.B.k..~..
    0830 - 64 a4 5d 59 69 22 aa 05-bd 25 98 23 3b fd 29 50   d.]Yi"...%.#;.)P
    0840 - c0 fd 56 9a 46 51 14 3b-cf 30 1b 6e 18 5e 4d b3   ..V.FQ.;.0.n.^M.
    0850 - 02 43 95 5c fc 9d ad 21-79 aa 3e d7 47 0c 2c 07   .C.\...!y.>.G.,.
    0860 - 42 e8 6f 60 d4 48 a5 84-2d 44 32 43 a8 2c b2 a4   B.o`.H..-D2C.,..
    0870 - b9 1c 29 f6 e2 4f a3 d9-3e b2 01 55 36 a3 1b 9d   ..)..O..>..U6...
    0880 - 10 0b 38 f8 82 31 8f 6a-5b 80 c5 a0 b4 f2 ce e9   ..8..1.j[.......
    0890 - f1 7d 9f 81 ca af c8 db-0f 1a bc 5c 03 a1 19 2a   .}.........\...*
    08a0 - a9 b0 8e d4 e3 b8 5f dd-8d 8b a1 26 62 43 e6 6d   ......_....&bC.m
    08b0 - c2 4e 59 b9 ef 04 e5 f7-0e 14 dc 2b 0e 17 72 64   .NY........+..rd
    08c0 - c4 0f d3 54 71 a0 f2 f5-a5 83 1b a3 22 ab 92 b0   ...Tq......."...
    08d0 - 47 f1 0d 35 8a cb 92 28-c9 cc 2f d8 70 97 80 b7   G..5...(../.p...
    08e0 - ce 2d 97 59 0a 3a aa 66-ae cd 80 f6 98 af 49 31   .-.Y.:.f......I1
    08f0 - ac 7b ae 3c 71 0c b0 8c-b6 2a 12 f6 b4 72 70 93   .{.<q....*...rp.
    0900 - a1 5a 6a 15 2c 63 55 81-cc d9 09 0f 16 3a 96 f0   .Zj.,cU......:..
    0910 - 35 b0 1b 0e cd 11 f2 08-77 58 72 e4 41 f4 ae 26   5.......wXr.A..&
    0920 - 3e 52 3e 49 ef b0 c1 01-6f 3c 9d c5 8f f2 19 e9   >R>I....o<......
    0930 - 14 15 e2 9b 40 4d ba 35-8c de ae 5e 70 2e a9 98   ....@M.5...^p...
    0940 - b0 e3 2e ff 71 cd cb 2a-75 b5 21 06 3e 2c 18 7f   ....q..*u.!.>,..
    0950 - 8b 13 b5 ec 03 a3 68 c9-82 89 f2 ee fc 88 a9 f7   ......h.........
    0960 - a4 08 f2 38 22 15 3a 00-14 9f 05 ff 66 c1 05 d2   ...8".:.....f...
    0970 - bd 16 6f 5b 41 ae 7c 4b-50 44 7c c5 c7 e0 63 76   ..o[A.|KPD|...cv
    0980 - 02 0d e3 fc 85 38 23 fe-65 ce 9b 21 fc 5b 21 fe   .....8#.e..!.[!.
    0990 - 63 af 20 7d 66 68 d9 f6-3d d3 cd 9b 26 d1 bf 3c   c. }fh..=...&..<
    09a0 - a2 69 10 db 24 38 04 01-50 dc ca 26 99 f3 3b 86   .i..$8..P..&..;.
    09b0 - f3 06 fb b9 05 02 3a f5-c9 9d 9d 42 37 69 6d b3   ......:....B7im.
    09c0 - 23 8b 3b 3e b0 a3 53 3f-71 f0 c0 42 cf 9f 94 5f   #.;>..S?q..B..._
    09d0 - 43 76 8c 59 ae 9e ca 29-17 9e 41 a1 52 6d 1c c7   Cv.Y...)..A.Rm..
    09e0 - ef 68 44 59 b5 1d 90 7f-6e f4 16 dd 27 c8 28 81   .hDY....n...'.(.
    09f0 - e3 1d 5f 61 6c 5d 95 4e-4c 4a 33 ca 2c c5 b7 fd   .._al].NLJ3.,...
    0a00 - fd 8a 85 31 c9 de 3b 40-e1 22 5d 7d 8b a1 79 c6   ...1..;@."]}..y.
    0a10 - 0d 69 91 71 87 32 0c 24-66 fb 05 f6 b5 94 98 7c   .i.q.2.$f......|
    0a20 - f4 51 b9 d6 7e 86 94 6a-57 30 cf bb da 7f 4d c1   .Q..~..jW0....M.
    0a30 - 80 14 b3 12 42 ab 40 68-cd 69 a3 6a 20 d6 82 1f   ....B.@h.i.j ...
    0a40 - 11 1d b5 09 c7 e5 9f f1-34 f4 47 83 37 fd c8 f8   ........4.G.7...
    0a50 - a4 fc d0 0c e6 b5 b9 ac-32 82 f2 fb 60 85 69 34   ........2...`.i4
    0a60 - b7 3a 37 e4 95 93 9f b6-74 d0 c8 76 32 e3 e6 81   .:7.....t..v2...
    0a70 - e8 81 97 a0 52 ac 4d 3e-bc 49 8c 17 e3 ba 21 b3   ....R.M>.I....!.
    0a80 - 1a cc d3 12 b1 51 51 9e-be 52 3f 8a bf b4 a9 b4   .....QQ..R?.....
    0a90 - 5a 55 9b 98 91 fa ff 41-e7 8b ee a8 ca 13 97 61   ZU.....A.......a
    0aa0 - c3 36 a6 e8 73 4d 58 3f-e1 41 e1 32 5f ef 68 d5   .6..sMX?.A.2_.h.
    0ab0 - 01 d5 a5 2d ec 02 8d 81-76 63 a9 a0 6d 04 1b 82   ...-....vc..m...
    0ac0 - 12 0e df a9 12 f0 3c 97-be fb a9 92 e7 0d f4 dc   ......<.........
    0ad0 - 52 4b 51 63 03 29 1b 1a-93 36 85 15 0b a1 12 09   RKQc.)...6......
    0ae0 - ff 4d 63 b5 c0 b8 87 6a-1f 24 77 57 1c cf 7f fe   .Mc....j.$wW....
    0af0 - f4 95 f5 79 44 be c0 17-b7 f6 21 04 bc b7 94 b4   ...yD.....!.....
    0b00 - e8 1d f0 95 a9 f1 f4 e7-8f 71 5c 4e 4c 34 76 ec   .........q\NL4v.
    0b10 - 17 a4 28 3d 4f d6 f3 1c-55 f9 5c 71 9c ad f0 0d   ..(=O...U.\q....
    0b20 - 11 76 d7 47 5f c8 a6 e7-e5 96 a9 eb 79 a1 36 d2   .v.G_.......y.6.
    0b30 - 61 3d 06 81 0d e6 60 55-f0 24 ce 4c 31 98 76 fc   a=....`U.$.L1.v.
    0b40 - 37 38 e0 b3 0e be 05 e8-d4 83 3e 45 72 a0 b7 98   78........>Er...
    0b50 - 02 61 30 41 00 8d bc 2d-cc 1b f4 68 23 0b c4 17   .a0A...-...h#...
    0b60 - 02 dd 92 5f 54 03 7a 30-13 3e a6 40 44 1a b1 72   ..._T.z0.>.@D..r
    0b70 - 8c 52 27 5b ef 78 29 42-e7 14 11 1d 32 9c 07 8c   .R'[.x)B....2...
    0b80 - f6 ba 04 4f bd 3c 6b f2-49 97 33 1d 23 13 b0 a7   ...O.<k.I.3.#...
    0b90 - 80 f4 52 72 ba d3 d4 2d-72 69 b8 1b 16 1a 0f 02   ..Rr...-ri......
    0ba0 - 14 4a 0b 44 f8 76 db 50-f9 f8 1c c0 07 55 46 5b   .J.D.v.P.....UF[
    0bb0 - 19 2d ab 62 3c ed 26 44-32 6a f8 48 3e 0a 61 03   .-.b<.&D2j.H>.a.
    0bc0 - 11 94 ce 63 79 a4 b6 0e-53 4a e9 92 a1 55 8c 96   ...cy...SJ...U..
    0bd0 - 64 95 5e af 00 75 3b bc-37 35 db 70 5b 6c de 4b   d.^..u;.75.p[l.K
    0be0 - a2 3a a2 19 be 3c 06 23-90 ba 8a 79 a6 70 6d 93   .:...<.#...y.pm.
    0bf0 - ad 62 a6 b5 a8 31 3a b3-ab 0f 34 74 34 56 1b c2   .b...1:...4t4V..
    0c00 - a7 63 9d e8 61 db f1 ad-fa cb 85 c1 fa 4a a0 ac   .c..a........J..
    0c10 - d4 a3 d4 9f 53 ea 0b 87-f4 94 06 27 b2 f7 4e a8   ....S......'..N.
    0c20 - 1e 9a a6 17 e6 34 7a 5a-c0 91 4d fa 3b b9 e3 20   .....4zZ..M.;..
    0c30 - de fe d7 25 c2 58 35 64-45 6e 38 47 30 af d3 bd   ...%.X5dEn8G0...
    0c40 - 84 15 f2 a6 46 49 e2 a8-f4 8c 4d 73 2a 75 f4 bc   ....FI....Ms*u..
    0c50 - 24 49 54 c0 93 a4 f5 6e-32 f2 a5 84 35 06 10 ae   $IT....n2...5...
    0c60 - 4c 9d db c8 b1 1c c3 e6-c3 0a 2a 6e 67 01 03 38   L.........*ng..8
    0c70 - 4c 3b 21 7d 7e c3 4b 05-68 ea ca e1 bf 19 57 ec   L;!}~.K.h.....W.
    0c80 - 99 ea 0f 28 06 08 9f d0-c3 a5 b2 3a 4c 9d 62 dd   ...(.......:L.b.
    0c90 - 6b 46 fa e3 51 32 82 a9-dc dc 05 5c 37 57 53 d8   kF..Q2.....\7WS.
    0ca0 - 61 30 23 84 eb b7 43 dc-5e d0 de 8c a7 cb 8b ee   a0#...C.^.......
    0cb0 - fb b2 6d f7 45 ac 7b 2a-14 24 30 19 16 d6 e1 29   ..m.E.{*.$0....)
    0cc0 - ef bc 07 ec 6d a9 cf e5-6a 1b e7 6b 09 0c f4 60   ....m...j..k...`
    0cd0 - 06 f2 ea 02 07 8f 0c a7-52 0e 64 31 81 24 2a ed   ........R.d1.$*.
    0ce0 - 4d a2 8b 8e de b5 fd ee-f2 4d bd 29 63 ce ef 5b   M........M.)c..[
    0cf0 - 26 7a 48 c4 64 3e 73 e4-0b 7b 1a 72 90 2c f1 18   &zH.d>s..{.r.,..
    0d00 - b9 6c 11 a4 5c f8 12 47-1f 79 0a de ff 5a 05 f4   .l..\..G.y...Z..
    0d10 - b4 1f a0 4f bf 21 b1 5c-aa 2b 8b 85 1c 1c ea a8   ...O.!.\.+......
    0d20 - 59 45 4f 5e 1f 8a 8f 5e-6c 68 0c 64 9d 41 8a 90   YEO^...^lh.d.A..
    0d30 - 2f 80 0d 4b c8 16 0d 9c-e9 65 71 71 c9 91 9d c9   /..K.....eqq....
    0d40 - a6 3d 22 f8 d8 e8 ae 5d-08 e3 6b 0a e9 0a 4d 21   .="....]..k...M!
    0d50 - 3e 05 41 a3 07 65 2a 80-a7 ba e4 58 e8 99 79 d3   >.A..e*....X..y.
    0d60 - 04 b8 9e 51 e4 66 92 84-ea 2b 8f 6f 91 a0 34 d6   ...Q.f...+.o..4.
    0d70 - e7 4b 07 2b 56 b6 89 63-09 32 a9 eb 05 e2 39 06   .K.+V..c.2....9.
    0d80 - 30 e3 f1 60 c1 77 fc f5-ff e7 89 5c b9 9c 3d ab   0..`.w.....\..=.
    0d90 - a4 f1 ab e6 7d af bc 2c-a7 a5 28 18 79 78 7c fe   ....}..,..(.yx|.
    0da0 - bc 93 21 8d 11 67 b3 23-22 d5 1e 0a b9 19 a7 c3   ..!..g.#".......
    0db0 - ac cb 7a 87 d7 1a 9f 2f-94 96 f9 09 36 01 9f b4   ..z..../....6...
    0dc0 - b2 cb 9b 26 ba f6 56 ad-af c2 c2 24 f9 51 d4 2f   ...&..V....$.Q./
    0dd0 - 70 54 5a 90 1a a5 e5 f1-6b 05 37 da 17 bb 76 75   pTZ.....k.7...vu
    0de0 - a8 b5 3e 85 86 0d a7 75-a8 ff a1 fb ef bf 28 3b   ..>....u......(;
    0df0 - 51 47 97 89 6e 91 b5 fa-d0 f7 32 b9 2e 76 bc f2   QG..n.....2..v..
    0e00 - d7 f5 f8 9c 2c a9 f8 c2-07 66 9e 36 9f 0e 43 38   ....,....f.6..C8
    0e10 - 37 9e 54 08 19 f7 0b ea-49 ca c8 87 6b 9b b2 d7   7.T.....I...k...
    0e20 - 1f 12 6d 08 bd 64 78 9b-63 56 7d f8 15 88 c4 3e   ..m..dx.cV}....>
    0e30 - d6 d4 93 a2 ed a0 01 1f-db 99 00 b6 25 34 38 73   ............%48s
    0e40 - e5 40 50 e9 74 ec ff 9d-83 30 a2 f7 37 14 59 8c   .@P.t....0..7.Y.
    0e50 - 57 e0 be dc c0 27 9e f3-37 7e 89 f0 7f 25 1b e5   W....'..7~...%..
    0e60 - a5 07 99 17 51 4d 71 ea-eb e0 4a 62 f0 9d 8a db   ....QMq...Jb....
    0e70 - ca 7e 78 7c 02 23 73 56-07 8c ca e0 31 d8 7d 76   .~x|.#sV....1.}v
    0e80 - fd fd be e4 dc 83 58 4b-59 ec 98 26 c8 43 d7 18   ......XKY..&.C..
    0e90 - cd dd 2f 90 4e 1e 02 e2-45 e7 21 6a d0 d7 90 3f   ../.N...E.!j...?
    0ea0 - 40 3f e7 33 26 a0 fd 80-ba fb 30 37 89 57 28 64   @?.3&.....07.W(d
    0eb0 - 97 1c 5e f3 f1 a2 f0 20-0b 50 45 04 8e 76 8d 56   ..^.... .PE..v.V
    0ec0 - 7e 4e a0 b2 99 27 9f ca-ff 8f b6 6f 34 de f8 99   ~N...'.....o4...
    0ed0 - 8a be ad a1 42 3e 5e 39-79 81 54 e5 10 80 b0 8b   ....B>^9y.T.....
    0ee0 - 3c 0b ab f5 1b 35 3c f8-f5 a0 ba d6 0e 49 02 3d   <....5<......I.=
    0ef0 - 05 7d f8 e7 e9 18 35 a1-50 a9 3b 6c 50 cf 86 50   .}....5.P.;lP..P
    0f00 - 19 df 9b 94 72 54 05 d8-e9 0c 44 c5 55 f0 02 b1   ....rT....D.U...
    0f10 - 26 e2 34 fe 77 08 53 8d-85 11 61 5b cf 84 b3 f4   &.4.w.S...a[....
    0f20 - 47 d6 01 db 2d aa bd 95-37 7f 00 b1 0d c6 ca 91   G...-...7.......
    0f30 - 11 e6 d4 44 f3 2d 9e 23-53 1f f9 5b 5a 2f 14 e6   ...D.-.#S..[Z/..
    0f40 - 13 82 ab 49 43 f4 ce c6-5d 03 9d ae 63 18 a5 90   ...IC...]...c...
    0f50 - 1e 3d 29 b7 bb fe a8 98-b7 0b 61 4e bf d7 b3 0a   .=).......aN....
    0f60 - a3 85 77 db 84 c6 54 33-22 77 74 21 8c a4 6c db   ..w...T3"wt!..l.
    0f70 - e6 90 f0 24 20 c7 15 aa-3a 32 0d 74 d9 4c be a5   ...$ ...:2.t.L..
    0f80 - 36 c0 27 2e b1 09 8a 86-64 d3 5e aa bc 29 bb 8e   6.'.....d.^..)..
    0f90 - 38 22 aa 78 ab c7 88 3b-2b 04 e8 14 62 fe 68 4c   8".x...;+...b.hL
    0fa0 - 8d e4 d2 53 72 f9 56 09-f1 37 73 5f 6b db bb a3   ...Sr.V..7s_k...
    0fb0 - eb 96 ba b8 1c f0 6d e2-4b 5e 81 8a 96 84 e1 8f   ......m.K^......
    0fc0 - 31 87 b0 c2 50 67 a6 8e-2a a7 51 d6 2d 07 de fd   1...Pg..*.Q.-...
    0fd0 - 45 db 1b f9 c7 16 c9 a2-e1 97 92 99 b4 f7 e4 8c   E...............
    0fe0 - b5 38 9c c6 45 3a 58 5c-ff da 42 53 41 7a cb 29   .8..E:X\..BSAz.)
    0ff0 - be 87 c1 a7 31 c2 23 a1-a8 93 78 e3 62 b0 cc fa   ....1.#...x.b...
    1000 - f7 ee 47 b4 ed 67 2f da-04 79 2f b8 e9 86 2a fe   ..G..g/..y/...*.
    1010 - 8c bc 83 1d 6f 67 5a 09-a8 16 bd 5e c6 76 26 27   ....ogZ....^.v&'
    1020 - 4f 96 b1 7d 48 9d a2 9b-c5 ad 15 85 bb a6 31 e7   O..}H.........1.
    1030 - c0 24 35 35 62 b0 79 45-49 60 5d 34 2c 37 a3 50   .$55b.yEI`]4,7.P
    1040 - cf 5b 91 f0 6c ff f9 a3-de 3e 49 9c ab 65 e5 60   .[..l....>I..e.`
    1050 - 72 3d f6 2f d5 aa e3 f4-c2 3c c5 6a 4b 55 6c 36   r=./.....<.jKUl6
    1060 - e0 aa b3 be 92 df 56 0a-c0 f5 97 97 e3 eb 65 08   ......V.......e.
    1070 - 98 77 90 de 98 6c 3f 57-4b fa d7 f7 24 78 40 92   .w...l?WK...$x@.
    1080 - 07 85 f5 2a 77 81 c1 a8-3c 5b b2 9a 62 10 14 f0   ...*w...<[..b...
    1090 - ae 54 0c 35 e3 4c 0b 6a-57 3e b9 76 0b e1 d1 b8   .T.5.L.jW>.v....
    10a0 - cf 56 3a 97 36 c4 4a 09-8c e3 8b 20 ab 90 07 cd   .V:.6.J.... ....
    10b0 - 20 93 46 bf 4a fe 56 77-42 2a b8 c1 32 ab 7f ae    .F.J.VwB*..2...
    10c0 - 90 0a 75 6b 5a ab 27 9f-6c e1 59 08 db 60 8a 8b   ..ukZ.'.l.Y..`..
    10d0 - ff 6e 80 fb 3e 78 0f 3d-77 22 bd 76 60 66 bf aa   .n..>x.=w".v`f..
    10e0 - 8d 8a a5 2e a5 91 28 16-94 12 57 89 36 5e 5b 45   ......(...W.6^[E
    10f0 - 07 e3 76 bd 81 9f 7a 4f-78 b8 80 9e b6 6c 32 f7   ..v...zOx....l2.
    1100 - bc 56 aa f1 a6 fd a7 8e-45 c5 1e de 58 51 72 67   .V......E...XQrg
    1110 - ba 8b ab 46 a3 a8 0f c7-52 43 e5 26 7a d5 0b d6   ...F....RC.&z...
    1120 - ed 16 3c 0a 0d 2c a8 76-fd 8a 80 90 a3 e8 ff 2b   ..<..,.v.......+
    1130 - 5f 5c 7b 1c 73 0b 04 b7-b0 cd b0 f6 e8 20 c8 fe   _\{.s........ ..
    1140 - 1e 45 ca f9 2a                                    .E..*

    Start Time: 1754365792
    Timeout   : 7200 (sec)

```

```
[srv_etqsml@ETQSMLUATAPP001 cdh]$ openssl s_client -connect apponboarding-gold.etiqa.com.my:11000 \
  -cert client_cert.pem \
>   -cert client_cert.pem \
>   -key private_key.pem \
>   -CAfile ca_certs.pem \
>   -servername apponboarding-gold.etiqa.com.my \
>   -crlf \
>   -ign_eof << EOF
> GET /unity-party-retrieval-svc/status/health HTTP/1.1
> Host: apponboarding-gold.etiqa.com.my:11000
x-app-id: ETIQAPLUS
> Content-Type: application/json
> x-app-id: ETIQAPLUS
> x-country-code: MYS
> x-api-version: 1
> Accept-Language: en
> Connection: close
>
>
> EOF
CONNECTED(00000003)
depth=1 CN = Maybank Group Internal CA V2
verify return:1
depth=0 C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my
verify return:1
---
Certificate chain
 0 s:C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my
   i:CN = Maybank Group Internal CA V2
 1 s:CN = Maybank Group Internal CA V2
   i:CN = Maybank Group Internal CA V2
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIE8DCCA9igAwIBAgITIwAAEcvBmJepy5vzqAAAAAARyzANBgkqhkiG9w0BAQsF
ADAnMSUwIwYDVQQDExxNYXliYW5rIEdyb3VwIEludGVybmFsIENBIFYyMCAXDTI1
MDYwNDA4MjUyN1oYDzIwNzAwMzA2MDMxODIyWjCBmzELMAkGA1UEBhMCTVkxHDAa
BgNVBAgTE1dpbGF5YWggUGVyc2VrdXR1YW4xFTATBgNVBAcTDEt1YWxhIEx1bXB1
cjEfMB0GA1UEChMWTWFsYXlhbiBCYW5raW5nIEJlcmhhZDEMMAoGA1UECxMDTVNT
MSgwJgYDVQQDEx9hcHBvbmJvYXJkaW5nLWdvbGQuZXRpcWEuY29tLm15MIIBIjAN
BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAoI4vNH2rC3yxjLVEm2nUsoqVPkXY
WRHI5K88gfQK6G8aAwYpQeoBp3KpC5zYQD0gupmxzJV6NkhbmAFDRgOIwlH+PsQf
YV06K5uPZ4vvxBxETb4mKVX2kFx1Bb20cne/CmwXwEheItzopS9U0gh+d9Jk8xOq
3BHI4DdVWAOZKiItFp+cvy7oGCzln4h0yDWTp3+9OWaUVzpoWmoq4fDOcy+qdpY9
h5o8bAT+qaq/81fS4omo6iAAU5mZw9q22kedr5ordROKsmx06cIpr5FG86kN+XYo
6wDNAZHeGJGtdv7QR/mEJfYQIna09ykvOaM8+aJAagLa2dCSrPZQKPFTJwIDAQAB
o4IBnDCCAZgwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMAsGA1UdDwQE
AwIEsDAdBgNVHQ4EFgQU/1h24JMxkdlaZItDO0ywJQS8qLAwTwYDVR0RBEgwRoIf
YXBwb25ib2FyZGluZy1nb2xkLmV0aXFhLmNvbS5teYIjd3d3LmFwcG9uYm9hcmRp
bmctZ29sZC5ldGlxYS5jb20ubXkwHwYDVR0jBBgwFoAUR0sClxmYfv4cfUKAcy0l
t3NDBwUwWQYDVR0fBFIwUDBOoEygSoZIZmlsZTovLy8vTUJCQ0FQUkQwMDEvQ2Vy
dEVucm9sbC9NYXliYW5rJTIwR3JvdXAlMjBJbnRlcm5hbCUyMENBJTIwVjIuY3Js
MHAGCCsGAQUFBwEBBGQwYjBgBggrBgEFBQcwAoZUZmlsZTovLy8vTUJCQ0FQUkQw
MDEvQ2VydEVucm9sbC9NQkJDQVBSRDAwMV9NYXliYW5rJTIwR3JvdXAlMjBJbnRl
cm5hbCUyMENBJTIwVjIuY3J0MAwGA1UdEwEB/wQCMAAwDQYJKoZIhvcNAQELBQAD
ggEBAD1p4fLCgJaBHlTa7ofR45gC07XAua3iJAWyZjL1zNDnR00eGpLKxQcjDgqe
aGO/PF8/ic9Gs0D6prIknzS7SHGpn3uaE23sUF4z7fyXBEItfCwkXwQRvnrXjAUM
DxNif9QtWOt0UF5oNRH3gctOA/nc8q+OlTJ2ZPOq1LqGufAOP4Uo7LbHhUtVqgAS
efnbQaTfxxmUfl9qUPEMEi5OBMQnRXInannElasSyl7vFrBFn7SOaB9rkEdXHauV
zcXFfyBYDhn1rwOC00grHReDmAp3QU868jgAZ1qiiiWfNyPxzHjdp3uAQVLL3DdB
Yt9wY96Q2LNq7erQyc1th4Mp2pE=
-----END CERTIFICATE-----
subject=C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my

issuer=CN = Maybank Group Internal CA V2

---
Acceptable client certificate CA names
C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apppartner-gold.etiqa.com.my
C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = apponboarding-gold.etiqa.com.my
C = MY, ST = Wilayah Persekutuan, L = Kuala Lumpur, O = Malayan Banking Berhad, OU = MSS, CN = appetqplus-gold.etiqa.com.my
Requested Signature Algorithms: ECDSA+SHA256:ECDSA+SHA384:ECDSA+SHA512:Ed25519:Ed448:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA+SHA256:RSA+SHA384:RSA+SHA512
Shared Requested Signature Algorithms: ECDSA+SHA256:ECDSA+SHA384:ECDSA+SHA512:Ed25519:Ed448:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA-PSS+SHA256:RSA-PSS+SHA384:RSA-PSS+SHA512:RSA+SHA256:RSA+SHA384:RSA+SHA512
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 3159 bytes and written 2781 bytes
Verification: OK
---
New, TLSv1.3, Cipher is TLS_AES_128_GCM_SHA256
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_128_GCM_SHA256
    Session-ID: C071D2808653D75D41D7F699A56F2A089D7B15DC98ECA90C7DB97DC22C07E09D
    Session-ID-ctx:
    Resumption PSK: ED6969FC336365E9A049568F3677379E86EB2AA435602B0330705DE5F4C7031F
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 86400 (seconds)
    TLS session ticket:
    0000 - bc d4 e4 6b 2a 7e b4 05-3b 4d 8f 29 01 f0 30 82   ...k*~..;M.)..0.
    0010 - db ce 52 f9 23 b9 de 2a-1a 9b 25 d0 1d b1 92 a4   ..R.#..*..%.....
    0020 - e9 91 67 77 70 5e c8 11-87 b3 fc 16 98 f0 48 c3   ..gwp^........H.
    0030 - 86 25 44 b0 54 38 70 02-a0 42 60 40 04 42 27 70   .%D.T8p..B`@.B'p
    0040 - ff 56 4a 2c 23 fb de 50-0a f5 02 bb 18 be c8 bc   .VJ,#..P........
    0050 - ba 7f 13 ff d3 6f 3f f8-e4 60 f2 c7 31 5f 09 eb   .....o?..`..1_..
    0060 - bb cd 08 44 87 5e aa cb-fe fe 4e fe 30 b2 43 50   ...D.^....N.0.CP
    0070 - f7 78 2f 29 df 4f 2c ba-f9 e2 a3 5c 39 96 37 ef   .x/).O,....\9.7.
    0080 - c4 84 05 40 94 03 4b 95-77 36 77 d1 3b da 60 f8   ...@..K.w6w.;.`.
    0090 - 49 e9 ca 3d 3d 60 f3 c6-4c e8 8c d9 e0 9b da fa   I..==`..L.......
    00a0 - 02 72 8b e5 d4 33 39 b8-7f 5d d7 ed 1b 2d 52 5b   .r...39..]...-R[
    00b0 - b0 81 4a 25 61 32 d2 b0-85 78 94 ab 3f b8 38 61   ..J%a2...x..?.8a
    00c0 - 77 3f 81 af e3 7a e4 46-4a 44 d7 64 17 87 5b c3   w?...z.FJD.d..[.
    00d0 - 87 b7 59 95 61 45 9f 81-37 2e d3 ea 3f 80 9e 1d   ..Y.aE..7...?...
    00e0 - 05 e9 46 f0 b5 13 4b 52-1f b5 a5 c5 dc 08 cf b4   ..F...KR........
    00f0 - d7 6b b0 aa 8b bd 74 56-b0 32 73 c7 ae b3 93 84   .k....tV.2s.....
    0100 - 39 a0 52 b7 1b 96 54 49-6f e2 c6 90 6a f3 aa e1   9.R...TIo...j...
    0110 - f0 65 0a ba 20 c0 e0 c7-36 40 b3 8a 50 90 40 39   .e.. ...6@..P.@9
    0120 - 7e e0 32 34 5f a0 7b e9-80 8f be 71 04 50 68 7b   ~.24_.{....q.Ph{
    0130 - 7f 37 c7 da d6 0f d1 1f-25 39 a9 9b 18 1b 10 df   .7......%9......
    0140 - 79 2e f6 5b 74 77 24 ad-72 9f 31 48 35 27 89 94   y..[tw$.r.1H5'..
    0150 - 45 db 63 a3 80 8c f5 96-5e 2c 08 ba 84 83 df 6b   E.c.....^,.....k
    0160 - aa 83 a4 08 7c 01 00 35-45 0d 80 c8 26 24 a9 90   ....|..5E...&$..
    0170 - 59 fe 30 df c6 26 bd 4d-e8 ee 35 42 0a ca ae 7b   Y.0..&.M..5B...{
    0180 - 7a 62 9d 86 c9 7f 7d 01-9f a0 ab 3f 85 0e 0b a7   zb....}....?....
    0190 - 6e ad c9 48 83 47 9d bc-f1 6a e0 64 cf a8 d4 f5   n..H.G...j.d....
    01a0 - f3 e2 66 7e dc e3 a6 be-64 c6 0c 03 e6 2e db 46   ..f~....d......F
    01b0 - ca ae 54 d7 7a bb 53 0b-d1 93 bd a6 64 78 6e 65   ..T.z.S.....dxne
    01c0 - 00 75 05 52 82 61 74 f4-8d 65 f2 de 1c 83 df cd   .u.R.at..e......
    01d0 - 68 15 25 a6 f9 bc 01 19-88 3e 59 6c ed be d0 eb   h.%......>Yl....
    01e0 - 22 91 a2 81 a2 87 01 79-89 32 ec 01 11 22 72 a6   "......y.2..."r.
    01f0 - c2 d9 4c 00 d3 f8 05 1a-01 73 83 20 58 fa f9 55   ..L......s. X..U
    0200 - 5e 20 2a 35 b7 b0 3d a9-29 a6 fc 92 a3 ba b7 e1   ^ *5..=.).......
    0210 - 71 5d cc 92 a3 6b c7 af-77 15 92 43 9c 84 ee d7   q]...k..w..C....
    0220 - b4 2c fd bf d2 9f 35 8e-e7 5f 21 33 0b 99 d4 5f   .,....5.._!3..._
    0230 - 30 c8 41 fb 3a 73 f5 20-78 30 8f 55 2d 65 82 5f   0.A.:s. x0.U-e._
    0240 - 37 14 e6 3c 45 d8 af ab-0b 06 56 f4 e9 a2 b6 1f   7..<E.....V.....
    0250 - d3 f8 60 2e 18 c3 e4 65-05 67 00 84 17 bf 6b 27   ..`....e.g....k'
    0260 - 63 21 d2 ec 8a 7b 0d 30-e6 44 9e 0a 3c 2b 00 d3   c!...{.0.D..<+..
    0270 - c7 0a 12 0c bd 94 c2 14-98 cb b3 e9 26 bc 2d a1   ............&.-.
    0280 - 46 a1 7a a1 35 c7 8b 0e-48 7a 36 1e 1c ae 19 ca   F.z.5...Hz6.....
    0290 - 98 2d 29 a0 ef 9d 7c 15-b5 17 ba 7c 5c 27 05 da   .-)...|....|\'..
    02a0 - cf 41 4a 70 5b e9 6f a8-5d 6e db ed 38 36 e7 e0   .AJp[.o.]n..86..
    02b0 - 9a 7b 80 c6 81 ad ac 90-79 47 6f f1 41 06 d4 8d   .{......yGo.A...
    02c0 - a1 b3 cf 58 40 2c c0 2e-3e e5 39 73 ea 10 47 65   ...X@,..>.9s..Ge
    02d0 - ad 05 bc 2a b2 cc 7f 12-e9 8c 73 93 c3 7d 71 2f   ...*......s..}q/
    02e0 - 8d 82 9b e5 0b c6 5b bc-9b 21 e5 97 b4 15 4a a7   ......[..!....J.
    02f0 - 18 5d 07 db e1 cb 55 3b-db 6a 38 ee 4d 75 16 05   .]....U;.j8.Mu..
    0300 - ba 39 c8 d0 a6 f8 22 12-0f de d2 cf db 82 34 23   .9....".......4#
    0310 - aa ca bb 49 85 46 ab b0-c3 ea 0c 12 67 8a 64 fc   ...I.F......g.d.
    0320 - d9 85 ca 37 c1 f9 48 94-b8 10 a5 51 7d d0 44 8c   ...7..H....Q}.D.
    0330 - 5f 31 69 18 41 da 1c fa-0f 3e af f3 65 1f bf a6   _1i.A....>..e...
    0340 - 9f 7d d1 27 6a 5a 22 e6-d2 50 55 8c 3f 27 21 01   .}.'jZ"..PU.?'!.
    0350 - 36 14 8f cf 8c b2 c1 b7-6e 77 f8 a3 70 94 9c 24   6.......nw..p..$
    0360 - a2 e8 fd 22 f4 40 0f 33-c6 d1 8d 36 20 57 28 43   ...".@.3...6 W(C
    0370 - 82 60 a0 73 a3 dc 77 ad-e5 a2 2a 18 9a 45 0c 39   .`.s..w...*..E.9
    0380 - a3 47 7b 52 5d c3 53 f1-c0 e0 a5 26 d7 97 eb d6   .G{R].S....&....
    0390 - e2 6a 97 fd 1e a7 64 1b-07 de ac 1c e0 56 f3 00   .j....d......V..
    03a0 - b0 9c 0d a1 21 b9 9c c5-3c 28 eb 01 c9 ea 9f 96   ....!...<(......
    03b0 - fd 01 6e cd 7a bc 7a f2-c5 bd c3 e9 2d e6 29 8f   ..n.z.z.....-.).
    03c0 - 0e c3 ea b6 0c e4 9b 85-83 c0 03 79 9d 6d c2 97   ...........y.m..
    03d0 - 3b f3 2e 00 4f f7 79 1e-d8 a7 04 49 c9 3c 93 c8   ;...O.y....I.<..
    03e0 - 04 dd 3b 94 a4 61 e0 08-d7 80 88 fa e5 d5 59 88   ..;..a........Y.
    03f0 - e3 de c6 7c 30 99 29 5e-a7 81 85 a1 2e 99 88 2a   ...|0.)^.......*
    0400 - df 8c 24 40 47 4b 4b 14-bb ad b6 eb e6 31 14 90   ..$@GKK......1..
    0410 - 8d dd 51 56 11 70 30 ca-29 d5 08 38 ad 0e ca 7d   ..QV.p0.)..8...}
    0420 - 76 67 7d 6c 67 0d 80 31-96 1b e1 85 05 33 97 cc   vg}lg..1.....3..
    0430 - 79 c8 71 00 96 24 bd e6-e0 a7 6e 69 bb 72 fb 41   y.q..$....ni.r.A
    0440 - eb e4 f1 b1 4f fa df 3e-af 40 54 27 8a 7d 5f 5a   ....O..>.@T'.}_Z
    0450 - 5c c2 c2 6b c1 5a 59 c8-cb 91 a1 81 d0 40 a3 49   \..k.ZY......@.I
    0460 - 66 0a 30 31 88 ec 0d ee-06 bd b4 13 90 eb da 83   f.01............
    0470 - a7 18 92 da 93 8f 24 d6-09 95 65 f3 42 d1 56 b3   ......$...e.B.V.
    0480 - 02 f9 c3 df 26 59 88 43-31 65 d2 07 8d b1 3e 71   ....&Y.C1e....>q
    0490 - 00 8b 04 f6 8d ee ca bd-0c 50 79 de 8d 77 36 4d   .........Py..w6M
    04a0 - 99 d4 19 eb a8 f5 32 de-4d 18 30 f0 d8 af 43 59   ......2.M.0...CY
    04b0 - 9d 8e a0 cd 50 4d 09 a4-a6 1c b7 59 78 41 f8 af   ....PM.....YxA..
    04c0 - 13 45 72 b5 0e 85 60 79-ef d8 5a 9d ba e5 09 24   .Er...`y..Z....$
    04d0 - 97 e4 c8 89 8b 69 5c 36-6e 36 00 8c bf 33 ba 20   .....i\6n6...3.
    04e0 - 91 f3 7a 91 04 4b 14 ba-af 5a 8d f8 5a aa 0e 04   ..z..K...Z..Z...
    04f0 - d4 25 94 c0 3d c7 1e 27-a7 d8 bd fd a7 0f 7d f7   .%..=..'......}.
    0500 - 84 87 a8 7b b2 76 78 36-cb eb 8f a1 1b d6 02 07   ...{.vx6........
    0510 - 3e ec e2 48 e7 5e 46 ad-a3 3c f5 db 20 6c a0 4f   >..H.^F..<.. l.O
    0520 - 37 ff 79 63 01 94 71 70-46 c3 05 dc 21 42 ee af   7.yc..qpF...!B..
    0530 - b5 43 8b b8 6f 30 b1 9d-a7 1e c4 40 1a 60 10 3d   .C..o0.....@.`.=
    0540 - 93 cc 68 e9 56 78 e4 27-65 6b 86 ff fc 90 a7 6b   ..h.Vx.'ek.....k
    0550 - 29 1e 47 d6 8d 10 36 58-a2 ae f5 96 75 bc 0e 45   ).G...6X....u..E
    0560 - b6 58 b4 87 e5 c0 35 dd-36 ec eb 26 78 a8 68 0d   .X....5.6..&x.h.
    0570 - d3 2b e8 e5 55 cf a3 53-81 3d 28 9e 2a 41 a0 14   .+..U..S.=(.*A..
    0580 - c1 72 06 7a 2b 5d fc 96-56 bd d6 e1 db a6 ed 34   .r.z+]..V......4
    0590 - ff fb 88 0b f2 e3 d9 46-c4 ec 6f 32 2f e2 6d 8a   .......F..o2/.m.
    05a0 - b9 de b6 a0 78 20 6b 15-0d 59 cf ce da 3a 1a de   ....x k..Y...:..
    05b0 - b9 fc 84 28 e2 ab 51 f8-d2 55 60 18 17 7a c7 da   ...(..Q..U`..z..
    05c0 - 02 1f 40 81 27 2e 99 f7-4a 8c ea 58 d2 75 58 06   ..@.'...J..X.uX.
    05d0 - 02 86 8d 5e 36 1a 47 a0-7e cb 64 8a 30 b2 03 22   ...^6.G.~.d.0.."
    05e0 - 7e 7e 74 16 50 17 5c 4b-e7 8f 21 c7 37 6c 28 6e   ~~t.P.\K..!.7l(n
    05f0 - 21 30 58 e8 29 1d 2f c5-66 ca 26 14 a8 09 6b a7   !0X.)./.f.&...k.
    0600 - 08 3a fb b2 0d 18 b9 f5-a7 97 b8 61 19 1d a6 44   .:.........a...D
    0610 - 9a 67 34 e3 6d 11 f1 23-9f e0 c2 8b 89 74 e7 0b   .g4.m..#.....t..
    0620 - cb 07 96 d2 b7 fe 8d b1-4c 6d 6d 0c 5a aa a3 87   ........Lmm.Z...
    0630 - d9 1c 03 33 cf ff 14 02-34 9d c7 4e 03 45 f9 3c   ...3....4..N.E.<
    0640 - 48 f1 66 71 43 a1 70 00-ad d2 2f 5d ee 10 35 b4   H.fqC.p.../]..5.
    0650 - a8 a2 ee 5c 37 1e 2c f1-23 c2 39 fe fa a6 71 43   ...\7.,.#.9...qC
    0660 - 4b b0 f9 4c 2b dd 8b 50-72 77 ee 94 1b 21 33 bb   K..L+..Prw...!3.
    0670 - cb 2a 23 31 eb 4e bd 5f-ac e8 55 54 95 6f 0b aa   .*#1.N._..UT.o..
    0680 - 09 32 8a f1 b7 39 d8 59-20 d8 ae 59 27 7a 6d c2   .2...9.Y ..Y'zm.
    0690 - 94 8d 1b bc 95 01 b9 00-31 ba 66 ed f2 75 f2 ab   ........1.f..u..
    06a0 - bf 5a 70 e2 92 87 4c 42-19 9a d8 3e 04 44 d2 5f   .Zp...LB...>.D._
    06b0 - 45 ea ef 4a a0 7d a5 a3-78 da ca 56 bf 77 63 2d   E..J.}..x..V.wc-
    06c0 - 48 5d b9 b5 3d fd 1e 51-78 14 c9 37 b8 ad 5a 99   H]..=..Qx..7..Z.
    06d0 - 6f 21 28 52 f8 55 6f ae-1c 47 73 65 a5 ae 0b f9   o!(R.Uo..Gse....
    06e0 - e4 2c 8c d7 17 3d 0e 5a-52 ed 34 7c 6b 8b dd 01   .,...=.ZR.4|k...
    06f0 - 89 6d 4b 51 d1 b3 11 4c-98 e3 28 35 2f d3 85 b1   .mKQ...L..(5/...
    0700 - e3 c6 14 e9 ee 6a 11 8e-50 2b 02 9e 8d dc d5 18   .....j..P+......
    0710 - 7f 5f b1 2c 91 bc 4a b2-74 54 d6 d8 db 71 94 d6   ._.,..J.tT...q..
    0720 - 31 4e 2d 63 90 e7 59 40-9d e4 e6 45 03 27 01 04   1N-c..Y@...E.'..
    0730 - ef e5 53 83 37 56 36 a9-4e a8 dc 2b 8b 80 93 a4   ..S.7V6.N..+....
    0740 - 61 3a 26 a6 37 b5 3b f3-02 e7 96 0b a2 38 1f f7   a:&.7.;......8..
    0750 - 1b e9 fc 5b 5b a1 f4 fe-e4 36 d5 d7 8e 75 80 5c   ...[[....6...u.\
    0760 - 19 64 b5 c1 31 f1 02 e9-27 b1 4d 9e ca 36 fb 65   .d..1...'.M..6.e
    0770 - 7b c5 47 3c 1e 7b 74 69-e4 0c 90 43 84 d3 c5 15   {.G<.{ti...C....
    0780 - b4 66 78 77 86 1b 8d c7-4b c8 cf 27 e1 b4 2f 25   .fxw....K..'../%
    0790 - cb b5 5a 6d a6 dd 84 ad-7b 99 fd ad 68 28 59 04   ..Zm....{...h(Y.
    07a0 - dd 8c 11 40 0f f0 46 17-ea ae 41 0f b3 cb 12 41   ...@..F...A....A
    07b0 - 46 07 6a 4e 12 7c 77 91-e9 19 9c 4d 5a b0 7d 9d   F.jN.|w....MZ.}.
    07c0 - a1 2e 6d 4f b1 fb 71 70-c7 b5 0a 72 07 71 c2 bc   ..mO..qp...r.q..
    07d0 - 9f 57 c0 d4 da 62 3c 27-62 d1 6c 99 1d 2d 69 d6   .W...b<'b.l..-i.
    07e0 - da 63 42 8e b9 49 40 6b-a2 3f fc 3b df 70 a0 99   .cB..I@k.?.;.p..
    07f0 - 41 e2 d1 11 de a6 1d fe-3e dc 13 ef 92 3e dc 1a   A.......>....>..
    0800 - e0 b9 f5 7c 08 49 e4 a3-d1 05 fd 12 ed 57 dc 51   ...|.I.......W.Q
    0810 - f5 b3 0a 40 35 b9 89 76-88 72 21 65 ee dd 18 42   ...@5..v.r!e...B
    0820 - 4d 3a 44 00 66 0c f6 02-12 8d 7b 71 99 ea d3 23   M:D.f.....{q...#
    0830 - 11 c9 8e f8 c8 a6 a7 f8-a9 27 42 79 aa 99 6c 31   .........'By..l1
    0840 - 49 dc dc 7e 8a 76 2f 95-91 c3 08 f8 3a a7 d6 65   I..~.v/.....:..e
    0850 - 16 f0 92 56 78 3b 17 4b-5f 2c 27 d0 37 f3 9d e4   ...Vx;.K_,'.7...
    0860 - 56 01 f9 08 d3 a6 a2 8c-fe d8 04 86 45 66 63 01   V...........Efc.
    0870 - 53 8f 4e c8 3b 24 0d 30-e1 1a 95 92 72 de 90 74   S.N.;$.0....r..t
    0880 - 15 30 f9 98 e8 5b d3 d5-80 bf 82 75 8f b3 19 fa   .0...[.....u....
    0890 - 02 6b 16 78 4f 7b 08 60-d4 84 d2 74 4f a5 e9 0e   .k.xO{.`...tO...
    08a0 - 4d 41 e9 4e 97 1a cd f6-1d a6 33 64 5a 94 24 2d   MA.N......3dZ.$-
    08b0 - 59 53 23 3a 66 df 96 ce-38 5b 2d 4e 2e 29 65 c5   YS#:f...8[-N.)e.
    08c0 - 71 64 79 0a 44 b6 de d6-6d 00 7c cb 58 0f 9d 22   qdy.D...m.|.X.."
    08d0 - d6 23 37 4b 89 62 f0 87-80 05 d7 10 cc bf 0b b7   .#7K.b..........
    08e0 - 99 f4 1a b3 f1 f1 a7 1e-e3 75 79 0a 68 79 c2 e1   .........uy.hy..
    08f0 - 51 c4 a8 49 4d 21 42 d8-eb 89 0a c8 a1 6e 59 01   Q..IM!B......nY.
    0900 - 0b 62 68 d1 53 87 72 2d-49 ee fb 10 18 21 cd c9   .bh.S.r-I....!..
    0910 - 4e 91 07 ed ba e5 68 4b-c2 72 a7 42 16 ba 96 7f   N.....hK.r.B....
    0920 - 9b 4a 74 21 ff 4e de 33-31 e3 38 5e 21 a5 0d fd   .Jt!.N.31.8^!...
    0930 - d6 eb db 54 e3 ca ea a7-90 fe 53 ed 74 9a 50 6d   ...T......S.t.Pm
    0940 - d8 95 83 bc a3 d8 56 87-78 97 a2 e9 c5 3c 5e 6d   ......V.x....<^m
    0950 - 87 79 93 8b fb a4 f7 ad-c4 f7 31 4c 6c 92 1f d1   .y........1Ll...
    0960 - 08 75 cf 0f 20 42 ea a6-d8 d1 b7 07 99 a3 7d ab   .u.. B........}.
    0970 - d7 4c 7a 26 1b 27 4e cc-ea 5d c0 80 cc 3a 1e 05   .Lz&.'N..]...:..
    0980 - b1 e0 02 a8 3c e6 1a be-50 21 e3 a8 51 0b 2d 1e   ....<...P!..Q.-.
    0990 - 71 b2 9c 2b 87 f1 5a 21-fc 31 2a fd 92 69 c0 49   q..+..Z!.1*..i.I
    09a0 - a4 f6 7a ef 13 9c 99 5d-26 7c 2a d8 ac 0c 72 3d   ..z....]&|*...r=
    09b0 - 23 03 27 20 b2 6f d8 8d-97 5f da a1 39 35 2b 71   #.' .o..._..95+q
    09c0 - ef 78 7e 35 e4 aa 85 dc-76 30 76 13 43 e8 09 d2   .x~5....v0v.C...
    09d0 - 72 41 15 9a da 09 47 b1-7e 95 1d 01 e3 34 4b ae   rA....G.~....4K.
    09e0 - 64 2d 01 a4 f4 9f 9d cd-3e 10 9c 1a 65 d7 c7 81   d-......>...e...
    09f0 - de 6b 64 10 0f a3 61 3d-fa 56 1e 48 8a 1d 37 5a   .kd...a=.V.H..7Z
    0a00 - be ff 3c 84 f9 88 4a 45-cf ee 57 29 06 16 47 a6   ..<...JE..W)..G.
    0a10 - b0 9e de 37 83 ae f1 45-7b 58 d7 8a 75 c1 93 09   ...7...E{X..u...
    0a20 - 4b 78 9f fa 6a 1f 52 e5-a8 9c 66 ea 9e 95 40 ea   Kx..j.R...f...@.
    0a30 - 2d 80 57 a3 90 8d 08 e9-58 45 6b a2 22 df f0 37   -.W.....XEk."..7
    0a40 - 6e 6c 2d 18 a6 51 6f 54-09 de 04 cb 1e 9d e3 b5   nl-..QoT........
    0a50 - 90 2b 42 53 d4 a1 f6 8f-09 3a ec bb b1 8b 1a 8a   .+BS.....:......
    0a60 - 5b 1b 64 16 2b c4 fd 49-ee b9 c8 b8 6b 79 07 d2   [.d.+..I....ky..
    0a70 - 30 69 14 3c f7 e0 dd 53-60 59 18 b1 b7 d9 91 75   0i.<...S`Y.....u
    0a80 - 79 a7 d9 25 2e ba ea 53-ab 46 d6 bd 9d 97 bc f8   y..%...S.F......
    0a90 - 4a ac 6a 77 88 ae c1 08-0b c7 4a c5 76 5a fe 22   J.jw......J.vZ."
    0aa0 - ae 3b c9 30 20 a0 74 45-ee d8 11 d0 86 23 94 01   .;.0 .tE.....#..
    0ab0 - 48 40 f1 9d 25 97 aa ff-48 e7 3b ab 4f bb c6 52   H@..%...H.;.O..R
    0ac0 - 62 66 c9 25 7d ad 35 11-cc c8 cb 08 2c ca 37 50   bf.%}.5.....,.7P
    0ad0 - 96 3f 59 db b2 7c c4 92-3c be 91 8a 40 24 10 6b   .?Y..|..<...@$.k
    0ae0 - 4c df e4 92 5b 4b 19 ee-cd ce 7c ef b3 bc e7 7f   L...[K....|.....
    0af0 - e3 0f 3a 9b b8 dc 9a ca-57 8d ff c3 7f f6 86 cf   ..:.....W.......
    0b00 - ab 40 5e 70 8f 67 db bc-75 57 13 c6 3e 7d 1c b7   .@^p.g..uW..>}..
    0b10 - fd c0 ed fa 2b 43 5e ce-75 d8 fc 9d aa 24 43 27   ....+C^.u....$C'
    0b20 - 80 66 aa ca b8 c4 9f 27-ae c6 3c 59 a1 e5 8d 92   .f.....'..<Y....
    0b30 - 96 7c 6c 83 40 4e 23 cd-91 cd 7f 3b 79 07 03 fc   .|l.@N#....;y...
    0b40 - 11 60 54 95 48 73 5d 08-90 11 b6 b3 b3 67 96 78   .`T.Hs]......g.x
    0b50 - 61 0d b5 89 98 06 25 dc-b0 2e e8 43 be 62 2d 74   a.....%....C.b-t
    0b60 - 94 8d f2 ca e7 20 e3 2a-d8 16 c1 36 9b e6 ff 49   ..... .*...6...I
    0b70 - 3b ef f7 74 22 83 ac d3-5c 70 d2 8f d6 31 3a 70   ;..t"...\p...1:p
    0b80 - ae dd 67 8b 0e 71 d5 13-50 c6 c3 de 54 35 ff b6   ..g..q..P...T5..
    0b90 - 15 d5 8c 49 da 9c 35 65-f3 a3 9e 2e 7b 8c df 47   ...I..5e....{..G
    0ba0 - 47 4b de 8d 4d 57 b5 2a-be f8 b5 d9 89 70 c1 d9   GK..MW.*.....p..
    0bb0 - 34 44 c9 bc 8f 53 c6 a7-eb 01 74 8a 48 b6 84 b2   4D...S....t.H...
    0bc0 - 1c 1f 18 d9 14 e7 1e 45-b1 e8 ff 2a 38 bd 0c d0   .......E...*8...
    0bd0 - 52 af 93 4b 7e 43 35 58-86 2d b7 6d 0a bf 30 74   R..K~C5X.-.m..0t
    0be0 - 57 80 13 b4 27 2e 69 56-2a 8e f2 b7 62 7f 19 d0   W...'.iV*...b...
    0bf0 - 88 57 84 35 6f 5e 0a f5-4e b3 95 fb 3f 23 f6 3d   .W.5o^..N...?#.=
    0c00 - 91 5a 85 f5 2a 46 46 e5-0b 7b 4e 29 54 8e b1 ac   .Z..*FF..{N)T...
    0c10 - fa 4b 81 1a ab 0a a5 48-61 81 e4 e3 97 14 02 f6   .K.....Ha.......
    0c20 - db 79 b3 2a ac ed 34 ce-3b 3a e7 d5 69 48 47 d0   .y.*..4.;:..iHG.
    0c30 - ae a8 cb 69 d7 84 fc dc-7c fd 10 26 df 37 06 6e   ...i....|..&.7.n
    0c40 - ec 2d d6 53 20 3c de 3b-40 93 64 18 cb 78 ae 70   .-.S <.;@.d..x.p
    0c50 - 50 94 b7 e3 4b 19 74 26-94 e7 d5 2c 08 36 70 29   P...K.t&...,.6p)
    0c60 - 6d 6b a8 22 4c fb 28 fa-46 6c 84 61 fa 7b f8 12   mk."L.(.Fl.a.{..
    0c70 - 39 ac 3f fa e9 f9 79 a0-bc f9 e6 15 c5 2b 3d ef   9.?...y......+=.
    0c80 - 63 14 c0 d4 34 e5 ed b7-aa f5 79 f0 d3 9b 25 6c   c...4.....y...%l
    0c90 - 4e 3b c3 3e fe ba c9 fc-37 c5 4a cb de 54 22 22   N;.>....7.J..T""
    0ca0 - 90 d1 02 53 ae 55 fb 2f-7c 89 09 2a 7c 56 42 da   ...S.U./|..*|VB.
    0cb0 - f9 15 38 5b 60 4b bd 7c-50 52 76 d7 42 8a 20 5d   ..8[`K.|PRv.B. ]
    0cc0 - 1b 17 7c 81 8a 37 3b e5-d3 99 34 83 15 6f 49 7e   ..|..7;...4..oI~
    0cd0 - 9e 02 7b b3 94 70 47 47-92 ed bf e4 47 db 38 ff   ..{..pGG....G.8.
    0ce0 - 91 78 2e 13 2d 09 13 58-22 87 22 d9 5b 6a 4e 4e   .x..-..X".".[jNN
    0cf0 - c8 b6 cc 39 72 b3 47 b2-6e 1d 57 5c 33 6e b9 9f   ...9r.G.n.W\3n..
    0d00 - 49 88 cb ee b1 87 dd dd-6d 08 51 1c b0 a8 b6 94   I.......m.Q.....
    0d10 - 7c 87 31 3a 37 d1 96 f0-e1 a5 69 5d e0 9a 24 d9   |.1:7.....i]..$.
    0d20 - 85 8f 79 b2 d5 32 f4 7e-0b 2f 01 3c 9f a8 05 60   ..y..2.~./.<...`
    0d30 - 6c 30 4f f5 28 f7 6c 0f-22 74 ac 38 44 06 ea 14   l0O.(.l."t.8D...
    0d40 - 5d 7e 84 fc c4 97 c9 dc-20 e3 22 f0 01 44 5d c6   ]~...... ."..D].
    0d50 - c8 be b8 a0 3d ad b0 25-3a a4 a5 f9 b7 55 03 d8   ....=..%:....U..
    0d60 - 17 1c 37 e7 b6 24 a1 72-e6 94 f7 98 34 68 1d 46   ..7..$.r....4h.F
    0d70 - f1 f4 ad ee b5 aa 85 fb-08 2b 25 e2 8f 3a 5a 2b   .........+%..:Z+
    0d80 - fe 69 9d 25 ef 2b 35 75-2d 37 77 bc cb 62 6e 2f   .i.%.+5u-7w..bn/
    0d90 - ae 29 d7 c2 73 48 09 f9-95 d3 be 6c a5 b1 b4 40   .)..sH.....l...@
    0da0 - f8 60 a1 df 2d d2 5b 12-b9 a4 1d 18 a5 e6 b8 33   .`..-.[........3
    0db0 - 73 46 8e 3b f4 2c 28 0d-46 28 31 ac 13 56 c0 c6   sF.;.,(.F(1..V..
    0dc0 - 51 15 3c 34 e5 7a 8b e3-a0 97 8a b6 df a4 0f 97   Q.<4.z..........
    0dd0 - 45 63 95 be 7f 4d dd 74-51 76 b3 3b 0e 4a 06 f9   Ec...M.tQv.;.J..
    0de0 - 59 86 27 b7 b4 3d b7 09-be b8 9a c4 a3 5e b8 02   Y.'..=.......^..
    0df0 - e9 ef 06 a6 da 64 d7 ae-87 f4 58 95 92 a1 72 66   .....d....X...rf
    0e00 - 78 1a 22 9d 34 df 7b 61-59 9a e4 da ac e5 82 14   x.".4.{aY.......
    0e10 - 96 9a 6a 19 19 73 1b bf-c7 db aa 5b 7a 42 b4 40   ..j..s.....[zB.@
    0e20 - 81 28 85 7d 9f 11 10 d3-c6 a6 f6 a2 56 45 06 92   .(.}........VE..
    0e30 - 2b de 74 83 ff 8a 4f 80-d7 c4 0b 90 9d 97 67 a5   +.t...O.......g.
    0e40 - 07 9e 7d 67 43 c5 dc fb-f5 fb a2 45 11 47 42 88   ..}gC......E.GB.
    0e50 - 95 cc 17 c1 3b d2 32 fd-aa 66 f2 ea dd c9 74 88   ....;.2..f....t.
    0e60 - 01 a2 18 b7 30 8c dd a1-84 a4 f5 3c dc 9c 05 d9   ....0......<....
    0e70 - db 85 4a e5 86 ed 86 63-43 a3 c5 af bd 73 f1 7d   ..J....cC....s.}
    0e80 - 73 42 4f de 36 97 5f e1-02 c1 f5 e6 b2 9c 00 50   sBO.6._........P
    0e90 - 4a 70 f5 2a ad 7c 9d ac-f8 47 18 8c 88 ce 6a 75   Jp.*.|...G....ju
    0ea0 - 47 cc 8e a3 74 ae a9 9c-a3 b5 60 29 f4 16 ea be   G...t.....`)....
    0eb0 - 1e b1 3b 9d ba 4c 60 d6-7a ee 20 a4 d7 c5 c1 f7   ..;..L`.z. .....
    0ec0 - 04 16 a6 bf e0 78 23 38-3f 41 72 26 ca ca 04 ce   .....x#8?Ar&....
    0ed0 - 82 17 89 22 5f 8a fc 24-9d 5f 6e 91 51 ce 02 39   ..."_..$._n.Q..9
    0ee0 - ec a3 10 13 23 ed 9a c9-0c 43 fd e3 e8 e5 1a d5   ....#....C......
    0ef0 - 1d 36 fa b4 26 21 e7 72-35 a5 52 c4 be 11 89 b6   .6..&!.r5.R.....
    0f00 - 1c da 24 fb 8c eb 8f b7-95 e9 21 ef 9e 15 d8 3c   ..$.......!....<
    0f10 - 77 b4 50 a4 b2 df 09 54-7f ec 76 b1 dd 9e ca 1c   w.P....T..v.....
    0f20 - c4 4a 4e 5f 59 65 15 6a-e2 c7 1d 4a 56 51 78 79   .JN_Ye.j...JVQxy
    0f30 - 04 7f c0 69 11 81 f7 01-6c 69 ff 11 ef 2e 1b 6e   ...i....li.....n
    0f40 - dd 7a ed 57 65 88 ef d4-42 b0 92 ba 70 f9 8e 2e   .z.We...B...p...
    0f50 - 53 f1 81 75 fe e0 23 29-ea 0c c4 a0 82 99 e9 c2   S..u..#)........
    0f60 - b0 a1 7a 4b ec 2c 8f e0-a5 fd 06 76 d0 6a 15 7d   ..zK.,.....v.j.}
    0f70 - e3 de 60 49 36 08 14 0b-38 c6 ae 5a 66 62 48 f4   ..`I6...8..ZfbH.
    0f80 - 75 27 14 e8 c8 7b 85 7f-00 15 dd 7f b5 2e 4c 9a   u'...{........L.
    0f90 - ca 16 0a a9 87 d9 36 b9-3e 86 53 dc fc 61 42 ea   ......6.>.S..aB.
    0fa0 - e6 b6 37 14 7e 8e 90 44-d9 68 8c d0 9f 33 5a 0b   ..7.~..D.h...3Z.
    0fb0 - 58 87 17 72 0c a4 37 1a-cb cc f7 b8 13 87 d5 49   X..r..7........I
    0fc0 - 7b f1 2e 0c 17 8e a8 8a-42 9a 4f 49 b2 8e e3 c7   {.......B.OI....
    0fd0 - 05 ab c9 01 61 94 58 e4-9a 8e 2f 51 c9 25 d6 0c   ....a.X.../Q.%..
    0fe0 - bf 33 9f 76 53 e7 b0 e4-c9 b5 3e 15 3c f7 8c 07   .3.vS.....>.<...
    0ff0 - f6 62 85 aa 4e bc 36 1e-bc 53 ca 88 80 a7 3e fe   .b..N.6..S....>.
    1000 - e3 67 d6 af ce 0c 68 cb-ea 42 31 60 25 36 80 0e   .g....h..B1`%6..
    1010 - 1c bd 26 69 76 26 d1 d8-23 35 14 04 e7 b5 52 81   ..&iv&..#5....R.
    1020 - 37 fd 93 e5 09 cb 86 ea-6c d7 9a d6 76 e9 e4 99   7.......l...v...
    1030 - 26 ed 30 9b 41 ab e4 1f-ef 56 bb af 26 d5 0d 3c   &.0.A....V..&..<
    1040 - 34 ef 0e a7 26 43 a1 b1-6a a6 44 fc fd cb 35 aa   4...&C..j.D...5.
    1050 - 54 45 6b d2 8c 78 9c 71-22 48 c0 97 01 66 77 3e   TEk..x.q"H...fw>
    1060 - 75 7f ce 01 8b 43 19 d4-34 69 2e e3 7b 4c 2a 1e   u....C..4i..{L*.
    1070 - cb 14 ad 00 63 16 71 56-84 be 26 1f 96 24 ee 67   ....c.qV..&..$.g
    1080 - 30 fa 14 76 86 47 f5 ff-9d 32 3b a6 38 99 5b fb   0..v.G...2;.8.[.
    1090 - fb 04 b5 88 7c 79 72 b6-6e bc 6e c3 bc 62 f6 fd   ....|yr.n.n..b..
    10a0 - b7 c9 33 15 65 34 dd 54-60 b3 f2 ca 73 25 d9 6e   ..3.e4.T`...s%.n
    10b0 - 55 39 24 89 36 e8 34 f5-6e a5 81 f6 a0 b9 20 4e   U9$.6.4.n..... N
    10c0 - 5a 12 7a d5 8d e1 d8 35-d4 ec aa 40 5e b2 10 30   Z.z....5...@^..0
    10d0 - 65 30 57 e3 82 1c ea c1-70 39 ee 57 7c c7 f7 b5   e0W.....p9.W|...
    10e0 - 3b ee 52 1b d4 e7 f2 b3-7e 2c 62 18 e5 2c 8c c7   ;.R.....~,b..,..
    10f0 - 7f 60 98 c4 38 15 51 f4-05 52 eb aa 33 2d 3f aa   .`..8.Q..R..3-?.
    1100 - 74 5c 44 bd b9 de 59 bc-71 98 aa 73 e2 99 9f 2d   t\D...Y.q..s...-
    1110 - 7c 90 10 48 93 f4 c6 5c-8f d3 d7 2a 3e 86 86 08   |..H...\...*>...
    1120 - eb 29 a5 5e 88 57 c4 2e-28 b3 30 d2 dc 32 5d 1b   .).^.W..(.0..2].
    1130 - aa 1f a0 14 52 98 5f 47-5b 57 55 0c 47 9b 07 8d   ....R._G[WU.G...
    1140 - 6a 6f 83 5b d5                                    jo.[.

    Start Time: 1754365959
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
HTTP/1.1 500 Internal Server Error
content-length: 0
connection: close

closed
[srv_etqsml@ETQSMLUATAPP001 cdh]$

```