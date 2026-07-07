---
order: 100
---

# Style guide
This style guide assumes that you have [Retype up and running](https://retype.com/guides/getting-started/). Once you build and view the site locally, spend 30 minutes browsing through Retype's docs on [configuration](https://retype.com/configuration/project/) and [components](https://retype.com/components/).

Only then should you continue with this style guide. It is best viewed as a web page.

## Naming convention
Use ONLY `kebab case`, with all words in lowercase, for all files and folders. For example, this document is called `style-guide.md`. Kebab case is easiest to read when it renders as a URL.

## Structuring the site
Each section must have `index.md` and `index.yml` pages. 

!!!
Here is a [example](https://github.com/LatticeInnovations/LatticeOnFhirMain/commit/7c657c123a2e85c78f21e8d784ee2da0a74063ea) of a commit in which index pages were added.
!!!

### Default page
`index.md` acts as the landing page for a section. It can be left empty, with just a level 1 heading. It can also be named `README.md`. See Retype's [page configuration](https://retype.com/configuration/page/#default-pages) docs for details.

### Side navigation behavior and visibility controls
`index.yml` provides the following information that controls side navigation behavior
- `expanded`: Whether or not the section should be expanded or collapsed
- `order`: Higher numbers appear higher up in navigation
- `icon`: Uses [Octicons](https://retype.com/components/octicons/), not Github emojis, as a decorative element. Folder icon shown if this parameter is omitted.
- `visibility`: `public|hidden|protected|private`. If omitted, defaults to `public`. Use the `hidden` label in case you are making an extensive change.  See Retype's [visibility settings](https://retype.com/configuration/page/#visibility) for details.

`order`, `icon` and `visibility` properties can also be applied to a page, as follows.
```yml
---
order: 10
icon: light-bulb
visibility: public
---
```

## Sequencing logic
[Retype provides many options](https://retype.com/configuration/page/#order) for deciding the sequence (or order) of sections and pages. This is controlled by the `order` property, introduced in the previous section.

This site [orders by number](https://retype.com/configuration/page/#order-by-number).

!!!
If the `order` property is not set, alphabetical ordering take over. 
!!!

### Sequencing sections 
Use the following sequence: `1000, 990, 980, ..., 20, 10`. Jumping in units of ten leaves space for inserting a new section between two existing ones.

### Sequencing pages
For sections with many pages, like [FHIR resources](/fhir-resources/index.md), sequence pages as 1000, 990, and so on. This has to be strictly adhered to, so that we leave room for future additions.

For smaller sections with a handful of pages, like [Key features](/key-features/index.md), sequence pages as 100, 90, 80 and so on. For mid-sized sections, decrement by a smaller step size, such as one or five.

## IDE configuration
### Link validation 
Link validation prevents navigation errors. While Retype CLI provides a list of link failures, it is better to validates links within the IDE.

VS Code supports [markdown link validation](https://code.visualstudio.com/docs/languages/markdown#_link-validation). This has been enabled for this workspace; see `.vscode/settings.json`. Please enable link validation if you use a different IDE, and inform other contributors via a change to this guide. 

### Spell checking
Use a spell checker in your IDE. This is a must.

For VS Code, the [Code Spell Checker](https://marketplace.visualstudio.com/items/?itemName=streetsidesoftware.code-spell-checker) extension works well. Not only does it spellcheck regular markdown text, it also checks embedded in code. For example, it will highlight `Usres` in a function called `getUsres`.

If it detects a noun that you anticipate using repeatedly (like `FHIR`), go to `Spellings > Add words to workspace settings` to add it to `.vscode/settings.json` so that the word is not tagged for any other team members who also has the same extension installed.

## GitHub-flavored markdown vs Retype syntax
For some components, GitHub-flavored markdown and Retype syntax provide similar results. Use whichever you prefer, but be consistent within a section. Also, if a section is likely to have multiple authors, then lean towards Github-flavored markdown.

One such component is the highlighted note:

+++ UI
> [!NOTE]
> This is the GitHub version. Changing the title from `NOTE` to `IMPORTANT` does NOT change its styling.
+++ Code
~~~
> [!NOTE]
> This is the GitHub version. Changing the title from `NOTE` to `IMPORTANT` does NOT change its styling.
~~~
+++

+++ UI
!!! 
This is a Retype alert. More variants with titles [described here](https://retype.com/components/alert/)
!!!
+++ Code
~~~
!!! 
This is a Retype alert. More variants with titles [described here](https://retype.com/components/alert/)
!!!
~~~
+++

## Styling code
Code snippets must mention the language to allow Retype to prettify it. 

Retype also supports adding a title by adding text after a space. For example, the title added to the code snippet below is `Response body`. Use this feature to avoid redundant headings.

+++ UI
```json Response body
{
  "status" : 1,
  "message" : "data created" 
  data: [
	  {
		  "status": "201 Created",
      "fhirId": "40670",
      "id": "f8cf0c06-8d9e-4b1e-a0c4-9fab28cdc729",
      "err": null
    }
  ]
}
```
+++ Code
~~~
```json Response body
{
  "status" : 1,
  "message" : "data created" 
  data: [
	  {
		  "status": "201 Created",
      "fhirId": "40670",
      "id": "f8cf0c06-8d9e-4b1e-a0c4-9fab28cdc729",
      "err": null
    }
  ]
}
```
~~~
+++

## Tabs vs tables
Use tabs when the user can see information can be presented in chunks, and where the first tab is more important. User tables when all the information needs to be visible.

## Custom UI
Retype supports custom CSS styling via containers. However, be sparing in the use of custom CSS. IF you do, avoid inline styling. 

Read more [here](https://retype.com/components/container/#custom-css-class).

## Digramming with Mermaid
Retype supports Mermaid charts, but it many not be compatible with the latest release. As of April 2025, Retype supports Mermaid v 10.3, wheras 11 is already out. This leads to newer Mermaid chart types [being unsupported](https://github.com/retypeapp/retype/issues/716).

Despite this lag, use Mermaid charts as extensively as possible. In the short-term, use screenshots of Google slides or docs to speed up your work, but create a TODO issue to track conversion to Mermaid charts.