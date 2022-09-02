# FortiGate Default Configuration repository

## Introduction

In one of my previous projects, I needed to compare the default configuration of a FortiGate with its current one in order to identify quickly what were the changes made on the FortiGate.
Since I add about 100 FortiGate to compare directly from a FortiManager with multiple models and different version, I wanted a quick way to get all the default configuration of the ForitGate depending on the model and major release.

In this process, I tried to "reverse engineer" the OVA file of the FortiManager expecting to find something interesting, and it was the case.

After extracting all the files from the FortiManager's OVA, you can decompress the file `syntax.tar.xz` and just search for all default configuration of FortiGate and FortiProxy under the directory `sysconfdef`.

## How it works

Each directory is containing default configuration of all supported FortiGate based on the major release :
- 200 : 2.0.x, used for the FortiProxy
- 600 : 6.0.x
- 620 : 6.2.x
- 640 : 6.4.x
- 700 : 7.0.x

Most of the models, either physical and VM, have multiple files associated for the different modes availables :
- *.def : Default "NAT" mode of a FortiGate
- *.nat.def : No idea yet
- *.split_vdom_root.def : Configuration of the root VDOM in a [split-task VDOM mode](https://community.fortinet.com/t5/FortiGate/Technical-Tip-Configuring-split-task-VDOM-mode-With-Fortinet/ta-p/193495?externalId=FD48617)
- *.split_vdom_traffic.net.def : Configuration of the traffic VDOM in [split-task VDOM mode](https://community.fortinet.com/t5/FortiGate/Technical-Tip-Configuring-split-task-VDOM-mode-With-Fortinet/ta-p/193495?externalId=FD48617) using NAT VDOM mode
- *.split_vdom_traffic.tp.def : Configuration of the traffic VDOM in [split-task VDOM mode](https://community.fortinet.com/t5/FortiGate/Technical-Tip-Configuring-split-task-VDOM-mode-With-Fortinet/ta-p/193495?externalId=FD48617) using transparent mode
- *.tp.def : No idea yet
- *.trans.def : FortiGate using [`transparent mode`](https://community.fortinet.com/t5/FortiGate/Technical-Note-Configure-a-FortiGate-unit-in-Transparent-mode/ta-p/194458)


## Usage

There is nothing specific to do in order to use it. You can either grab a file or the whole directory and use it in another tool.

I don't plan to update it often, maybe once per major release.
