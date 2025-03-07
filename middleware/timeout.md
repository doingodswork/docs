# Timeout

Timeout middleware for [Fiber](https://github.com/gofiber/fiber) wraps a `fiber.Handler` with a timeout. If the handler takes longer than the given duration to return, the timeout error is set and forwarded to the centralized [ErrorHandler](https://docs.gofiber.io/error-handling).

## Signatures

```go
func New(h fiber.Handler, t time.Duration) fiber.Handler
```

## Examples

Import the middleware package that is part of the [Fiber web framework](https://github.com/gofiber/fiber)

```go
import (
  "github.com/gofiber/fiber/v2"
  "github.com/gofiber/fiber/v2/middleware/timeout"
)
```

After you initiate your Fiber app, you can use the following possibilities:

```go
handler := func(ctx *fiber.Ctx) {
    ctx.Send("Hello, World 👋!")
}

app.Get("/foo", timeout.New(handler, 5 * time.Second))
```

