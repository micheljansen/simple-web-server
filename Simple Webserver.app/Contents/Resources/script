#!/bin/sh

SERVER_PATH=$@

while [ ! -d "$SERVER_PATH" ]; do

  if [ ! -z "$SERVER_PATH" ]; then
    echo "ERROR: Cannot serve '$SERVER_PATH'. Please select a valid directory.";
    RES=`osascript -e "tell app \"System Events\"
    activate
    set res to button returned of (display dialog \"Cannot serve '$SERVER_PATH'. Please select a valid directory.\" buttons {\"Quit\", \"Select Directory\"} default button \"Select Directory\" cancel button \"Quit\")
    end tell
    "`
    if [ "$RES" != "Select Directory" ]; then
      echo "Canceled, bye";
      exit 0
    fi
  fi

  SERVER_PATH=`osascript -so -e 'tell application "Finder"
  activate
  POSIX path of (choose folder with prompt "Please select directory to serve")
  end tell'`
  if [[ $SERVER_PATH =~ "canceled" ]] ; then
    echo "Canceled, bye.";
    exit 0
  fi
done

cd "$SERVER_PATH"

osascript -e 'tell application "Simple Webserver" to activate'

echo "Starting Webserver in: `pwd`"
echo "Access it at http://localhost:8000"
python -m SimpleHTTPServer 2>&1
STATUS=$?
echo "Server exited with status: $STATUS"
RES=`osascript -e "tell app \"System Events\"
activate
set res to button returned of (display dialog \"The webserver exited unexpectedly.
See the log window for details.\" buttons {\"OK\"} default button \"OK\" cancel button \"OK\")
end tell
"`
