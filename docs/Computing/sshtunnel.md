# Tunnelling to connect behind the CERN Firewall

If you are working from home you may not be able to access certain services that are behind the CERN firewall. A possible solution is to use an `SSH tunnel`. We can set up a tunnel by:
```bash
ssh -D 8888 lxtunnel.cern.ch
```
Which would set up a tunnel on port `8888`. It is possible to set up the tunnel system wide, as show in [this guide](https://codimd.web.cern.ch/s/Hkq8XF7rI), however we advise using the simpler method of a browser extension such as [Proxy SwitchOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif) to switch between the proxy quickly. 