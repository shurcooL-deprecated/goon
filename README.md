goon
====

Go Object Notation

Latest tagged version: N/A

Be warned, this spec is changing a lot. Until it's marked as 1.0, you should assume that it is unstable and act accordingly.

Objectives
----------

Goon aims to be an open standard for human-readable data interchange, primarily between an existing Go program and a future Go program.

Example
-------

The following Go program:

```go
package main

import "<...>/goon"

func main() {
    type Inner struct {
        Field1 string
        Field2 int
    }
    type Lang struct {
        Name  string
        Year  int
        URL   string
        Inner *Inner
    }

    x := Lang{
        Name: "Go",
        Year: 2009,
        URL:  "http",
        Inner: &Inner{
            Field1: "Secret!",
        },
    }

    goon.Dump(x)
}
```

Will produce this goon to stdout:

```go
Lang{
    Name: "Go",
    Year: 2009,
    URL:  "http",
    Inner: &Inner{
        Field1: "Secret!",
    },
}

```

Spec
----

* goon is valid gofmt-ed Go code.
* goon is a [Go literal](http://golang.org/ref/spec#Literal).

Relevant things that need to be integrated here
-----------------------------------------------

- https://github.com/davecgh/go-spew/issues/6
- https://github.com/davecgh/go-spew
- http://golang.org/pkg/encoding/gob/
- http://en.wikipedia.org/wiki/JSON
- http://golang.org/ref/spec
- gofmt
- http://semver.org/

Seriously?
----------

Yeah. I went there.

But why?
--------

Because I want programming to be as easy as possible. As long as Go programs cannot easily spit out at least parts of Go code (i.e. variable values) that I can easily look at, cut relevant parts out of, modify and paste into new Go programs, there will always be things that are harder than they have to be.

More concretely, I hack around with Go ASTs quite often. `parser.ParseFile(...)`, `for _, d := range file.Decls {`, `if f, ok := d.(*ast.FuncDecl); ok {`, `spew.Dump(x);`, that kind of stuff. Right now my iterations are slowed down because I can't easily extract various AST segments that I want to further manipulate.

Did you just steal this template from Tom's TOML?
-------------------------------------------------

Stealing implies I prevented someone from [owning](https://twitter.com/shurcooL/status/266294572949327872) something. When it comes to digital things, one typically copies. However, it's possible to steal [credit](https://twitter.com/shurcooL/status/266294965053820928) for having created something. I don't think that's the case here since I'm acknowledging Tom's original efforts. Thank you Tom, you rock! :)

Implementations
---------------

If you have an implementation, send a pull request adding it to this list. Please note the commit SHA1 or version tag that your parser supports in your readme.

- N/A

License
-------

- [MIT License](http://opensource.org/licenses/mit-license.php)
