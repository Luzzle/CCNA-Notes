#ccna-day13 #ccna-day14 #ccna-day15

IP addresses are assigned to companies by the IANA.

### CIDR
CIDR allows us to variably change the amount of bits assigned to host address space and thus reduces IP Address wastage. 

Represented by the form \[NETWORK ADDRESS\]/No. Leading 1 Bits in Subnet Mask

This applies to FLSM (Fixed Length Subnet Masks), meaning all subnets use the same prefix length.
### Subnetting CIDR
![[Pasted image 20250408111213.png]]

## Subnets for Class C networks
![[Pasted image 20250408062813.png]]

### Variable Length Subnet Masks (VLSM)
##### Overview
 VLSM is the process of creating subnets of different sizes, to make your use of network addresses more efficient.

##### Process
1. Assign the largest subnet at the start of the address space
2. Assign the second largest after it
3. Repeat the process until all subnets have been assigned

[Subnetting Questions - subnettingpractice.com](https://subnettingpractice.com/)