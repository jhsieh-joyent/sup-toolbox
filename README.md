# Toolbox

Peter Gale's sourceable toolbox functions.

## Usage

```
[root@sup-ams1-jpc-notify0 ~]# source ~/toolbox/toolbox
Enter your JPC Headnode username: jdoe
SDC/JPC Toolbox - Version 4.3.3 - The Welshman (20161013)
```

## Docs
After sourcing run ```docs``` to see all the available commands:

```
[root@sup-ams1-jpc-notify0 ~]# docs
SDC/JPC Toolbox - Version 4.3.3 - The Welshman (20161013)
add_notify_roles :uuid or :email   -  Create the JPC-Notifications* roles for a user
add-key :uuid or :email            - Add an SSH key to an account for debugging
auth :zd_ticket :account_uuid      - Show if the ticket requester is authorised for the given account
auth_ip :zd_ticket [:IP]           - Show if the ticket requester is authorised for the IP (Omit IP to use IP on ticket)
auth_vm :zd_ticket :VM_UUID        - Show if the ticket requester is authorised for the given machine UUID
call_api :az :api :path :options   - generic api interface
capi :dc :path :options            - Call to capi
cn_res :dc :cn_uuid                - Free Ram. Disk and CPU per CN
cn_state :dc :hostname/:uuid       - Summary of CN and VM's state
cn_vms :dc :uuid                   - calls cnapi to list all the VM's for a CN
cn_vms2 :dc :hostname              - calls cnapi to list all the VM's for a CN
cnapi :dc :path :options           - Call to cnapi
count                              - Counts distinct values of the first field on the input stream
cust :uuid or :email               - Display the customer record of the last VM displayed by vm/vmi
cust_imgs :cust_uuid or :email     - List private images for a customer
cust_nets :uuid or :email          - List customers Networks in all DC's
cust_summary :uuid or :email       - Summary of a customers details and deployment
cust_vms :uuid or :email           - List customers VM's in all DC's
cust_vms2 :uuid or :email          - List customers VM's in all DC's (Show server and PI)
cvm                                - Redisplays the VM summary from the last call to vm/vmi. Job list is refreshed
designation :job_uuid              - Show why a provison landed on the CN
disabler :uuid/:email [NP]         - Disables a user. NP = appends '.nonpayment' instead of the default ('.disabled')
disku :dc :cn_uuid                 -
docs                               - Display the tools box documentation
email_search :email_address        - List accounts matching the email address. Accepets * as wild card
fail_vm :dc :uuid                  - Mark a VM that is stuck in provisioning as "failed"
find_ip :ip_address                - Finds the VM with the given IP Address
fingerprint_search :fingerprint    - Lists users with an ssh key matching the fingerprint
fp_search_active :fingerprint      - Lists users with an ssh key matching the fingerprint that are approved for provisioning
fp_vms :fingerprint                - list VMs for users who's ssh key matches the fingerprint
fraud [m] [N]                      -  List possible fraud VM's for this Month (m) or today and the previous N days
fvm :uuid                          - Find the VM across all DC's and call vm()
fwapi :dc :path :options           - Call to fwapi
img                                - Display details of the Image of the last VM displayed by vm/vmi
imgapi :dc :path :options          - Call to imgapi
imo :dc :vm_uuid                   - Show image origin of a VM
job_q :dc                          - List queued and running jobs
keys :uuid or :email               - List customers SSH keys
last_boot                          -  Tabular list of last boot times
limits :uuid or :email             - Display the provisioning limits for a user
ncra :job_uuid                     - Show why a provison returned "No Compute Resources Available"
notify_roles :uuid or :email       -  List the emails associated with the JPC-Notifications* roles for a user
pi [B]                             -  Tabular list of PI's running [or Booting]
pkg_list                           - Lists active packages in this DC
pkg_list_full                      - Lists ALL packages in this DC
risk :cust_uuid or :email          - print the account sign up risk analysis
sum                                - Sums the values of the second field on the input stream
svr                                - SSH to the CN of the last VM displayed by vm/vmi
tier :zd_ticket                    - Show Support tier and other Org data from ZD
to_zd :zd_ticket [t]               - Send stdin to a ZD ticket as a private comment in a code block. t = text not code
uuid :email_or_uuid                -  Converts an email to a uuid or just returns the uuid (or bails)
valid_dc :dc                       - Validates a dc name and switches - to _
ver                                - Display toolbox version
vm :dc :uuid [S][Q]                - Displays summary information for a VM. S = call svr(), Q = Quick, no job or FW stuff
vm_fw :dc :vm_uuid                 - List Firewall rules applicable to a VM
vm_key :List the keys and fingerprints in the metadata of a VM-
vmapi :dc :path :options           - Call to vmapi
vmi :ip_address                    - Calls find_ip to get UUID and then calls vm to display a VM summary
vmping                             - Ping the first IP of the last VM displayed by vm/vmi
vms_by_pkg :package                - Find VMS by package name.
wdjf :dc :job_uuid                 - Print bunyan parsed job error message showing low level failure details
workflow :dc :path :options        - Call to workflow
zd :zd_ticket                      - get email from ticket and push JPC Summary back to ticket
```


## Updating the toolbox

The official version of toolbox exists in Manta and is synced to this repo.
To update this repo follow these steps:

```
git clone git@github.com:joyent/sup-toolbox.git
cd sup-toolbox
mget -O /joyentsup/stor/TOOLS/toolbox
```

Review changes in the toolbox script using ``git diff`` so that you can create a commit message describing the recent changes then ``git add``, ``git commit``, and ``git push``.

```
git diff toolbox
git add toolbox
git commit -m "Synced from Manta: Replaced sdc-ldap/ufds with OpenLDAP client"
git push origin master
```
