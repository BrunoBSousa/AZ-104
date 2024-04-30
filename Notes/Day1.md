Related to Network the model of payment is that we pay for **Egress** traffic (going outside Azure), but we don't pay for **ingress** traffic (going inside azure)

![Traffic](/Notes/Images/Traffic1.svg)<br>
<br>

A ***Vnet*** lives inside a subscription and a particular region, the ***Vnet*** can't expand across boundries outside the ones that it was created in. It must be defined as at least one IPv4 CIDR address range and if you want to, one IPv6 CIDR adress range.<br>

The ***Vnet*** can be broken in ***subnets*** inside the CIDR range that we gave to it, this subnet will carry the region and the subscription as they are the inheritance of the ***Vnet*** where the ***subnet*** lives.

Image of a VNET/ subets

Inside the any subnet we always lose 5 IP adresses, as they are always used by to define the following:
**This example is based on a /24 CIDR**

.0 Network adress<br>
.1 Default Gateway<br>
.2 DNS<br>
.3 DNS<br>
.255 Broadcast<br>

(Image of Subetnet Ip losts due to configurations)

If we follow other CIDR based adresses it will be always the first four adresses and the last one of any network inside the CIDR that we are using. We should not forget that all the IP's here are ***Private** IP's, here we can't assign a DHCP, this will be facilitated by **Azure fabric**, what you can do is to static assign IP's to the resources, lets say in this case to a Network card.

Public IP adresses will need to be explicited assigned in the creation of the resource, this is the only way that your resource will get a public IP's otherwise will always have a Private IP
