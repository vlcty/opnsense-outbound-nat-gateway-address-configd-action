# Custom configd OPNsense actions

I've created this repository because [my pull request](https://github.com/opnsense/core/pull/4130) has not been merged. One maintainer [has decided that they don't want it in the codebase](https://github.com/opnsense/core/issues/4159) because it's legacy code. Please don't get me wrong! I've rephrased the last sentence a couple of times to sound nicer. I'm not mad at them or butthurt. It's his project and his decision to merge or not. That's the open source spirit. For me this functionality is necessary and not doable with the provided tools.

## The problem

I've a subscription to ExpressVPN. I'm not pulling a default route because I want to decicde which which hosts I want to route over the VPN tunnel. Because every time the tunnel is reestablished a new /30 network is negotiated. So every time I'd need to set a new gateway address and alter my NAT outbound rule. [I've made a blog post about this](https://blog.veloc1ty.de/2020/05/27/opnsense-openvpn-automatic-gateway-creation/) with more details.   
I've added configd actions to automate the two manual actions.

## Install

Login as root to your OPNsense via ssh and get a shell. Execute the following commands:

- Create a custom scripts directory: `mkdir /usr/local/opnsense/scripts/vlcty`
- Copy both php scripts to the previously created directory
- Change the permissions on them: `chmod 0755 /usr/local/opnsense/scripts/vlcty/*`
- Upload the .conf file to `/usr/local/opnsense/service/conf/actions.d/`
- Reload configd: `service configd restart`

If you think this should be part of OPNsense let the maintainers know.
