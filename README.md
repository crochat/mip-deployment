# mip-deployment for Ubuntu >= 18.04

This is the MIP6 ready **local** deployment script.

* Once you get it, you may change the install path in the script, to /opt/mip (it's $(pwd) by default, which means that the setup is done in the directory where you are when you call the command. Changing it to /opt may be a better idea then).
```bash
sed --in-place 's/^INSTALL_PATH.*/INSTALL_PATH="\/opt\/mip"/' mip-deployment/local_deployment.sh
```
* Then, you may move the script to use it later the easy way
```bash
sudo mv mip-deployment/local_deployment.sh /usr/local/bin/mip
```
* Then, just call *mip* with its options to auto-do the setup: start, stop, status, whatever required
```bash
sudo mip install -y
```
```bash
sudo mip status
```
If everything is ok here, this means that you should be able to see the MIP on http://*your_machine*

* If you have issues, sometimes, doing it may save you
```bash
sudo mip restart
```
* Or even, in case of real problems
```bash
sudo mip stop --force
sudo mip start
```
