# Linux Mirrors

## Cronjobs/
Contains the Kubernetes CronJobs to update the mirror source via rsync, using a custom image that will be in containers/eventually

## Mirror-Rsync
Provides the RSync Daemon Server

## Mirror-Web
Provides PVC, Ingress, SVC, Pod per Mirror.

Doing a pod per mirror was chosen to make doing stats via loki logs easier. Using a slightly custom image of NGINX w/Amplify, and autoindex turned on, and a JSON Log format for ingest into Loki

## Misc.

- Mirror-PVC.yaml
  - Provides a single PVC used by Ubuntu & EPEL together, since its stored on a seperate storage class due to my flash-ceph cluster being full.
- Network-Policy.yaml
  - Restricts the pods to only allow inbound from traefik, and outbound to amplify + kube-dns