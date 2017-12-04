# CCIE-Lab-Automation
## Version 1.9

Use this script to automate a CSR1000V deployment, primarily within a CCIE lab environment.

Built in python 2.7. The following are a few features currently available with this script:

- Basic configuration and in-band IP setup
   
- Baseline and hardening script configuration

- Scenarios configuration per INE's CCIE topology (Will introduce Micronics' labs into the mix soon)

- Configuration backups to an SCP server (A Raspberry Pi was used for testing)

- Install trial premium license for extra functionality i.e. Security and Data licenses (MPLS, IPSec)

**Prerequisites & Dependencies:**

* Python (Duh)

* Required libraries

  + Netmiko
	  
  + All other libraries come with python 2.7 natively
	   
  + TQDM (Used as a progress bar for tasks)
  
  + NAPALM (Used for the configure replace operations)

* SCP server for backups (Can modify for FTP)

* RADIUS or TACACS+ server for authentication (FreeRADIUS was used in testing on a Raspberry Pi)

**New in this release:**

- Initial attempts at multithreading functions (Currently supported for scenario configs and pulling BGP ASNs)

- Text variable files have been eliminated. All variables now go into the "device-vars.yml" file

**(Potential) Future Development:**

- TextFSM integration for data parsing

- Ansible integration for supplementary configuration management purposes

- Multithreading abilities for additional functions (Used to speed up the process of pulling data and pushing configurations)

- Consolidation of certain code to provide greater modularity

**Caveats:**

Baseline script formatting must have the following requirements for configure replace to take it properly:
	
- "Version 15.4" (Or the applicable version)
	
- "end" command
	
- Subcommands, such as those under "interface Gigx/x", must have a space in them to display hierarchy. Otherwise those lines
won't be added.

- ALL whitespaces should be filled with "!". In addition, it is advised against using a configuration with a banner
  in it during configure replace operations

Paths should be defined in the script to suit your needs. Things that may need to be changed in the script includes:
	
- SCP server IP
	
- SCP server path
	
- Router/Switch serial IPs and ports, and in-band IPs
	
- Path to your scenario/baseline/hardening configurations on the box running the script

**Community Input**

Any and all recommendations to make this script better are encouraged. If you're looking for a function to be added,
please ask! I am looking to improve this more, and having more than one person involved would be great! PRs are encouraged
as well, assuming they fit into the context.