**Shashank Prakash Naidu**

**Overview:**

This diagram illustrates a basic Azure network architecture with a load balancer, two virtual machines (VMs), a network security group (NSG), and a subnet within a virtual network (VNet). It demonstrates how traffic is routed from the internet to the VMs.

**Components:**

- **Internet:** The external network from which traffic originates.
- **Load Balancer:** A network device that distributes incoming traffic across multiple servers (in this case, the two VMs).
- **Public IP:** A static IP address assigned to the load balancer, making it accessible from the internet.
- **VM-1 and VM-2:** Two virtual machines running within the subnet, serving as the backend servers for the load balancer.
- **NSG-1:** A network security group associated with the subnet, filtering incoming and outgoing network traffic based on defined rules.
- **Subnet-01:** A logical division of the virtual network, containing the two VMs.
- **Public-IP-NAT:** A Network Address Translation (NAT) gateway that translates private IP addresses of the VMs to public IP addresses, allowing them to communicate with the internet.

**Traffic Flow:**

1. **Incoming Traffic:** Traffic from the internet reaches the load balancer's public IP address.
2. **Load Balancing:** The load balancer distributes the traffic to either VM-1 or VM-2 based on its load-balancing algorithm.
3. **NAT:** The VMs' private IP addresses are translated to the public IP address of the NAT gateway, allowing them to communicate with the internet.
4. **NSG Rules:** The NSG-1 filters incoming and outgoing traffic to the VMs based on defined rules. This helps protect the VMs from unauthorized access and ensures only allowed traffic reaches them.

**Key Points:**

- The load balancer provides high availability and scalability by distributing traffic across multiple VMs.
- The NSG enhances security by filtering traffic and preventing unauthorized access to the VMs.
- The NAT gateway enables the VMs to communicate with the internet using a single public IP address.
- The subnet provides a logical grouping for the VMs within the virtual network.
- This architecture is commonly used in Azure to create scalable and secure web applications or services that can handle high traffic loads.

**Additional Notes:**

- **NAT Gateway:**
  - Provides a secure and efficient way for resources in a private subnet to access the internet without exposing them directly to public traffic.
  - Translates private IP addresses to public IP addresses.
- **Load Balancer:**
  - Distributes incoming traffic across multiple VMs to improve performance, reliability, and scalability.
  - Helps prevent bottlenecks and improve fault tolerance.
- **VMs:**
  - Can be Windows or Linux based.
  - Serve as the backend servers for the load balancer.
- **Virtual Network:**
  - Provides a private network environment for the load balancer, VMs, and other resources.
  - Ensures secure and efficient communication within the VNet.
- **Network Watcher and Connection Monitor:**
  - Essential tools for monitoring and troubleshooting network connectivity issues.
  - Provide insights into network traffic, performance, and potential problems.

**Testing:**

1. **NAT Gateway:** Verify the IP address returned by a command matches the public IP address of the NAT gateway.
2. **Ping with Linux VM using Private address:** Test communication between the VMs within the subnet.
3. **Communication with external resources:** Ensure the VMs can access external resources through the NAT gateway.
4. **Network Watcher:** Use Network Watcher to monitor for any issues or failures in network connectivity.
5. **Nginx-listener:** If not installed on the Linux VM, install it to avoid network watcher failures.
6. **Alert Rules:** Create alert rules in the Monitor section for both Windows and Linux VMs to be notified of any issues.
