# EC2 - Elastic Compute Cloud #

VMs in the cloud! Various types of instance classifications optimized for certain
tasks.

## Pricing ##

* On Demand: no upfront costs or commitments, pay as you go.
    * Linux - $/second
    * Other - $/hour
* Reserved: 1-3 year contract, variable discount depending on upfront payment
* Spot: Bid on instance capacity. Prices fluctuate ( like stock market ).
* Dedicated: Physical EC2 instance, single-tenant host

## Use Scenarios ##

| On Demand |Reserved|Spot|
|-----------|--------|----|
|No commitment|Steady State, predictable use|
|Short-term work that cannot be interrupted|Long term contract|
|First time or experimental|
