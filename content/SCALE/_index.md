---
title: "TrueNAS SCALE"
geekdocCollapseSection: true
weight: 20
aliases:
  - /scale/devnotes/
  - /scale/introduction/
---
<p style="text-align:center;">
<img src="/images/truenas_scale-logo-full-color-rgb.png" style="width:50%;">
</p>

**TrueNAS SCALE** is the latest member of the TrueNAS family and provides Open Source HyperConverged Infrastructure (HCI) including Linux containers and VMs.
TrueNAS SCALE includes the ability to cluster systems and provide scale-out storage with capacities of up to hundreds of Petabytes.
Just like TrueNAS CORE, TrueNAS SCALE is designed to be the most secure and efficient solution to managing and sharing data over a network, from smaller home networks "scaled" up to massive business environments.

The Linux base of SCALE allows for a similar, but slightly different feature set that will appeal to an audience that is more familiar with Linux applications and workflows while TrueNAS CORE continues to provide the known and heavily tested performance and features from the FreeBSD operating system.
SCALE is an acronym that represents the core features of the software:

<ul style="list-style: none;">
	<li><b>S</b>caled-Out ZFS</li>
	<li><b>C</b>onverged</li>
	<li><b>A</b>ctive-Active</li>
	<li><b>L</b>inux Containers</li>
	<li><b>E</b>asy to Manage</li>
</ul>

Unlike other HCI platforms, a user can get started with TrueNAS SCALE on a single node and incrementally scale up and scale out to over 100 storage nodes with many additional compute-only nodes.
TrueNAS SCALE is true Disaggregated HCI, meaning storage and compute can be scaled independently.
Each node can support Virtual Machines (with the KVM hypervisor) as well as Docker containers by using native Kubernetes.

{{< tabs "SCALE Features" >}}
{{< tab "Open Source" >}}
Free to download and use, TrueNAS SCALE welcomes developers and testers to contribute to its Open Source development model.
{{< /tab >}}
{{< tab "Scale-Out" >}}
OpenZFS and Gluster combine to enable scale-out ZFS capabilities with excellent stability and very efficient compression and snapshots.
{{< /tab >}}
{{< tab "Hyperconverged" >}}
Deploy a single hyperconverged node in a home/office or a cluster with hundreds of compute and storage nodes in a datacenter.
{{< /tab >}}
{{< tab "Virtualization" >}}

With support for KVM VMs, Kubernetes, and Docker containers, it’s easy to add applications to suit your every need.
{{< /tab >}}
{{< /tabs >}}

## Documentation Sections

{{< include file="/_includes/SCALEDocsSections.md" type="page" >}}

{{< include file="static/includes/General/MenuNav.md.part" markdown="true" >}}
