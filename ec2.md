# EC2 - Elastic Compute Cloud #

VMs in the cloud! Various types of instance classifications optimized for certain
tasks.

## Pricing ##

* On Demand
    * no upfront costs or commitments
    * pay as you go.
    * Linux - $/second
    * Other - $/hour
* Reserved
    * 1-3 year contract
    * variable discount depending on upfront payment
* Spot
    * Bid on instance capacity.
    * Prices fluctuate ( like stock market ).
* Dedicated
    * Physical EC2 instance, single-tenant host

## Use Scenarios ##

| On Demand |Reserved|Spot|Dedicated Host|
|-----------|--------|----|--------------|
|No commitment|Steady State, predictable use|Flexible start and stop|Regulatory requirements|
|Short-term work that cannot be interrupted|Long term contract|Very low pricing|Licensing|
|First time or experimental||Huge amounts of computer power for low price|Can be on-demand or reserved|

## Instance Types ##

Below is a mnemonic device to remember the intended use for each instance type. Instances have a letter and number ( e.g t2 ) that represents its classification and generation respectively. **Note:** The letters don't actually abbreviate the right-hand side of the mnemonic.

F - FPGA ( Field Programmable Gate Array )

I - IOPS ( Input Output Per Second )

G - Graphics

H - High disk throughput

T - Tiny ( general purpose, lowest cost )

D - Density

R - RAM

M - Main ( general purpose )

C - Compute

P - Pixels ( think graphics )

X - XTREME Memory optimization

## EBS Volumes ##

Virtual disk storage on an EC2 instance. Automatically replicated in ***same*** Availability Zone.

## Volume Types ##

* GP2 ( General Purpose )
    * Cost effective at < 10k IOPS
* Provisioned
    * I/O intensive ( >10k IOPS )
* ST1
    * Throughput optimized
    * **Cannot be boot volume**
* SC1
    * Infrequent access
    * Lowest cost
    * **Cannot be boot volume**
* Magnetic
    * Lowest cost ***bootable***
    * ***Legacy***
