# Markdown JavaDoc API

The [`mdjavadoc-api`](https://www.npmjs.com/package/mdjavadoc-api) contains five methods, documented below. Yes, this program does indeed write its own documentation. Information about the accepted parameters and the behavior of these functions can be found in the [project README](https://jfenn.me/redirects/?t=github&d=mdjavadoc).


## [generateMarkdownFiles](./index.js#L29)

**Type:** `function`

Generates a set of markdown docs from the files in a directory. 



|Parameter Name|Description|
|-----|-----|
|dir|The directory to generate the docs from.|
|out|The directory in which to place generated files.|
|options|Optional arguments.|

## [generateMarkdownFile](./index.js#L79)

**Type:** `function`

Generates a markdown doc from the specified file. 



|Parameter Name|Description|
|-----|-----|
|file|The file to generate the docs from.|
|out|The file to output the markdown into.|
|options|Optional arguments.|

## [formMarkdown](./index.js#L94)

**Type:** `function`

Form basic markdown from an array of parsed data. 



|Parameter Name|Description|
|-----|-----|
|data|The parsed data (returned by [parseFile](#parseFile)) to generate markdown from.|
|options|Optional arguments.|

**Returned Value:**  A string of the markdown formatted docs.


## [parseDirectory](./index.js#L143)

**Type:** `function`

Parses docs for all of the files in a directory. 



|Parameter Name|Description|
|-----|-----|
|dir|The starting directory to parse files from.|
|prefix|Internally used prefix to append to package names.|
|reg|A regex statement to match file names to.|

**Returned Value:**  An array of the docs fetched from each file.


## [parseFile](./index.js#L171)

**Type:** `function`

Parses the docs in a specific file. Docs are formatted 
as follows: 

```javascript 
{
	name: "methodName", 
	description: "This method does a thing with something and somethingelse.", 
	type: ["function"], // basically an array of anything that comes before the method name 
	source: "/package/structure/ClassName.java#L247", 
	param: [ // all tags are added to the map 
		{ 
			content: "@param something The thing for the stuff.", 
			template: ["Parameter Name", "Description"], 
			values: ["something", "The thing for the stuff."] 
		}, 
		{ 
			content: "@param somethingelse The other thing for the stuff.", 
			template: ["Parameter Name", "Description"], 
			values: ["somethingelse", "The thing for the stuff."] 
		} 
	] 
} 
``` 

The full list of tags that are included in this object can 
be found [here](https://jfenn.me/redirects/?t=github&d=mdjavadoc).

The full list of tags that are included in this object can 
be found [here](https://jfenn.me/redirects/?t=github&d=mdjavadoc).



|Parameter Name|Description|
|-----|-----|
|file|The file to parse docs from.|
|prefix|The prefix to add to the doc packages.|
|options|Optional arguments.|

**Returned Value:**  An array of the parsed docs for the file.


## [parsePhrase](./index.js#L312)

**Type:** `function`

Parses an embedded tag (usually enclosed in brackets) and returns the 
markdown-formatted result. This currently only works with "@see" and 
"@link" tags. The URL of the formatted link is the similar as the format 
used in the javadoc, making the returned value something like 
`[this](package.name.api#parsePhrase)`. 



|Parameter Name|Description|
|-----|-----|
|phrase|An array of the values of the embedded tag, starting  with the tag name (excluding the @) and all of the following embedded text split by whitespace.|
|prefix|The package prefix to append to urls.|
|fileName|The file name to append to urls.|

**Returned Value:**  A markdown link to append to stuff.
