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


