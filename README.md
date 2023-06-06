Ansible Role FRRouting
=========

This role installs and configures frrouting on Ubuntu 20.04+.

Requirements
------------

Operating System Support: Ubuntu 20.04 or later

Role Variables
--------------

# FRR Base
```
frr_hostname: "{{ inventory_hostname }}"
# frr_loopback_address: 192.168.1.1
frr_enable_vtysh: "yes"
```
# FRR Static
```
# frr_static_routes: []
```

# FRR OSPF
```
frr_enable_ospf: "no"
frr_ospf_router_id: "{{ frr_loopback_address }}"
# frr_ospf_networks: []
```

# FRR BGP
```
frr_enable_bgp: "no"
frr_bgp_router_id: "{{ frr_loopback_address }}"
# frr_bgp_local_asn: 65535
# frr_ibgp_neighbors: []
# frr_ebgp_neighbors: []
# frr_bgp_networks: []
```

# FRR Redistribute Connected
```
# frr_redistribute_connected: []
```

# FRR BGP Prefix List
```
# frr_bgp_prefix_list: []
```

# FRR BGP Route Maps
```
# frr_bgp_route_maps: []
```

# UFW
```
frr_ufw_default_route_policy: allow
frr_ufw_deny_routed_traffic_from_untrusted_interfaces: true
frr_untrusted_interfaces:
  - "{{ ansible_default_ipv4['interface'] }}"
```

Dependencies
------------

No dependency.

Example Playbook
----------------

Install
```
ansible-galaxy install cihanyilmazer.ansible_role_docker
```

    - hosts: routers
      roles:
         - cihanyilmazer.ansible_role_frrouting

Run with Custom Tags (at least one tag must be provided)
- frr
- frr-install
- frr-configure-ufw
- frr-configure-base

```
ansible-playbook -i hosts playbook.yml --tags initial --limit routers
```

License
-------

MIT

Author Information
------------------

Cihan Yilmazer<br />
https://www.cihanyilmazer.com<br />
https://www.github.com/cihanyilmazer<br />
https://galaxy.ansible.com/cihanyilmazer<br />