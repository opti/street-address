![Gem Version](http://img.shields.io/gem/v/StreetAddress.svg)
![Build Status](https://circleci.com/gh/derrek/street-address.svg?style=shield)

#DESCRIPTION
  
Parses one line street addresses and returns a normalized address object.

This is a near direct port of the of the perl module 
Geo::StreetAddress::US originally written by Schuyler D. Erle. 

The port was from http://search.cpan.org/~sderle/Geo-StreetAddress-US-0.99/

Since the original port the two code bases have drifted somewhat. The most recent perl codebase is [here](https://github.com/timbunce/Geo-StreetAddress-US). Any help porting updates would be greatly appreciated.

## Installation

    gem install StreetAddress

then in your code

    require 'street_address'

or from Gemfile

    gem 'StreetAddress', :require => "street_address"

## Basic Usage

    require 'street_address'
    address = StreetAddress::US.parse("1600 Pennsylvania Ave, Washington, DC, 20500")
    address.street # Pennsylvania
    address.number # 1600
    address.postal_code # 20500
    address.city # Washington
    address.state # DC
    address.state_name # District of columbia
    address.street_type # Ave
    address.intersection? # false
    address.to_s # "1600 Pennsylvania Ave, Washington, DC 20500"
    address.to_s(:line1) # 1600 Pennsylvania Ave
    StreetAddress::US.parse("1600 Pennsylvania Ave") # nil not a full address

## Informal/Loose Parsing

    address = StreetAddress::US.parse("1600 Pennsylvania Avenue", :informal => true)
    address.number # 1600
    address.street # Pennsylvania
    address.street_type # Ave
    address.to_s # 1600 Pennsylvania Ave

## Zip+4

    address = StreetAddress::US.parse("5904 Richmond Hwy Ste 340 Alexandria VA 22303-1864")
    address.postal_code_ext # 1846
    address = StreetAddress::US.parse("5904 Richmond Hwy Ste 340 Alexandria VA 223031864")
    address.postal_code_ext # 1846

## License
The [MIT Licencse](http://opensource.org/licenses/MIT)

Copyright (c) 2007,2008,2009,2010,2011,2012,2013,2014 Derrek Long
