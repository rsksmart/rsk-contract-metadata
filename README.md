<p align="middle">
    <img src="https://www.rsk.co/img/rsk_logo.svg" alt="logo" height="100" >
</p>
<h3 align="middle">RSK Contract Metadata</h3>
<p align="middle">
    A mapping of addresses to metadata, like names, and images of those addresses' logos.
</p>
<p align="middle">
  <a href="https://circleci.com/gh/rsksmart/rsk-contract-metadata">
    <img src="https://img.shields.io/circleci/build/github/rsksmart/rsk-contract-metadata?label=test" alt="circlci">
  </a>
  <a href="https://npmjs.org/@rsksmart/rsk-contract-metadata">
    <img src="https://img.shields.io/npm/v/@rsksmart/rsk-contract-metadata" alt="circlci">
  </a>
  
</p>

All address keys follow the [EIP 1191 address checksum format](https://github.com/ethereum/EIPs/issues/1191).

Submit PRs to add valid logos, and obviously valid logos will be merged.

## Usage

You can install from npm with `npm install @rsksmart/rsk-contract-metadata` and use it in your code like this:

```javascript
const contractMap = require('@rsksmart/rsk-contract-metadata')
const toChecksumAddress = require('rskjs-util').toChecksumAddress

function imageElFor (address) {
  const metadata = iconMap[toChecksumAddress(address, 30)]
  if (!('logo' in metadata)) {
    return false
  }
  const fileName = metadata.logo
  const path = `${PATH_TO_METADATA_MODULE}/images/${fileName}`
  const img = document.createElement('img')
  img.src = path
  img.style.width = '100%'
  return img
}
```

## Submission Process

1. Fork this repository.
2. Add your logo image in a web-safe format to the `images` folder.
3. Add an entry to the `contract-map.json` file with the specified address as the key, and the image file's name as the value.

Criteria:
- The icon should be small, square, but high resolution, ideally a vector/svg.
- Do not add your entry to the end of the JSON map, messing with the trailing comma. Your pull request should only be an addition of lines, and any line removals should be deliberate deprecations of those logos.
- PR should include link to official project website referencing the suggested address.
- Project website should include explanation of project.
- Project should have clear signs of activity, either traffic on the network, activity on GitHub, or community buzz.
- Nice to have a verified source code on a RSK explorer.

Tokens should include a field `"erc20": true`, and can include additional fields:

- symbol (a five-character or less ticker symbol)
- decimals (precision of the tokens stored)

A sample submission:

```json
"0x2aCc95758f8b5F583470bA265Eb685a8f45fC9D5": {
  "name": "RIF",
  "logo": "rif.png",
  "erc20": true,
  "symbol": "RIF",
  "decimals": 18
}
```

A full list of permitted fields can be found in the [permitted-fields.json](./permitted-fields.json) file.

## Disclaimer

Maintaining this list is a considerable chore, and it is not our highest priority. We do not guarantee inclusion in this list on any urgent timeline. We are actively looking for fair and safe ways to maintain a list like this in a decentralized way, because maintaining it is a large and security-delicate task.

