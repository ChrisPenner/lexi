lexi
====

lexi is a language agnostic movement to map keywords of programming languages for autocompletion, tooltips, and syntax highlighting.

lexi is composed of 3 parts

1. The '_.lex_' file spec which specifies formatting instructions for a language's keywords and documentation.
2. Multiple language-specific parsers designed to organize the keywords, functions, classes, and variables of languages, libraries, modules and files into a '_.lex_' file.
3. A family of text-editor plugins which use _.lex_ files to intelligently provide autocompletion, tooltips, and documentation as the user types.

lexi is necessary because no standards exist in the land of autocompletion, this results in an inconsistent experience for users. It also currently requires an enormous effort on the part of developers to develop a language parser for each language, organize that information independently (not shared amongst similar plugins) then implement a completion plugin and hope to get it right. By standardizing a file format for autocompletion words and documentation and providing a set of tools which can take source code and build organized files of keywords and documentation, all that is left for the developer is to focus on building a good autocompletion interface.

Anyone is welcome to contribute by either improving the spec files, or by building a parser which conforms to the spec files either IN a language of your choice, or FOR a language of your choice, e.g. a parser written in python for building _.lex_ files from _.js_ source files, or perhaps writing a parser in C that can recognize keywords and function in C source code. Before starting a new project make sure to check if a similar project exists to which you could contribute instead.

## Example .lex file for the python module hmac
### inside 
```yaml
HMAC: { 
    type: class,
    children: [ 
        __init__: { 
            type: function, 
            args: [
                self: { 
                    type: HMAC, 
                    required: true }, 
                key: { 
                    type: string,
                    required: true },
                msg: {
                    type: string,
                    default: None,
                    required: false },
                digestmod: {
                    type: hashlib obj, 
                    default: None,
                    required: false }]
            returns: HMAC }
        digest_size: { 
            type: int }
        
        ]
    
    }
digest_size: { type: int, }
```
HMAC:
    type: class
    children:
        - 
