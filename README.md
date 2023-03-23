# nixos-addblock-hosts
A nixos configuration file that you can import from configuration.nix to block common ad/tracker hosts

Option 1

Download <code>tejas-hosts.nix</code> to <code>/etc/nixos/tejas-hosts.nix</code> and add it as import to your <code>/etc/nixos/configuration.nix</code> like this (example):

```nix
# Edit this configuration file to define what should be installed on
# your system.  Help is available in the configuration.nix(5) man page
# and in the NixOS manual (accessible by running ‘nixos-help’).

{ config, pkgs, ... }:

{
  imports =
    [ # Include the results of the hardware scan.
      ./hardware-configuration.nix
      ./tejas-hosts.nix
    ];

```

Option 2
Inspired from Steve Black says in his repo add the following line to your configuration.nix

```nix
{
  networking.extraHosts = let
    hostsPath = https://raw.githubusercontent.com/tejasjyothishetty/nixos-addblock-hosts/master/hosts;
    hostsFile = builtins.fetchurl hostsPath;
  in builtins.readFile "${hostsFile}";
}
```


Also note this comment from the top of the original <code>hosts</code> file:

<pre>
# This hosts file is brought to you by Dan Pollock and can be found at
# http://someonewhocares.org/hosts/
# You are free to copy and distribute this file for non-commercial uses,
# as long the original URL and attribution is included. 
</pre>

#### waste
https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts;

https://github.com/tejasjyothishetty/nixos-addblock-hosts/blob/master/tejas-hosts.nix
