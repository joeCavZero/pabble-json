# PABBLE JSON

JSON library for Pabble/Penguin projects.

## Functions

- `parse(text)` — Parses a JSON string and returns `{ ok, value, error }`.
- `decode(text)` — Parses a JSON string and returns the value or `nil` on failure.
- `stringify(value)` — Converts a Penguin value to compact JSON.
- `pretty(value)` — Converts a Penguin value to formatted JSON.
- `escape_string(text)` — Escapes a string using JSON rules.

## Reading a JSON file

```peng
import("fs") as fs
import("io") as io
import("json") as json

func main() {
    var text = fs:read("config.json")

    var result = json:parse(text)

    if !result.ok {
        io:println("Failed to parse JSON:")
        io:println(result.error)
        return
    }

    var config = result.value

    io:println("Application:")
    io:println(config.name)

    io:println("Version:")
    io:println(config.version)

    io:println("Debug:")
    io:println(config.debug)
}
```

Example `config.json`:

```json
{
    "name": "Pebble",
    "version": "0.1.0",
    "debug": true
}
```

## Creating a JSON document

```peng
import("io") as io
import("json") as json

func main() {
    var config = {
        name = "Pebble",
        version = "0.1.0",
        debug = true,
        authors = [
            "Joe",
            "Penguin Team"
        ]
    }

    io:println(json:stringify(config))

    io:println(json:pretty(config))
}
```