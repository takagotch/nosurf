### nosurf
---
https://github.com/justinas/nosurf

```go
package main

import (
  "fmt"
  "github.com/justinas/nosurf"
  "html/template"
  "net/http"
)

var emplateString string = `

`

var templ = template.Must(template.New("t1").Parse(templateString))

func myFunc(w http.ResponserWriter, r *http.Request) {
  context := make(map[string]string)
  context["token"] = nosurf.Token(r)
  if r.Method == "POST" {
    context["name"] = r.FormValue("name")
  }
  
  templ.Execute(w, context)
}

func main() {
  myHandler := http.HandlerFunc(myFunc)
  fmt.Println("Listening on http://127.0.0.1:8000/")
  http.ListenAndServe(":8000", nosurf.New(myHandler))
}


func HandleJson(w ReponseWriter, r *http.Request) {
  d := struct{
    X, Y int
    Tkn string
  }{}
  json.Unmarshal(ioutil.ReadAll(r.Body), &d)
  if !nosurf.VerifyToken(nosurf.Token(r), d.Tkn) {
    http.Error(w, "CSRF token incorrect", http.StatusBadRequest)
    return
  }
}

func (h *CSRFHandler) ExamptFunc(fn func(r *http.Request) bool)
func (h *SCRFHandler) ExemptGlob(pattern string)
func (h *SCRFHandler) ExemptGlobs(patterns ...string)
func (h *SCRFHandler) ExemptPath(path string)
func (h *SCRFHandler) ExemptPaths(paths ...string)
func (h *SCRFHandler) ExemptRegexp(re interface{})
func (h *SCRFHandler) ExemptRegexpt(res ...interface{})
```

```
```

```
```


