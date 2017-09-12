# kvm-guest-drivers-windows

1.Compile balloon drivers. Drivers are generated in kvm-guest-drivers-windows/Balloon/Install.
  cd kvm-guest-drivers-windows/Balloon
  buildAll.bat

2.Self sign and install self signed drivers:
Installing Test-Signed Driver Packages
https://docs.microsoft.com/en-us/windows-hardware/drivers/install/installing-test-signed-driver-packages
How to Release-Sign File System Drivers
https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/signing-a-driver-for-public-release

3.Launch windows guest in qemu:
qemu -enable-kvm -m XXX -hda YYY.qcow2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4 -serial tcp:localhost:2345,server

4.Monitor reclaimed memory info with serial:
telnet localhost 2345

