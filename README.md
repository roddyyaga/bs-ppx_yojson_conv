This is a version of [ppx_yojson_conv](https://github.com/janestreet/ppx_yojson_conv) for use in BuckleScript projects.

# Installation
Add these dependencies to your `package.json`:
```
"@roddynpm/bs-ppx_yojson_conv": "^0.1.0",
"@roddynpm/bs-ppx_yojson_conv_lib": "^0.3.0",
"@roddynpm/bs-yojson": "^0.3.0",
```
and these bs-dependencies to `bsconfig.json`:
```
"@roddynpm/bs-ppx_yojson_conv",
"@roddynpm/bs-ppx_yojson_conv_lib",
"@roddynpm/bs-yojson",
```
and this ppx flag to `bsconfig.json`:
```
"ppx-flags": ["@roddynpm/bs-ppx_yojson_conv/ppx.sh"]
```
Currently there is only the one ppx binary that works for my setup (in terms of OS etc.). Please create an issue if you would like others.

# Usage
Just like native:
```
[@deriving yojson]
type t = {
  x: string,
  y: int,
};

let some_t = {x: "hello", y: 7};

let a = Yojson.Safe.to_string(yojson_of_t(a_t));

let b = t_of_yojson(Yojson.Safe.from_string({|{"x": "hi", "y": 3}|})).x;
```
