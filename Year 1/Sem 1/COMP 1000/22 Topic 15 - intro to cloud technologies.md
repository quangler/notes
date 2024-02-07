cloud stuff auto updates, can change what is provided and how it is displayed

  

server: provides a resource or service

on prem model:

  

client > web server > application server > database server > database

|   |   |   |
|---|---|---|
|presentation tier|business tier|data tier|

  

you own all the stuff, but you take responsibility for it

  

cloud model:

|   |   |   |   |
|---|---|---|---|
|web server vm|application server vm|database server vm|sql server (data)|
|presentation tier|business tier|data|tier|

  

"cloud first"/"cloud native" - all stuff in the cloud

cloud people own all services and servers,

customers pay to use em, and they auto update

you are the one responsible for configuring cloud service and code

  

**SaaS** - software as a service - keep all software off servers

ex. office 365, google suite, discord

----------

makes the most money

all the apps on your computer are basically just pointers to web stuff

---------

this allows you to not have a ton of software on every computer, plus you only pay for what you use

---------

can only do so much with your apps, cant really customize stuff

  

**PaaS** - platform as a service - they own the stuff, give you basic apps but we gotta configure them

ex. AWS elastic compute and elastic beanstalk, app42 PaaS

---------

they offer you the computing power and storage capacity

---------

move all software off servers but want to be able to customize it

still only paying for what you use, never have to update

  

**IaaS** - infrastructure as a service - easy mode - everything is preset for you

ex. amazon web services (AWS), ms azure, google compute engine

----------

basically a giant packet tracer but in real life (over cloud)

still need to configure it, if you mess up the configuration its on you

  

Dropbox for Business:

you have admin permissions where you can restore backups to a higher detail than you would normally

have more features to work with than a normal user (the admins)

  

on prem > IaaS > PaaS > SaaS

  

from most admin/user responsibility to least

  

on prem: have to configure everything

IaaS: they control the physical servers

PaaS: you only control the apps and data

SaaS: you control nothing