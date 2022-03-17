## Python 

### Run a web server from current directory on port 8080

    python3 -m http.server 8080

By default, this server will be listening on all interfaces and on port 8080, but only be accessible from the same computer.


### Run a web server from any directory with -directory

As of Python 3.7, you can use the -directory flag to serve files from a directory that is not necessarily the current directory.

    python3 -m http.server -directory /path/to/folder 8080

### Run a web server that can be reached by other computers

    import http.server
    import socketserver
    import sys

    PORT = 8080
    Handler = http.server.SimpleHTTPRequestHandler

    with socketserver.TCPServer(("", PORT), Handler) as httpd:
        print("serving at port", PORT)
        httpd.serve_forever()

### Log traffic to a file

    import http.server
    import socketserver
    import sys

    PORT = 8080
    Handler = http.server.SimpleHTTPRequestHandler

    with socketserver.TCPServer(("", PORT), Handler) as httpd:
        print("serving at port", PORT)
        buffer = 1
        sys.stderr = open('logfile.txt', 'a', buffer)
        httpd.serve_forever()
