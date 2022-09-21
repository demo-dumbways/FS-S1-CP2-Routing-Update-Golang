---
sidebar_position: 8
---

# 8. Query String for Blog Detail

import useBaseUrl from '@docusaurus/useBaseUrl';

Nama route yang kita gunakan untuk menghandle proses menampilkan blog detail yaitu `/blog`, kemudian diikuti `/{index}` agar kita dapat menangkap index yang dikirim melalui route/url. 

<br />

<a class="btn-example-code" href="">
Contoh code
</a>

<br />
<br />

```go {8} title="main.go"
// this code same like before
func main() {
    route := mux.NewRouter()
    
    route.HandleFunc("/", helloWorld).Methods("GET")
    route.HandleFunc("/home", home).Methods("GET")
    route.HandleFunc("/blog", blogs).Methods("GET")
    route.HandleFunc("/blog/{id}", blogDetail).Methods("GET")
    route.HandleFunc("/contact-me", contactMe).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}
// continuation this code same like before
```

Sementara untuk saat ini kita akan mengirimkan response dalam bentuk konten statis

<br />

<a class="btn-example-code" href="">
Contoh code
</a>

<br />
<br />

```go {4-23} title="main.go"
// this code same like before
// this code below func blogs(w http.ResponseWriter, r *http.Request) { 

func blogDetail(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")

	id, _ := strconv.Atoi(mux.Vars(r)["id"])

	var tmpl, err = template.ParseFiles("views/blog-detail.html")
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		w.Write([]byte("message : " + err.Error()))
		return
	}

	resp := map[string]interface{}{
		"Data": Data,
		"Id":   id,
	}

	w.WriteHeader(http.StatusOK)
	tmpl.Execute(w, resp)
}

func contactMe(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")

	var tmpl, err = template.ParseFiles("views/contact.html")
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		w.Write([]byte("message : " + err.Error()))
		return
	}

	w.WriteHeader(http.StatusOK)
	tmpl.Execute(w, Data)
}
```

Response yang dikirimkan bukan hanya sekedar view saja, namun bisa juga mengirimkan data yang dibungkus kedalam struct. Data yang dikirimkan melalui response ini bisa kita gunakan pada view yang dituju, dalam case ini view tersebut adalah blog detail.