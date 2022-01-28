# VScode Snippets and Settings

## Snippets
VS Code User Snippets v0.1

Instructions
1. Cmd + shift + “p”
2. “Preferences: Configure User Snippets”
3. Select “javascript.json”
4. Copy and paste code below
5. Save file
6. Rinse & Repeat for the file “javascriptreact.json”

JavaScript:
```json
{
	"Console Log": {
		"prefix":"cl",
		"body": "console.log($1)",
		"description": "Console Log"
	},  
	"For Loop": {
		"prefix": "for", 
		"body": [
			"for(let i = 0; i < array.length; i++) {",
			"  const ${1:element} = array[i]",
			"}"
		],
		"description": "For Loop"
	},
  "Anonymous Function": {
    "prefix": "anonfn",
    "body": ["function() {", "  $2", "}"],
    "description": "Anonymous Function"
  },
  "Arrow Function": {
    "prefix": "arwfn",
    "body": ["const ${1:functionName} = ($2) => {", "  $3", "}"],
    "description": "Arrow Function"
  },
  "Basic If Statement": {
    "prefix": "if",
    "body": ["if(${1:condition}) {", " $2 ", "}"],
    "description": "If Statement"
  },
  "If Else Statement": {
    "prefix": "ifelse",
    "body": ["if(${1:condition}) {", "  $2", "} else {", "  $3", "}"],
    "description": "If else statement"
  },
  "Array Method": {
    "prefix": "arrmth",
    "body": [
      "${1|forEach,map,filter,reduce,some|}((${2:item}) => {",
      "  $3",
      "})"
    ],
    "description": "Array Method"
  },
  "Fetch Request": {
    "prefix": "fetchreq",
    "body": [
      "fetch('${1:url}')",
      "  .then(res => res.json())",
      "  .then(data => console.log(data));"
    ],
    "description": "Fetch Request"
  },
  "asfetchreq": {
    "prefix": "Async Await Fetch",
    "body": [
      "const request = async ($1) => {",
      "    const response = await fetch('${2:url}');",
      "    const payload = await response.json();",
      "    console.log(data);",
      "}"
    ],
    "description": "Fetch Async/Await"
  }
}
```

Instructions
1. Cmd + shift + “p”
2. “Preferences: Configure User Snippets”
3. Select “ruby.json”
4. Copy and paste code below
5. Save file

Ruby: 
```json
{
  "Named Method": {
  "prefix": "nm_mthd, name, method",
    "body": [
      "def ${1:named_method} do |value|",
      "  value",
      "end",
      ""
    ],
    "description": "named method"
  },
  "Array Method": {
    "prefix": "arr_mthd, map, filter, each",
    "body": [
      "${1|map,filter,each,select,reject|} do |value|",
      "  value",
      "end"
    ],
    "description": "Array Method"
  },
    "Route": {
      "prefix": "route",
      "body": [
        "get '/${1:pathway}' => '${2:controller}#${1:pathway}'"
      ],
      "description": "route"
  }
}
```

## Settings 
VScode Tab Settings
1. Cmd + ','
2. Search: “tab”
3. Deselect “Editor: Detect Indentation”
4. Set “Editor: Tab Size” -> 2

### Recommended Extensions
- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)

- [Ruby](https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby)

- [EndWise](https://marketplace.visualstudio.com/items?itemName=kaiwood.endwise)
