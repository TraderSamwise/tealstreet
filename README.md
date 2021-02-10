# tealstreet

This GitHub page is for bug tracking / ticket tracking for the https://tealstreet.io trading terminal.

Request beta access via https://t.me/tealstreet

## Keyboard Shortcuts to use in ShortKey Chrome extension

link to extension https://chrome.google.com/webstore/detail/shortkeys-custom-keyboard/logpjaacgmcbpdkdchjiaagddngobkck?hl=en

Extension is currently not available on Chrome Store. Should be fixed soon by the developer. For now, you can download it from this repo. Then on Chrome, go to manage your extensions. Turn on "developer mode", click "Load Unpacked Extension", go to where you downloaded ShortKeys. Click inside that folder, and upload the folder that has the versio number as the title. Local extensions wont sync between your computers like normal chrome extensions.

Please note, the "/trade/..." url / path must be the first page you visit when going to https://www.tealstreet.io. If you, say, login first, such that the initial url you visit is "/login" then you must refresh once in the trading terminal before the shortcuts will work. This is because the ShortKeys shortcuts are only active on "/trade/..." to not interfere with other parts of the site, but because React uses a virtual router it doesn't detect changes to the url within the site itself, only the first page you visit. 

```

[
  {
    "action": "javascript",
    "activeInInputs": true,
    "blacklist": "whitelist",
    "code": "document.getElementsByClassName(\"ant-checkbox-input\")[0].click()\ndocument.getElementsByClassName(\"ant-checkbox-input\")[3].click()",
    "exported": true,
    "key": "e",
    "open": false,
    "sites": "*tealstreet.io/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "label": "Toggle Track Price"
  },
  {
    "action": "javascript",
    "activeInInputs": true,
    "blacklist": "whitelist",
    "code": "document.getElementsByClassName(\"ant-checkbox-input\")[1].click()\ndocument.getElementsByClassName(\"ant-checkbox-input\")[4].click()",
    "exported": true,
    "key": "q",
    "open": false,
    "sites": "*tealstreet.io/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "label": "Toggle Post Only"
  },
  {
    "action": "javascript",
    "activeInInputs": true,
    "blacklist": "whitelist",
    "code": "document.getElementsByClassName(\"ant-checkbox-input\")[2].click()\ndocument.getElementsByClassName(\"ant-checkbox-input\")[5].click()",
    "exported": true,
    "key": "w",
    "open": false,
    "sites": "*tealstreet.io/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "syncToOtherDevices": false,
    "label": "Toggle Reduce"
  },
  {
    "action": "javascript",
    "blacklist": "whitelist",
    "code": "document.getElementsByClassName(\"order-button\")[6].click()",
    "exported": true,
    "key": "alt+shift+a",
    "open": false,
    "sites": "*tealstreet.io/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "activeInInputs": true,
    "label": "Place buy order at price in order form"
  },
  {
    "action": "javascript",
    "blacklist": "whitelist",
    "code": "document.getElementsByClassName(\"order-button\")[13].click()",
    "exported": true,
    "key": "alt+shift+d",
    "open": false,
    "sites": "*tealstreet.io/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "activeInInputs": true,
    "label": "place sell order at price in order form"
  },
  {
    "action": "javascript",
    "activeInInputs": true,
    "blacklist": "whitelist",
    "code": "document.getElementsByClassName(\"ant-table-tbody\")[0].children[0].children[8].children[0].click()",
    "exported": true,
    "key": "alt+shift+k",
    "open": false,
    "sites": "*tealstreet.io/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "label": "close top list position in positions table"
  },
  {
    "key": "alt+shift+t",
    "action": "javascript",
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*",
    "open": false,
    "code": "if (typeof _orderSize == 'undefined') {\n    let _orderSize;\n    let _price;\n    let _rawSize;\n    let _posSize;\n    let _buy;\n    let prevOrder;\n    let nativeInputValueSetter;\n    let _setReduce\n}\n\n_setReduce = false;\n\nnativeInputValueSetter = Object.getOwnPropertyDescriptor(window.HTMLInputElement.prototype, \"value\").set;\n\n_rawSize = document.getElementsByClassName(\"ant-table-tbody\")[0].children[0].children[1].children[0].children[0].innerText;\n_buy = true;\n_posSize = parseFloat(_rawSize)\nif (isNaN(_posSize)) {\n    _buy = false;\n   _rawSize = _rawSize.substring(1, _rawSize.length);\n    _posSize = parseFloat(_rawSize)\n}\n_orderSize = Math.ceil(_posSize * (1/3))\n\n_price = parseFloat(document.getElementsByClassName(\"List\")[0].children[0].children[0].children[1].children[0].children[0].innerText)\n\nif (!_buy) {\n    if (document.getElementsByClassName(\"ant-checkbox-input\")[1].checked) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[1].click()\n    }\n    if (!document.getElementsByClassName(\"ant-checkbox-input\")[2].checked) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[2].click()\n        _setReduce = true;\n    }\n    if (document.getElementsByClassName(\"ant-checkbox-input\")[0].checked) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[0].click()\n    }\n    prevOrder = document.getElementsByClassName(\"ant-input-number-input\")[1].value\n    nativeInputValueSetter .call(document.getElementsByClassName(\"ant-input-number-input\")[1], _orderSize)\n    document.getElementsByClassName(\"ant-input-number-input\")[1].dispatchEvent(new Event('input', { bubbles: true }));\n    nativeInputValueSetter.call(document.getElementsByClassName(\"ant-input-number-input\")[2], _price + 30)\n    document.getElementsByClassName(\"ant-input-number-input\")[2].dispatchEvent(new Event('input', { bubbles: true }));\n    document.getElementsByClassName(\"order-button\")[6].click()\n    nativeInputValueSetter.call(document.getElementsByClassName(\"ant-input-number-input\")[1], prevOrder)\n    document.getElementsByClassName(\"ant-input-number-input\")[1].dispatchEvent(new Event('input', { bubbles: true }));\n    if (_setReduce ) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[2].click()\n    }\n} else {\n    if (document.getElementsByClassName(\"ant-checkbox-input\")[4].checked) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[4].click()\n    }\n    if (!document.getElementsByClassName(\"ant-checkbox-input\")[5].checked) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[5].click()\n        _setReduce = true;\n    }\n    if (document.getElementsByClassName(\"ant-checkbox-input\")[3].checked) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[3].click()\n    }\n    prevOrder = document.getElementsByClassName(\"ant-input-number-input\")[4].value\n    nativeInputValueSetter.call(document.getElementsByClassName(\"ant-input-number-input\")[4], _orderSize)\n    document.getElementsByClassName(\"ant-input-number-input\")[4].dispatchEvent(new Event('input', { bubbles: true }));\n    nativeInputValueSetter.call(document.getElementsByClassName(\"ant-input-number-input\")[5], _price - 30)\n    document.getElementsByClassName(\"ant-input-number-input\")[5].dispatchEvent(new Event('input', { bubbles: true }));\n    document.getElementsByClassName(\"order-button\")[13].click()\n    nativeInputValueSetter.call(document.getElementsByClassName(\"ant-input-number-input\")[4], prevOrder)\n    document.getElementsByClassName(\"ant-input-number-input\")[4].dispatchEvent(new Event('input', { bubbles: true }));\n    if (_setReduce) {\n        document.getElementsByClassName(\"ant-checkbox-input\")[5].click()\n    }\n}",
    "activeInInputs": true,
    "exported": true,
    "sitesArray": [
      "*tealstreet.io/trade*"
    ],
    "label": "close 1/3 of top listed position in positions table"
  },
  {
    "key": "d",
    "action": "javascript",
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "open": false,
    "code": "nativeInputValueSetter = Object.getOwnPropertyDescriptor(window.HTMLInputElement.prototype, \"value\").set;\n\nbuyTrack = document.getElementsByClassName(\"ant-input-number-input-wrap\")[0].children[0].value\nbuyTrack = parseFloat(buyTrack)\n\n    newBuyTrack = buyTrack + 0.5\n    nativeInputValueSetter .call(document.getElementsByClassName(\"ant-input-number-input-wrap\")[0].children[0], newBuyTrack)\n        document.getElementsByClassName(\"ant-input-number-input-wrap\")[0].children[0].dispatchEvent(new Event('input', { bubbles: true }));\n\n\nsellTrack= document.getElementsByClassName(\"ant-input-number-input-wrap\")[3].children[0].value\nsellTrack= parseFloat(sellTrack)\n\n\n    newSellTrack = sellTrack - 0.5\n    nativeInputValueSetter .call(document.getElementsByClassName(\"ant-input-number-input-wrap\")[3].children[0], newSellTrack)\n     document.getElementsByClassName(\"ant-input-number-input-wrap\")[3].children[0].dispatchEvent(new Event('input', { bubbles: true }));",
    "activeInInputs": true,
    "exported": true,
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "move track price offset on both sides closer to top book prices (stops at 0 offset)"
  },
  {
    "key": "a",
    "action": "javascript",
    "code": "nativeInputValueSetter = Object.getOwnPropertyDescriptor(window.HTMLInputElement.prototype, \"value\").set;\n\nbuyTrack = document.getElementsByClassName(\"ant-input-number-input-wrap\")[0].children[0].value\nbuyTrack = parseFloat(buyTrack)\n\nif (buyTrack > 0) {\nnewBuyTrack = buyTrack - 0.5\nnativeInputValueSetter .call(document.getElementsByClassName(\"ant-input-number-input-wrap\")[0].children[0], newBuyTrack)\ndocument.getElementsByClassName(\"ant-input-number-input-wrap\")[0].children[0].dispatchEvent(new Event('input', { bubbles: true }));\n}\n\nsellTrack= document.getElementsByClassName(\"ant-input-number-input-wrap\")[3].children[0].value\nsellTrack= parseFloat(sellTrack)\n\nif (sellTrack < 0) {\nnewSellTrack = sellTrack + 0.5\nnativeInputValueSetter .call(document.getElementsByClassName(\"ant-input-number-input-wrap\")[3].children[0], newSellTrack)\ndocument.getElementsByClassName(\"ant-input-number-input-wrap\")[3].children[0].dispatchEvent(new Event('input', { bubbles: true }));\n}",
    "activeInInputs": true,
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "move track price offset on both sides farther from top of book"
  },
  {
    "key": "ctrl+shift+a",
    "action": "javascript",
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "open": false,
    "code": "document.getElementsByClassName(\"List\")[0].children[0].children[3].children[0].children[0].children[1].click()\ndocument.getElementsByClassName(\"order-button\")[6].click()",
    "activeInInputs": true,
    "exported": true,
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "place buy order at price visible in bottom buy side of orderbook"
  },
  {
    "key": "ctrl+shift+d",
    "action": "javascript",
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "open": false,
    "code": "document.getElementsByClassName(\"List\")[0].children[0].children[3].children[1].children[0].children[1].click()\ndocument.getElementsByClassName(\"order-button\")[13].click()",
    "activeInInputs": true,
    "exported": true,
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "place sell order at price visible in bottom row sell side of orderbook"
  },
  {
    "key": "ctrl+alt+a",
    "action": "javascript",
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "open": false,
    "code": "document.getElementsByClassName(\"List\")[0].children[0].children[2].children[0].children[0].children[1].click()\ndocument.getElementsByClassName(\"order-button\")[6].click()",
    "activeInInputs": true,
    "exported": true,
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "place buy order at price visible in top buy side of orderbook"
  },
  {
    "key": "ctrl+alt+d",
    "action": "javascript",
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "open": false,
    "activeInInputs": true,
    "code": "document.getElementsByClassName(\"List\")[0].children[0].children[2].children[1].children[0].children[1].click()\ndocument.getElementsByClassName(\"order-button\")[13].click()",
    "exported": true,
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "place sell order at price visible in top sell side of orderbook"
  },
  {
    "key": "x",
    "action": "javascript",
    "code": "if(typeof i !== 'undefined'){\n    let i;\n    let rows;\n}\n\ni = 0;\nrows = document.getElementsByClassName(\"ant-table-tbody\")[1].children;\n\nwhile (i < rows.length) {\n    let currRow = rows[i];\n    if (!currRow.classList.contains(\"updating-cell-row\")) {\n         currRow.children[7].children[0].click();\n        break;\n    }\n    i += 1;\n}",
    "activeInInputs": true,
    "blacklist": "whitelist",
    "sites": "*tealstreet.io/trade*\n*192.168.86.34/trade*",
    "sitesArray": [
      "*tealstreet.io/trade*",
      "*192.168.86.34/trade*"
    ],
    "label": "cancel top listed active order (left most tab showing orders must be clicked to work)"
  }
]

```
