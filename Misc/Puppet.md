---
title: "Puppet"
---
**Puppet** is a deployment and configuration management toolset that provides you with enterprise tools that you need to automate an entire lifecycle on your Azure infrastructure.

The architectual components of Puppet are:
- Puppet Master
- Puppet Agent
- Console Services
- Facts

You can deploy Puppet on Azure using the **Puppet Enterprise** image from the Azure Marketplace.

When using Puppet, your files are named *Puppet Program failes*, or .pp files. Here's an example:

```Ruby
class mrpapp {
  class { 'configuremongodb': }
  class { 'configurejava': }
}

class configuremongodb {
  include wget
  class { 'mongodb': }->

  wget::fetch { 'mongorecords':
    source => 'https://raw.githubusercontent.com/Microsoft/PartsUnlimitedMRP/master/deploy/MongoRecords.js',
    destination => '/tmp/MongoRecords.js',
    timeout => 0,
  }->
  exec { 'insertrecords':
    command => 'mongo ordering /tmp/MongoRecords.js',
    path => '/usr/bin:/usr/sbin',
    unless => 'test -f /tmp/initcomplete'
  }->
  file { '/tmp/initcomplete':
    ensure => 'present',
  }
}

class configurejava {
  include apt
  $packages = ['openjdk-8-jdk', 'openjdk-8-jre']
  apt::ppa { 'ppa:openjdk-r/ppa': }->
  package { $packages:
    ensure => 'installed',

}
}
```

The Puppet Master component is responsible for compiling code and creating agent catalogs.
