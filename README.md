# PABBLE JSON

JSON library for Pabble/Penguin projects.

## Functions

- `stringify(value)` — converts Penguin values to compact JSON.
- `pretty(value)` — converts Penguin values to formatted JSON.
- `parse(text)` — returns `{ ok, value, index, error }`.
- `decode(text)` — returns the parsed value, or `nil` if parsing fails.
- `escape_string(text)` — escapes a string for internal JSON usage.

## Example

```peng
import("json") as json
import("io") as io

func main() {
    var data = {
        name = "Penguin",
        tags = ["lang", "json"],
        active = true
    }

    io:println(json.stringify(data))
    io:println(json.pretty(data))

    var parsed = json.parse("{\"ok\":true}")

    if parsed.ok {
        io:println(parsed.value.ok)
    } else {
        io:println(parsed.error)
    }
}