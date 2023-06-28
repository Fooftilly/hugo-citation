# Hugo Citation
This is a very basic implementation of some kind of citation system for Hugo based in APA.
It is still work in progress.
Bugs are expected.

## Install
You can manually download this repo and place it inside `themes/hugo-citation` directory.

You can also use git and add it as submodule. Run this inside your Hugo project directory:
```bash
git submodule add https://github.com/Fooftilly/hugo-citation.git themes/hugo-citation
```

## Configure
For this to work, you must configure your theme section inside `config.toml` file:
```
...
theme = ["...", "...", "hugo-citation"]
...
```

## Usage
You will need to create a json file containing your bibliography.
I suggest creating something like this:
```bash
# Hugo project directory
├── content
    ├── bibliography
        ├──bib.json
```

You will also need to edit Hugo's frontmatter inside the file that you want to cite in:
```yml
---
...
bibFile: "content/bibliography/bib.json"
citations:
  - "key1"
  - "example2"
---
```

You will need to add citation key that you want to use, too.

Those keys are provided from the bib.json file. It should look like this:
```json
{
  "key1": {
    "author": "Author1",
    "title": "Title of Work 1",
    "year": "Year1",
    "source": "Source1",
    "url": "URL1"
  },
  "example2": {
    "author": "Author2",
    "title": "Title of Work 2",
    "year": "Year2",
    "source": "Source2",
    "url": "URL2"
  },
  ...
}
```

Valid fields inside this json file are:
`author`, `title`, `chaptertitle`, `year`, `journal`, `publisher`, `url`, `place`, `translator`, `editor`, `pages`, `volume`, `number` and `notes`.


I've also indluded `bib-gen.html` file inside the repo. It can be used to easily generate these json fields.

### Shortcodes
To cite a source, use the shortcode `{{< cite "key1" >}}`. If you want to include a page number, use `{{< cite "key1" 22 >}}`, replacing "key1" with the actual citation key and 22 with the desired page number.

To generate a bibliography at the end of your document, use the following shortcode:
```
{{< bibliography >}}
```

## TODO
- Order bibliography by last name instead of numbers
- Multiple language support using i18n
- Footnote style citations
- Pop-up style windows next to footnote style citations
