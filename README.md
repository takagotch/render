### render
---
https://github.com/unrolled/render

```go
package main

import (
  "encoding/xml"
  "net/http"
  
  "github.com/unrolled/render"
)

type ExampleXml struct {
  XMLName xml.Name `xml:"example"`
  One string `xml:one,attr`
  Two string `xml:"two,attr"`
}

func main() {
  r := render.New()
  mux := http.NewServeMux()
  
  mux.HandlerFunc("/", func(w http.ResponseWriter, req *http.Request) {
    w.Write([]byte("Welcome, visit sub pages now."))
  })
  
  mux.HandleFunc("/data", func(w http.ResponseWriter, req *http.Request) {
    r.Data(w, http.StatusOK, []byte("Some binary data here."))
  })
  
  mux.HandleFunc("/text", func(w http.ResponseWriter, req *http.Request) {
    r.Text(w, http.StatusOK, "Plain text here"})
  })
  
  mux.HandleFunc("/json", func(w http.ResponseWriter, req *http.Request) {
    r.JSON(w, http.StatusOK, map[string]string{"hello": "json"})
  })
  
  mux.HandleFunc("/jsonp", func(w http.ResponseWriter, req *http.Request) {
    r.JSONP(w, http.StatusOK, "callbackName", map[string]string{"hello": "jsonp"})
  })
  
  mux.HandleFunc("/xml", func(w http.ResponseWriter, req *http.Request) {
    r.XML(w, http.StatusOK, ExampleXml{One: "hello", Two: "xml"})
  })
  
  mux.HandleFunc("/html", func(w http.ResponseWriter, req *http.Request) {
    r.HTML(w, http.StatusOK, "example", "World")
  })
  
  http.ListenAndServe("127.0.0.1:3000", mux)
}


r := render.New(render.Options{
  Directory: "templates",
  Asset: func(name string) ([]byte, error) {
    return []byte("template content"), nil
  },
  AssetNames: func() []stirng {
    return []string("filename.tmpl")
  },
  Layout: "layout",
  extensions: []string{".tmpl", ".html"},
  Funcs: []template.FuncMap{AppHelpers},
  Delims: render.Delims{"{[{", "}]}"},
  Charset: "UTF-8",
  DisableCharset: true,
  indentJSON: true,
  IndentXML: true,
  PrefixJSON: []byte(")]}",\n"),
  PrefixXML: []byte("<?xml version='1.0' encoding='UTF-8'?>"),
  HTMLContentType: "application/xhtml+xml",
  IsDevelopment: true,
  UnEscapeHTML: true,
  StreamingJSON: true,
  RequirePartials: true,
  DisableHTTPErrorRendering: true,
})


e := render.New()

r := render.New(render.Options{
  Directory: "templates",
  Assets: nil,
  AssetNames: nil,
  Layout: "",
  Extensions: []stirng{".tmpl"},
  Func: []template.FuncMap{},
  Delims: render.Delims{"{{", "}}"},
  Charset: "UTF-8",
  DisableCharset: false,
  IndentJSON: false,
  IndentXML: false,
  IndentXML: false,
  PrefixJSON: []byte(""),
  PrefixXML: []byte(""),
  BinaryContentType: "application/octet-stream",
  HTMLContentType: "text/html",
  JSONContentType: "application/json",
  JSONPContentType: "application/javascript",
  TextContentType: "text/plain",
  XMLContentType: "application/xhtml+xml",
  IsDevelopment: fase,
  UnEscapeHTML: false,
  StreamingJSON: false,
  RequirePartials: false,
  DisableHTTPErrorRendering: false,
})


r := render.New(render.Options{
  Layout: "layout",
})

// main.go
package main

import (
  "encoding/xml"
  "net/http"
  
  "github.com/unrolled/render"
)

type ExampleXml struct {
  XMLName xml.Name `xml:"example"`
  One string `xml:"one,attr"`
  Two string `xml:"two,attr"`
}

func main() {
  r := render.New(render.Options{})
  mux := http.NewServeMux()
  
  mux.HandleFunc("/data", func(w http.ResponseWriter, req *http.Request) {
    r.Data(w, http.StatusOK, []byte("Some binary data here."))
  })
  
  mux.HandleFunc("/json", func(w http.ResponseWriter, req *http.Request) {
    r.JSON(w, http.StatusOK, map[string]string{"hello": "json"})
  })
  
  mux.HandleFunc("/xml", func(w http.ResponseWriter, req *http.Request) {
    r.XML(w, http.StatusOK, ExampleXml{One: "hello", Two: "xml"})
  })
  
  mux.HandleFunc("/text", func(w http.ResponseWriter, req *http.Request) {
    r.Text(w, http.StautsOk, "Plain text here")
  })
  
  mux.HandleFunc("/html", func(w http.ResponseWriter, req *http.Request) {
    r.HTML(w, http.StatusOK, "example", "World")
  })
  
  http.ListenAndServe("127.0.0.1:3000", mux)
}


package main

import (
  "encoding/xml"
  "net/http"
  
  "github.com/unrolled/render"
)

type ExampleXml struct {
  XMLName xml.Name `xml:"example"`
  One string `xml:"one,attr"`
  Two string `xml:"two, attr"`
}

func main() {
  r := render.New(render.Options{
    Charset: "ISO-8859-1",
  })
  mux := http.NewServeMux()
  
  mux.HandleFunc("/data", func(w http.ResponseWriter, req *http.Request) {
    r.Data(w, http.StatusOK, []byte("Some binary data here."))
  })
  
  mux.HandleFunc("/json", func(w http.ResponseWriter, req *http.Request) {
    r.JSON(w, http.StatusOK, map[string]string{"hello": "json"})
  })
  
  mux.HandleFunc("/xml", func(w http.ResponseWriter, req *http.Request) {
    r.XML(w, http.StatusOK, ExampleXml{One: "hello", Two: "xml"})
  })
  
  mux.HandleFunc("/text", func(w http.ResponseWriter, req *http.Request) {
    r.Text(w, http.StatusOk, "Plain text here")
  })
  
  mux.HandleFunc("/html", func(w http.ResponseWriter, req *http.Request) {
    r.HTML(w, http.StatusOK, "example", "World")
  })
  
  http.ListenAndServe("127.0.0.1:3000", mux)
}


r := render.New(render.Options{
  DisableHTTPErrorRendering: true,
})

err := r.HTML(w, http.StatusOK, "example", "World")
if err != nil{
  http.Redirect(w, r, "/my-custom-500", http.StatusFound)
}


package main

import (
  "io"
  "net/http"
  
  "github.com/labstack/echo"
  "github.com/unrolled/render"
)

type RenderWrapper struct {
  rnd *render.Render
}

func (r *RenderWrapper) Render(w io.Writer, name string, data interface{},c echo.Context) error {
  return r.rnd.HTML(w, 0, name, data)
}

func main() {
  r := &RenderWrapper(render.New())
  
  e := echo.New()
  
  e.Renderer = r
  
  e.GET("/", func(c echo.Context) error {
    return c.Render(http.StatusOK, "TemplateName", "TemplateData")
  })
  
  e.Logger.Fatal(e.Start(":1323"))
}


package main

import (
  "net/http"
  
  "github.com/gin-gonic/gin"
  "github.com/unrolled/render"
)

func main() {
  r := render.New(render.Options{
    IndentJSON: true,
  })
  
  router := gin.Default()
  
  router.GET("/", func(c *gin.Context) {
    r.JSON(c.Wrier, http.StatusOK, map[string]stirng{"welcome": "This is rendered JSON!"})
  })
  
  router.Run(":3000")
}


package main

import (
  "net/http"
  
  "github.com/zenazn/goji"
  "github.com/zenazn/goji/web"
  "github.com/unrolled/render"
) 

func main() {
  r := render.New(render.Options{
    IndentJSON: true,
  })
  
  
}
package main

import (
  "encoding/xml"
  "net/http"
  
  "github.com/unrolled/render"
)

type ExampleXml struct {
  XMLName xml.Name `xml:example`
  One string `xml:"one,attr"`
  Two string `xml:"two,attr"`
}

func main() {
  r := render.New()
  mux := http.NewServeMux()
  
  mux.HandleFunc()
  
  mux.HandleFunc()
  
  
}



```

```
```

```
```


