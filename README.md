# mip-deployment for CentOS >= 8.0.1905

This is the MIP6 ready **local** deployment script.

* In order to fix the default *PATH* for users in CentOS, execute the following:
```bash
cat <<EOF >/etc/profile.d/path.sh
paths="/usr/local/bin /usr/local/sbin"

for path in \$paths; do
        if [ "\$(echo \$PATH|grep -w \$path)" = "" ]; then
                PATH="\$PATH:\$path"
        fi
done
export PATH
EOF

. /etc/profile.d/path.sh
```

* Once you get it, you may change the install path in the script, to /opt/mip (it's $(pwd) by default, which means that the setup is done in the directory where you are when you call the command. Changing it to /opt may be a better idea then).
```bash
sed --in-place 's/^INSTALL_PATH.*/INSTALL_PATH="\/opt\/mip"/' mip-deployment/local_deployment.sh
```
* Then, you may move the script to use it later the easy way
```bash
mv mip-deployment/local_deployment.sh /usr/local/bin/mip
```
* Then, just call *mip* with its options to auto-do the setup: start, stop, status, whatever required
```bash
mip install -y
```
```bash
mip status
```
* If you have issues, sometimes, doing it may save you
```bash
mip restart
```
* Or even, in case of real problems
```bash
mip stop --force
mip start
```
