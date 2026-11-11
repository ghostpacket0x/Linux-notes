
# 12. Serving files over HTTP

You can turn any folder into a small website with one command. This is handy for sharing files between your VM and your own computer, or for testing.

## Quick reference

| Command | What it does |
|---|---|
| `npx http-server` | Serves the current folder using Node.js |
| `php -S` | Serves the current folder using PHP's built-in server |
| `wget` | Downloads a file from a web server |
| `curl` | Fetches a URL and shows the response |
| `import` | Captures an X server screen (ImageMagick) |

## Starting a server

| Command | What it does | Example |
|---|---|---|
| `npx http-server -p 8080` | Serves the current folder using Node.js (needs npm installed) | `npx http-server -p 8080` |
| `php -S 127.0.0.1:8080` | Serves the current folder using PHP's built-in server | `php -S 127.0.0.1:8080` |

- Open `http://localhost:8080` in a browser to see the files.
- `-p 8080` picks the port number.
- `127.0.0.1` means only your own machine can connect.
- Stop either server with `Ctrl+C`.
- Only serve folders you are happy for others to see.

## Related commands

| Command | What it does | Example |
|---|---|---|
| `wget <url>` | Downloads a file from a web server, useful for testing a server you started | `wget http://127.0.0.1:8080/index.html` |
| `curl -i <url>` | Requests a page and shows the response headers and body | `curl -i http://127.0.0.1:8080/` |
| `import <file>.png` | Captures an X server screen and saves the image (needs a desktop session) | `import screen.png` |   

## Practice 

Try the hands-on lab for this section: [Labs/12-http-practice.md](../Labs/12-http-practice.md)
