Simple Mac Web Server
=================

A convenient droplet app to quickly serve static a website on Mac OS X.


## Introduction

While working on web projects, it's often convenient to be able to
quickly serve up a site directory on your Mac using a webserver for
development or testing. This little app does just that: give it a
directory and it fires up a webserver to serve it from your Mac.


## Requirements

This "App" is a really thin wrapper around Python's SimpleHTTPServer
module, which comes with most recent versions of Mac OS X. If you're
running Mac OS X, you're probably good to go.


## Usage

There are two ways to run the Simple Mac Web Server:

1. Launch the app, then choose a directory using the dialog.
2. Drag & Drop a directory on top of the app's icon.


## Limitations

This app relies heavily on the Python SimpleHTTPServer module, which is,
as the name implies, pretty simple. Don't expect high performance or
many features.

There is no support for PHP, Ruby, Python or any other fancy dynamic
server side stuff. Static files only.

Finally, the app supports only one server instance at a time. If you
need more, use something more advanced or use the terminal to start the
SimpleHTTPServer module from there (you could have learned how to do it
in the time it took to read this README).
