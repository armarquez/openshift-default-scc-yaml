# Openshift Default Security Context Constraints (SCC) Object YAML files

**NOTE: THIS IS STILL A WORK IN PROGRESS AS I STILL TRANSLATING ANNONATIONS. PLEASE DO NOT USE THIS IN PRODUCTION OR SENSITIVE SYSTEMS.**

YAML files that create Pod Security Policy objects that are based upon the default SCC objects for an OpenShift installation.

## SCC Descriptions

Below are the official descriptions for each SCC object.

### anyuid

`anyuid` provides all features of the restricted SCC but allows users to run with any UID and any GID.

#### hostaccess

`hostaccess` allows access to all host namespaces but still requires pods to be run with a UID and SELinux context that are allocated to the namespace. WARNING: this SCC allows host access to namespaces, file systems, and PIDS.  It should only be used by trusted pods.  Grant with caution.

#### hostmount-anyuid

`hostmount-anyuid` provides all the features of the restricted SCC but allows host mounts and any UID by a pod.  This is primarily used by the persistent volume recycler. WARNING: this SCC allows host file system access as any UID, including UID 0.  Grant with caution.

#### hostnetwork

`hostnetwork` allows using host networking and host ports but still requires pods to be run with a UID and SELinux context that are allocated to the namespace.

#### nonroot

`nonroot` provides all features of the restricted SCC but allows users to run with any non-root UID.  The user must specify the UID or it must be specified on the by the manifest of the container runtime.

#### privileged

`privileged` allows access to all privileged and host features and the ability to run as any user, any group, any fsGroup, and with any SELinux context.  WARNING: this is the most relaxed SCC and should be used only for cluster administration. Grant with caution.

#### restricted

`restricted` denies access to all host features and requires pods to be run with a UID, and SELinux context that are allocated to the namespace.  This is the most restrictive SCC and it is used by default for authenticated users

## Similar References

[Kubernetes Security - Best Practice Guide](https://github.com/freach/kubernetes-security-best-practice/blob/master/PSP/default-non-apparmor.psp.yaml)