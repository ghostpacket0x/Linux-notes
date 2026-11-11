# Lab 12: Serving files over HTTP

**Goal:** serve a folder with one HTML page, open it in a browser, then stop the server.

**Linked section:** [12 Serving files over HTTP](../sections/12-serving-files-over-http.md)

## Steps

```bash
mkdir -p ~/site && cd ~/site
echo "<h1>Hello from my server</h1>" > index.html
npx http-server -p 8080
```

Open `http://localhost:8080` in Firefox, then press `Ctrl+C` in the terminal.

## What to check

The page should show "Hello from my server".

## Clean up

```bash
rm -r ~/site
```

If `npx` isn't found, use `php -S 127.0.0.1:8080` instead.
