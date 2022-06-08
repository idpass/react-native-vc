# react-native-vc

React Native component to verify the signature of a JWT string representation of a Verifiable Credential.

## Installation

``` sh
npm install react-native-vc
```

## Usage
``` js
import { verifySignature } from "react-native-vc";

// ...

const isValid = verifySignature(jwtStr);
```

See complete React Native sample in https://github.com/idpass/react-native-vc/tree/main/example/src

## How to construct the JWT string from a Verifiable Credential (VC) in JSON format
With an existing [sample VC](https://github.com/idpass/mimoto/blob/develop/src/main/resources/template.json) stored as a file, do:

``` js
const fs = require('fs')
const vc = fs.readFileSync('filename.json')
const vcJson = JSON.parse(vc)
var parts = vcJson.event.data.proof.signature.split('.')
const jwtStr = parts[0] + '.' + vcJson.event.data.credential + '.' + parts[2]

// Then verify the signature of jwtStr
var isValid = verifySignature(jwtStr) 
```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
