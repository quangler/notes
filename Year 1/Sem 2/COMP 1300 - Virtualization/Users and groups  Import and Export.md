**User Management**

authentication and authorization govern access

vCenter SSO (single sign on) supports authentication which means it allows user access to vSphere components

each user must be authorized to view or manipulate vSphere objects

  

initial sign on is through vCenter SSO domain (administrator@vsphere.local)

- add identity source > which users and groups are defined to vCenter SSO
- give privs to a user or group by selecting an object and assign a role for the user or group

  

**Import and Export**

- import through Open Virtual Format (OVF)
- export into .OVF files
- Open Virtual Appliance (OVA) - works in vSphere versions older than 6.5

  

Exporting an OVF template:

- vm > actions > template> export OVF template (MAKE SURE VM IS TURNED OFF)
- enter in name and or description

  

Deploying an OVF template:

- right click server > right click > deploy OVF template
- select OVF template
- name and folder, unique name, easy