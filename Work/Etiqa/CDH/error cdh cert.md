```
 [backend] info        2025-08-05 12:22:41.536 [LoggingInterceptor] START-> 2P74KbCvkXAr POST /api/backoffice/portal-user/retrieve-details-direct-cdh - {
417|backoffice  |   value: {
417|backoffice  |     message: 'START-> 2P74KbCvkXAr POST /api/backoffice/portal-user/retrieve-details-direct-cdh'
417|backoffice  |   },
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '0592cdfe8c772c57',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +3s
417|backoffice  | [backend] info        2025-08-05 12:22:41.542 retrieveCdhDataByDetails - {
417|backoffice  |   value: {
417|backoffice  |     message: 'retrieveCdhDataByDetails',
417|backoffice  |     bodyRequest: {
417|backoffice  |       client: {
417|backoffice  |         idType: '001',
417|backoffice  |         idValue: '000522055323',
417|backoffice  |         ecif: 'PIMYS2507WRA9DE92FE'
417|backoffice  |       }
417|backoffice  |     },
417|backoffice  |     adminId: {
417|backoffice  |       _id: '65042ca6d77bfdf29d8126a5',
417|backoffice  |       pfNumber: 'admin01',
417|backoffice  |       name: 'System Admin',
417|backoffice  |       email: '',
417|backoffice  |       password: '$2a$12$E6zRaaO98wO8Efr6P/6VyOSdJFUIYoXWgGVFJR384Txrn75ogk1Gu',
417|backoffice  |       isAccountLocked: false,
417|backoffice  |       loginFailedAttempts: 0,
417|backoffice  |       refreshToken: 'Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI2NTA0MmNhNmQ3N2JmZGYyOWQ4MTI2YTUiLCJ0aW1lc3RhbXAiOjE3NTQzNjc2OTcwNDAsImlhdCI6MTc1NDM2NzY5NywiZXhwIjoxNzU0MzY4NTk3LCJpc3MiOiJFdGlxYSsgQmFja29mZmljZSJ9.FxdVLihy03Uhcr-Lf-DNwsvoCL5cYnP3zQrjxp-SFfOVeXQvPX60SWC2ScAA748rusNF9zMqk0CyTqQeDcW5CNy7ffwouNym7AtSO2eIgLOY0_Da_eh11Q62HOfp98smRo_Q0QRPvs0bSNMr5AcJdsltDhVViHF5eGBRhKNBJIXqbP_6QwKDThhDpxymHoJiAjFRP4ZUoaJhdOhiiHnLud0O8mZ_HCK2Pyly7tXghx-B7UvUXf0-w5xiwUxuNLP41twlGtiXikHtf-XXkqHjaj8VuCi45ZjVwEH8TPpfP6RSsydmyyEzXkphZVxyCGpoK3iS_wd9OyusXQi7CkkGEA',
417|backoffice  |       roleId: '6528f16b6e4c66e7f9726b30',
417|backoffice  |       createdAt: '2023-09-15T10:06:30.223Z',
417|backoffice  |       updatedAt: '2025-08-05T04:21:37.044Z',
417|backoffice  |       lastLogin: '2025-08-05T04:21:37.028Z',
417|backoffice  |       roleName: 'Super Admin',
417|backoffice  |       roleCode: 'SUPER_ADMIN'
417|backoffice  |     }
417|backoffice  |   },
417|backoffice  |   bodyRequest: {
417|backoffice  |     client: {
417|backoffice  |       idType: '001',
417|backoffice  |       idValue: '000522055323',
417|backoffice  |       ecif: 'PIMYS2507WRA9DE92FE'
417|backoffice  |     }
417|backoffice  |   },
417|backoffice  |   adminId: {
417|backoffice  |     _id: '65042ca6d77bfdf29d8126a5',
417|backoffice  |     pfNumber: 'admin01',
417|backoffice  |     name: 'System Admin',
417|backoffice  |     email: '',
417|backoffice  |     password: '$2a$12$E6zRaaO98wO8Efr6P/6VyOSdJFUIYoXWgGVFJR384Txrn75ogk1Gu',
417|backoffice  |     isAccountLocked: false,
417|backoffice  |     loginFailedAttempts: 0,
417|backoffice  |     refreshToken: 'Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI2NTA0MmNhNmQ3N2JmZGYyOWQ4MTI2YTUiLCJ0aW1lc3RhbXAiOjE3NTQzNjc2OTcwNDAsImlhdCI6MTc1NDM2NzY5NywiZXhwIjoxNzU0MzY4NTk3LCJpc3MiOiJFdGlxYSsgQmFja29mZmljZSJ9.FxdVLihy03Uhcr-Lf-DNwsvoCL5cYnP3zQrjxp-SFfOVeXQvPX60SWC2ScAA748rusNF9zMqk0CyTqQeDcW5CNy7ffwouNym7AtSO2eIgLOY0_Da_eh11Q62HOfp98smRo_Q0QRPvs0bSNMr5AcJdsltDhVViHF5eGBRhKNBJIXqbP_6QwKDThhDpxymHoJiAjFRP4ZUoaJhdOhiiHnLud0O8mZ_HCK2Pyly7tXghx-B7UvUXf0-w5xiwUxuNLP41twlGtiXikHtf-XXkqHjaj8VuCi45ZjVwEH8TPpfP6RSsydmyyEzXkphZVxyCGpoK3iS_wd9OyusXQi7CkkGEA',
417|backoffice  |     roleId: '6528f16b6e4c66e7f9726b30',
417|backoffice  |     createdAt: '2023-09-15T10:06:30.223Z',
417|backoffice  |     updatedAt: '2025-08-05T04:21:37.044Z',
417|backoffice  |     lastLogin: '2025-08-05T04:21:37.028Z',
417|backoffice  |     roleName: 'Super Admin',
417|backoffice  |     roleCode: 'SUPER_ADMIN'
417|backoffice  |   },
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +6ms
417|backoffice  | [backend] info        2025-08-05 12:22:41.544 PortalUserService: retrieveCdhDataDirectly - {
417|backoffice  |   value: { message: 'PortalUserService: retrieveCdhDataDirectly' },
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +2ms
417|backoffice  | [backend] info        2025-08-05 12:22:41.547 [CDHVer2Service] Tracker Object - {
417|backoffice  |   value: {
417|backoffice  |     message: 'Tracker Object',
417|backoffice  |     refType: 'SEARCH_PARTY_REQUEST',
417|backoffice  |     traceDetail: {
417|backoffice  |       errors: [],
417|backoffice  |       logs: [],
417|backoffice  |       clientIdNumber: '000522055323',
417|backoffice  |       timestamp: '2025-08-05T04:22:41.544Z'
417|backoffice  |     },
417|backoffice  |     request: {
417|backoffice  |       client: {
417|backoffice  |         idType: '001',
417|backoffice  |         idValue: '000522055323',
417|backoffice  |         ecif: 'PIMYS2507WRA9DE92FE'
417|backoffice  |       }
417|backoffice  |     },
417|backoffice  |     response: {},
417|backoffice  |     moduleType: 'CDH'
417|backoffice  |   },
417|backoffice  |   refType: 'SEARCH_PARTY_REQUEST',
417|backoffice  |   traceDetail: {
417|backoffice  |     errors: [],
417|backoffice  |     logs: [],
417|backoffice  |     clientIdNumber: '000522055323',
417|backoffice  |     timestamp: '2025-08-05T04:22:41.544Z'
417|backoffice  |   },
417|backoffice  |   request: {
417|backoffice  |     client: {
417|backoffice  |       idType: '001',
417|backoffice  |       idValue: '000522055323',
417|backoffice  |       ecif: 'PIMYS2507WRA9DE92FE'
417|backoffice  |     }
417|backoffice  |   },
417|backoffice  |   response: {},
417|backoffice  |   moduleType: 'CDH',
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +3ms
417|backoffice  | [backend] info        2025-08-05 12:22:41.548 [CDHVer2Service] CDH p12Path - {
417|backoffice  |   '0': '/',
417|backoffice  |   '1': 'a',
417|backoffice  |   '2': 'p',
417|backoffice  |   '3': 'p',
417|backoffice  |   '4': '/',
417|backoffice  |   '5': 's',
417|backoffice  |   '6': 'm',
417|backoffice  |   '7': 'i',
417|backoffice  |   '8': 'l',
417|backoffice  |   '9': 'e',
417|backoffice  |   '10': '/',
417|backoffice  |   '11': 'b',
417|backoffice  |   '12': 'a',
417|backoffice  |   '13': 'c',
417|backoffice  |   '14': 'k',
417|backoffice  |   '15': 'e',
417|backoffice  |   '16': 'n',
417|backoffice  |   '17': 'd',
417|backoffice  |   '18': '/',
417|backoffice  |   '19': 'l',
417|backoffice  |   '20': 'i',
417|backoffice  |   '21': 'b',
417|backoffice  |   '22': 's',
417|backoffice  |   '23': '/',
417|backoffice  |   '24': 's',
417|backoffice  |   '25': 'h',
417|backoffice  |   '26': 'a',
417|backoffice  |   '27': 'r',
417|backoffice  |   '28': 'e',
417|backoffice  |   '29': 'd',
417|backoffice  |   '30': '/',
417|backoffice  |   '31': 'p',
417|backoffice  |   '32': 'u',
417|backoffice  |   '33': 'b',
417|backoffice  |   '34': 'l',
417|backoffice  |   '35': 'i',
417|backoffice  |   '36': 'c',
417|backoffice  |   '37': '/',
417|backoffice  |   '38': 's',
417|backoffice  |   '39': 't',
417|backoffice  |   '40': 'a',
417|backoffice  |   '41': 't',
417|backoffice  |   '42': 'i',
417|backoffice  |   '43': 'c',
417|backoffice  |   '44': '/',
417|backoffice  |   '45': 'c',
417|backoffice  |   '46': 'd',
417|backoffice  |   '47': 'h',
417|backoffice  |   '48': '/',
417|backoffice  |   '49': '2',
417|backoffice  |   '50': '5',
417|backoffice  |   '51': '0',
417|backoffice  |   '52': '8',
417|backoffice  |   '53': '0',
417|backoffice  |   '54': '4',
417|backoffice  |   '55': '-',
417|backoffice  |   '56': 'a',
417|backoffice  |   '57': 'p',
417|backoffice  |   '58': 'p',
417|backoffice  |   '59': 'e',
417|backoffice  |   '60': 't',
417|backoffice  |   '61': 'q',
417|backoffice  |   '62': 'p',
417|backoffice  |   '63': 'l',
417|backoffice  |   '64': 'u',
417|backoffice  |   '65': 's',
417|backoffice  |   '66': '-',
417|backoffice  |   '67': 'g',
417|backoffice  |   '68': 'o',
417|backoffice  |   '69': 'l',
417|backoffice  |   '70': 'd',
417|backoffice  |   '71': '.',
417|backoffice  |   '72': 'e',
417|backoffice  |   '73': 't',
417|backoffice  |   '74': 'i',
417|backoffice  |   '75': 'q',
417|backoffice  |   '76': 'a',
417|backoffice  |   '77': '.',
417|backoffice  |   '78': 'c',
417|backoffice  |   '79': 'o',
417|backoffice  |   '80': 'm',
417|backoffice  |   '81': '.',
417|backoffice  |   '82': 'm',
417|backoffice  |   '83': 'y',
417|backoffice  |   '84': '.',
417|backoffice  |   '85': 'p',
417|backoffice  |   '86': '1',
417|backoffice  |   '87': '2',
417|backoffice  |   value: {
417|backoffice  |     '0': '/',
417|backoffice  |     '1': 'a',
417|backoffice  |     '2': 'p',
417|backoffice  |     '3': 'p',
417|backoffice  |     '4': '/',
417|backoffice  |     '5': 's',
417|backoffice  |     '6': 'm',
417|backoffice  |     '7': 'i',
417|backoffice  |     '8': 'l',
417|backoffice  |     '9': 'e',
417|backoffice  |     '10': '/',
417|backoffice  |     '11': 'b',
417|backoffice  |     '12': 'a',
417|backoffice  |     '13': 'c',
417|backoffice  |     '14': 'k',
417|backoffice  |     '15': 'e',
417|backoffice  |     '16': 'n',
417|backoffice  |     '17': 'd',
417|backoffice  |     '18': '/',
417|backoffice  |     '19': 'l',
417|backoffice  |     '20': 'i',
417|backoffice  |     '21': 'b',
417|backoffice  |     '22': 's',
417|backoffice  |     '23': '/',
417|backoffice  |     '24': 's',
417|backoffice  |     '25': 'h',
417|backoffice  |     '26': 'a',
417|backoffice  |     '27': 'r',
417|backoffice  |     '28': 'e',
417|backoffice  |     '29': 'd',
417|backoffice  |     '30': '/',
417|backoffice  |     '31': 'p',
417|backoffice  |     '32': 'u',
417|backoffice  |     '33': 'b',
417|backoffice  |     '34': 'l',
417|backoffice  |     '35': 'i',
417|backoffice  |     '36': 'c',
417|backoffice  |     '37': '/',
417|backoffice  |     '38': 's',
417|backoffice  |     '39': 't',
417|backoffice  |     '40': 'a',
417|backoffice  |     '41': 't',
417|backoffice  |     '42': 'i',
417|backoffice  |     '43': 'c',
417|backoffice  |     '44': '/',
417|backoffice  |     '45': 'c',
417|backoffice  |     '46': 'd',
417|backoffice  |     '47': 'h',
417|backoffice  |     '48': '/',
417|backoffice  |     '49': '2',
417|backoffice  |     '50': '5',
417|backoffice  |     '51': '0',
417|backoffice  |     '52': '8',
417|backoffice  |     '53': '0',
417|backoffice  |     '54': '4',
417|backoffice  |     '55': '-',
417|backoffice  |     '56': 'a',
417|backoffice  |     '57': 'p',
417|backoffice  |     '58': 'p',
417|backoffice  |     '59': 'e',
417|backoffice  |     '60': 't',
417|backoffice  |     '61': 'q',
417|backoffice  |     '62': 'p',
417|backoffice  |     '63': 'l',
417|backoffice  |     '64': 'u',
417|backoffice  |     '65': 's',
417|backoffice  |     '66': '-',
417|backoffice  |     '67': 'g',
417|backoffice  |     '68': 'o',
417|backoffice  |     '69': 'l',
417|backoffice  |     '70': 'd',
417|backoffice  |     '71': '.',
417|backoffice  |     '72': 'e',
417|backoffice  |     '73': 't',
417|backoffice  |     '74': 'i',
417|backoffice  |     '75': 'q',
417|backoffice  |     '76': 'a',
417|backoffice  |     '77': '.',
417|backoffice  |     '78': 'c',
417|backoffice  |     '79': 'o',
417|backoffice  |     '80': 'm',
417|backoffice  |     '81': '.',
417|backoffice  |     '82': 'm',
417|backoffice  |     '83': 'y',
417|backoffice  |     '84': '.',
417|backoffice  |     '85': 'p',
417|backoffice  |     '86': '1',
417|backoffice  |     '87': '2',
417|backoffice  |     message: 'CDH p12Path'
417|backoffice  |   },
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +1ms
417|backoffice  | [backend] info        2025-08-05 12:22:41.549 [CDHVer2Service] CDH p12Path Exists? - {
417|backoffice  |   value: { message: 'CDH p12Path Exists?' },
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +1ms
417|backoffice  | [backend] info        2025-08-05 12:22:41.550 [CDHVer2Service] CDH HTTPS Agent Config - rejectUnauthorized: true, useCertAuth: false - {
417|backoffice  |   value: {
417|backoffice  |     message: 'CDH HTTPS Agent Config - rejectUnauthorized: true, useCertAuth: false'
417|backoffice  |   },
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +1ms
417|backoffice  | [backend] error       2025-08-05 12:22:41.610 CDH Retrieve Error: - {
417|backoffice  |   stack: [ 'Unsupported PKCS12 PFX data' ],
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +60ms
417|backoffice  | [backend] error       2025-08-05 12:22:41.611 CDH Retrieve Party - Unexpected Error - {
417|backoffice  |   stack: [ { error: { code: 'ERR_CRYPTO_UNSUPPORTED_OPERATION' } } ],
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +1ms
417|backoffice  | [backend] error       2025-08-05 12:22:41.613 PortalUserService: retrieveCdhDataDirectly - {
417|backoffice  |   stack: [ { code: 'ERR_CRYPTO_UNSUPPORTED_OPERATION' } ],
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +2ms
417|backoffice  | [backend] error       2025-08-05 12:22:41.613 retrieveCdhDataByDetails error - {
417|backoffice  |   stack: [ { code: 'ERR_CRYPTO_UNSUPPORTED_OPERATION' } ],
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +0ms
417|backoffice  | [backend] error       2025-08-05 12:22:41.613 [CustomException] Unsupported PKCS12 PFX data - {
417|backoffice  |   stack: [ null ],
417|backoffice  |   value: {
417|backoffice  |     statusCode: 500,
417|backoffice  |     message: 'Unsupported PKCS12 PFX data',
417|backoffice  |     errorCode: 'Unsupported PKCS12 PFX data'
417|backoffice  |   },
417|backoffice  |   statusCode: 500,
417|backoffice  |   errorCode: 'Unsupported PKCS12 PFX data',
417|backoffice  |   trace_id: '83239c0af725eb0034b818817c017f7f',
417|backoffice  |   span_id: '905306cd56639439',
417|backoffice  |   trace_flags: '01'
417|backoffice  | } +0ms


```