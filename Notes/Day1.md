Related to Network the model of payment is that we pay for **Egress** traffic (going outside Azure), but we don't pay for **ingress** traffic (going inside azure)

![Traffic](/Notes/Images/Traffic1.svg)<br>
<br>

A ***Vnet*** lives inside a subscription and a particular region, the ***Vnet*** can't expand across boundries outside the ones that it was created in. It must be defined as at least one IPv4 CIDR address range and if you want to, one IPv6 CIDR adress range.<br>

The ***Vnet*** can be broken in ***subnets*** inside the CIDR range that we gave to it, this subnet will carry the region and the subscription as they are the inheritance of the ***Vnet*** where the ***subnet*** lives.

Inside the any subnet we always lose 5 IP adresses, as they are always used by to define the following:
**This example is based on a /24 CIDR**

![Subnet](/Notes/Images/Subnet1.svg)<br>
<br>

If we follow other CIDR based adresses it will be always the first four adresses and the last one of any network inside the CIDR that we are using. We should not forget that all the IP's here are ***Private** IP's, here we can't assign a DHCP, this will be facilitated by **Azure fabric**, what you can do is to static assign IP's to the resources, lets say in this case to a Network card.

Public IP adresses will need to be explicited assigned in the creation of the resource, this is the only way that your resource will get a public IP's otherwise will always have a Private IP


Azure gives you the ability to bring your own Public IP's address space into Azure, you will need to validate that you own thta pulic IP, via a plentora of methods.<br><br>

As we talked above a ***Vnet*** can only live in one region, but if we need to communitate with other ***Vnets*** that aren't inside that region one of the ways that we have is by using ***Peering***, this way allows other ***Vnets*** that are in other regions to communicate to resources alocated in neighboor ***Vnets***.

![Peering](/Notes/Images/Peering1.svg)<br>

Based on the image above let's assume that we have 3 ***Vnets*** in diferent regions and in one of that regions we have a virtual machine running some kind of service that we need to access from the other ***Vnet's***, one of the possible ways to do this is creating a peer between ***Vnet's*** as demonstrated in the above image. In this way the ***Vnet2*** and ***Vnet3*** can have the possibility to access the virtual machine in the ***Vnet1***.<br><br>
This by default won't be enought to let the traffic pass from ***Vnet*** to ***Vnet***, to do so, we need to go into the ***Vnet*** that we want to peer and in the settings choose ***Peering***, this will open a new pane and we can now choose to create a new peering. When this option is selected we can check the box of "Allow '***VnetN***' to access the peered virtual network", this way we can now access the virtual machine from another ***Vnet***
