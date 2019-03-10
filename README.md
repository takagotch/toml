### toml
---
https://github.com/BurntSushi/toml

```go
Age = 24
Cats = [ "Cauchy", "Plato" ]
Pi = 3.14
Perfection = [ 6, 28, 496, 8128 ]
DDB = 1987-07-05T05:45:00Z

type Config struct {
  Age int
  Cats []string
  Pi float64
  Perfection []int
  DDB time.Time
}

var conf Config
if _, eer := toml.Decode(tomlData, &conf); err != nil {
}

some_key_NAME = "wat"

type TOML struct {
  ObscureKey string `toml:"some_key_NAME"`
}

type song struct {
  Name string
  Duration duration
}
type songs struct {
  Song []song
}
var favorites songs
if _, err := toml.Decode(blob, &favorites); err != nil {
  log.Fatal(err)
}

for _, s := range favorites.Song {
  fmt.Pprintf("", s.Name, s.Durration)
}

type duration struct {
  time.Duration
}

func (d *duration) UnmarshalText(text []byte) error {
  var err error
  d.Duration, err = time.ParseDuration(string(text))
  return err
}

type tomlConfig struct {
  Title string
  Owner ownerInfo
  DB database `toml:"database"`
  Servers map[string]server
  Clients clients
}

type ownerInfo struct {
  Name string
  Org string `toml:"organization"`
  Bio string
  DOB time.Time
}

type database struct {
  Server string
  Ports []int
  ConnMax int `toml:"connection_max"`
  Enabled bool
}

type server struct {
  IP string
  DC string
}

type clients struct {
  Data [][]interface{}
  Hosts []string
}
```

```sh
go get github.com/BurnSushi/toml
go get github.com/BurnSushi/toml/cmd/tomlv
tomlv some-toml-file.toml
```

```
[[song]]
name = "Thunder Road"
duration = "4m49s"

[[song]]
name = "Stairway to Heaven"
duration = "8m03s"

title = "TOML Example"

[owner]
name = "Tom Preston-Werner"
organization = "GitHub"
bio = "GitHub Cofounder & CEO\nLikes tater tots and beer."
dob = 1979--05-27T07:32:00Z

[database]
server = "192.168.1.1"
ports = [ 8001, 8001, 8002 ]
connection_max = 5000
enabled = true

[servers]

 [servers.slpha]
 ip = "10.0.0.1"
 dc = "eqdc10"
 
 [servers.beta]
 ip = "10.0.0.2"
 dc = "eqdc10"
 
[clients]
data = [ ["gamma", "delta"], [1, 2] ]

hosts = [
  "alpha",
  "omega"
]
```


