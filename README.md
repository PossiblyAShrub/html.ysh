# HTML Templating in YSH

> [!WARNING]
> this currently does **not** do proper HTML escaping. Do not run on untrusted data.

Generate HTML from YSH.

Tested with YSH 0.24.0.

## Example

```ysh
use html.ysh

html document {
  body {
    h1 id=title 'html.ysh'

    var words = :| generate html from ysh |
    ol {
      for word in (words) {
        li $word
      }
    }
  }
}
```

will write the following HTML to stdout:

```html
<!DOCTYPE html>
<html>
  <body>
    <h1 id="title">
      html.ysh
    </h1>
    <ol>
      <li>
        generate
      </li>
      <li>
        html
      </li>
      <li>
        from
      </li>
      <li>
        ysh
      </li>
    </ol>
  </body>
</html>
```

## Running Tests

Currently `is-main` doesn't work with `use`/modules, so for now all tests can
be run with `ysh test/<test>.ysh`. (Once that bug has been fixed, tests can be
run via `ysh test.ysh`.)

## License

See [LICENSE](./LICENSE) for details.
