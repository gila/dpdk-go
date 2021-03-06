# Go bindings for [dpdk](http://dpdk.org/)

## Install dpdk and dpdk-go

- Setup `RTE_TARGET`, `RTE_SDK` and `DPDK_VERSION` in `hack/dpdk.rc`
- Install dpdk by `hack/dpdk-install.sh`
- Initial dpdk:
    - `source hack/dpdk-util.sh`
    - `init-dpdk`
- `go get -u github.com/feiskyer/dpdk-go`

Notes: If dpdk is installed inside a virtual machine, (e.g. VMWARE), then patch `hack/vmware.diff` must be applied before compling the dpdk source.

## Install dpdk-ovs

- First install dpdk
- Install ovs: `hack/ovs-install.sh`
- Start ovs with dpdk:
    - `source hack/dpdk-util.sh`
    - `init-dpdk`
    - `start-ovs`

## Sample Applications

### [Helloworld](http://dpdk.org/doc/guides/sample_app_ug/hello_world.html)

```
$ go get -u github.com/feiskyer/dpdk-go/samples/helloworld
$ helloworld -c3 -n1
```

### [skeleton](http://dpdk.org/doc/guides/sample_app_ug/skeleton.html)

A simple skeleton example of a forwarding application.

```
$ go get -u github.com/feiskyer/dpdk-go/samples/skeleton
$ skeleton -c3 -n1
```

### [Exception Path](http://dpdk.org/doc/guides/sample_app_ug/exception_path.html)

Reads packets from `dpdk port 0`, and then write the data to `tap_dpdk_00`:

```sh
$ go get -u github.com/feiskyer/dpdk-go/samples/exception-path
$ exception-path
```

Open another termial, and run 

```sh
$ tcpdump -nn -i tap_dpdk_00
```