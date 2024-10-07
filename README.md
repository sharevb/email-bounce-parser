# Email Bounce Parser in Browser

[![Test and Build](https://github.com/sharevb/email-bounce-parser-browser/workflows/Test%20and%20Build/badge.svg?branch=master)](https://github.com/sharevb/email-bounce-parser-browser/actions?query=workflow%3A%22Test+and+Build%22) [![Build and Release](https://github.com/sharevb/email-bounce-parser-browser/workflows/Build%20and%20Release/badge.svg)](https://github.com/sharevb/email-bounce-parser-browser/actions?query=workflow%3A%22Build+and+Release%22) [![NPM](https://img.shields.io/npm/v/email-bounce-parser.svg)](https://www.npmjs.com/package/email-bounce-parser) [![Downloads](https://img.shields.io/npm/dt/email-bounce-parser.svg)](https://www.npmjs.com/package/email-bounce-parser)

Parses bounce emails and extracts details **in Browser**

**😘 Maintainer**: ShareVB

## Original Library

https://github.com/crisp/email-bounce-parser

## Features

The original library is used at [Crisp](https://crisp.chat/) everyday to parse bounce emails.
It supports most variations of bounce emails (Postfix, Dovecat, Gmail, Outlook).

## Usage

```js
const EmailBounceParse = require("email-bounce-parser-browser");

const result = new EmailBounceParse().read(MY_EMAIL_STRING);

console.log(result);
```

## API

### Parse a bounce email

`read(body)` parses the bounce email and extracts available information (error code and type, server, original recipient, etc.):
* `body` must be a string representing the bounce email **text** body (not HTML body). You can use [mailparser](https://github.com/nodemailer/mailparser) for example.

```js
const EmailBounceParse = require("email-bounce-parser-browser");

const result = new EmailBounceParse().read(MY_EMAIL_STRING);

console.log(result);
// {
//   bounce: true,
//
//   email: {
//     body: "This is the mail system at host mailer.acme.email [...] (in reply to RCPT TO command)",
//     intro: "This is the mail system at host mailer.acme.email [...] The mail system",
//     error: "<john@yipee.com>: host smtp.secureserver.net[92.240.81.0] said: [...] (in reply to RCPT TO command)"
//   },
//
//   data: {
//     error: {
//       code: {
//         basic: "550",
//         enhanced: "5.1.1"
//       },
//       label: "<john@yipee.com> Recipient not found.",
//
//       type: "action_not_taken",
//
//       temporary: false,
//       permanent: true,
//
//       data: {
//         type: "no_such_user",
//         blocked: false,
//         spam: false
//       }
//     },
//
//     recipient: "john@yipee.com",
//
//     server: {
//       hostname: "smtp.secureserver.net",
//       ip: "92.240.81.0",
//       port: "25"
//     },
//
//     command: "RCPT TO"
//   }
// }
```

Head over to `/test/fixtures/` for more bounce examples and parsing results (anonymized data).

## Contributing

Feel free to fork this project and submit fixes. We may adapt your code to fit the codebase.

You can run unit tests using:

```
npm test
```

## License

email-bounce-parser-browser is released under the MIT License. See the bundled LICENSE file for details.
