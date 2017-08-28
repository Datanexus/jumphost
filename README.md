# jumphost
community jumphost release
## configuration
If any pairs don't apply, comment them out.
### aws
Certain _key:value_ pairs can be configured per project. Others should remain fixed for all projects.

These values should remain unchanged.

    cloud: aws
Replace TENANT with the name of the AWS_PROFILE environment variable. 
    
    tenant: TENANT
Replace PROJECT_NAME with the name of the project hosting the instances. 

    project: PROJECT_NAME
Replace DOMAIN with a `production` or `development` (or another value of your choosing).

    domain: DOMAIN
These values should remain unchanged.
    
    application: jumphost
Replace REGION with your desired AWS region such as `us-east-1` or `ap-southeast-2`.

    region: REGION    
Replace COUNT with the number of systems to instantiate.

    count: COUNT
Replace USER with `centos` for CentOS or `redhat` for RHEL.

    user: USER
Replace AMI with the AMI ID in the region you wish to deploy; Centos 7.3 or RHEL 7.3 are supported. If commented out or removed, CentOS 7.3 will be booted.

    image: AMI
Replace SIZE with  `t2.micro`, `t2.small`, `t2.medium`, `t2.large`, `t2.xlarge`, `t2.x2large`,  or another value from [here](https://aws.amazon.com/ec2/instance-types/).

    type: SIZE
Replace SIZE with the size of the root volume in GB, e.g, `20` for 20gig or `2000` for 2TB. `11` is a reasonable value for the root volume.

    root_volume: SIZE
Replace CIDR_BLOCK and SUBNET with the values in the VPC, e.g., 172.31.0.0/16, 172.31.1.0/24, 172.31.2.0/24. The internal subnet is private and non-routable, the external subnet will outbound routing.
    
    cidr_block: CIDR
    internal_subnet: SUBNET
    external_subnet: SUBNET
(if needed) Replace  PROXY with `yes` or `no` if there is an HTTP proxy involved in getting to the internet.
 
    http_proxy: PROXY
(if needed) Replace USER, PASSWORD, DOMAIN, PORT with the necessary values.
    
    http_proxy_url: http://USER:PASSWORD@DOMAIN:PORT

### osp
Certain _key:value_ pairs can be configured per project. Others should remain fixed for all projects.

These values should remain unchanged.

    cloud: osp
Replace TENANT with the name of the configure OSP tenant. 

    tenant: TENANT
Replace PROJECT_NAME with the name of the project hosting the instances. 
    
    project: PROJECT
Replace DOMAIN with a `production` or `development` (or another value of your choosing).

    domain: DOMAIN
These values should remain unchanged.

    application: jumphost
Replace REGION with your configured OSP region.

    region: OSP_REGION
Replace COUNT with the number of systems to instantiate.

    count: count
Replace USER with `centos` for CentOS or `redhat` for RHEL.

    user: USER
Replace IMAGE_UUID with the UUID of the image you wish to boot.

    image: IMAGE_UUID
Replace TYPE with configured virtual machine size.

    type: TYPE
Replace SIZE with the size of the root volume in GB, e.g, `20` for 20gig or `2000` for 2TB. `11` is a reasonable value for the root volume. If booting from an image, this is ignored.

    root_volume: SIZE
Replace  SUBNET with the configured values, e.g., 172.31.1.0/24, 172.31.2.0/24. The internal subnet is private and non-routable, the external subnet will outbound routing.
    
    internal_subnet: SUBNET
    external_subnet: SUBNET
Replace  FLOAT with the floating IP pool, e.g., external. 
    
    float_pool: FLOAT
Replace SUBNET_UUID with the UUID's of the internal and external subnets.

    internal_uuid: SUBNET_UUID
    external_uuid: SUBNET_UUID
Replace ZONE with the configured OSP zone.

    zone: ZONE 
(if needed) Replace USER, PASSWORD, DOMAIN, PORT with the necessary values.

    http_proxy: yes
(if needed) Replace USER, PASSWORD, DOMAIN, PORT with the necessary values.
    
    http_proxy_url: http://USER:PASSWORD@DOMAIN:PORT
    
## deployment
### amazon web services
To deploy on AWS:

    ./deploy aws

Expected running time is approximately 3 minutes 

### openstack
To deploy on OSP:
  
    ./deploy osp

Expected running time is approximately 3 minutes.

## testing
If the `deploy` code ran without errors, that's a pretty good indicator of a successful deployment. However, you can run the following to be sure.

### all clouds
To test the deployment, simply connect to the jumphost:

    ssh dn_jumphost
        
### expected results
You should get a shell prompt on the jumphost.

    Last login: Mon Aug 28 19:29:19 2017 from 121-195-24-147.dhcp.nc.charter.com
    [centos@jumphost-1619e612b02e482b8575021802c908e1 ~]$
