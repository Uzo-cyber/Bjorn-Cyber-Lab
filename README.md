# Bjorn-Cyber-Lab
Implementation and troubleshooting of an autonomous Raspberry Pi security tool (Bjorn) in a virtualized lab environment
Challenges & Problem Solving
Challenge 1: Virtualization & Network Routing Conflicts

Issue: The Kali Linux VM and Docker containers were using internal network bridges that shadowed the physical network, preventing the Bjorn (Raspberry Pi) from "seeing" the targets.

Solution: Reconfigured the VirtualBox Network Adapter to Bridged Mode and adjusted the ip route settings to ensure all lab components were on the 192.168.0.x subnet.

Challenge 2: GPIO Hardware Contention

Issue: The Bjorn service failed to initialize due to a lgpio: GPIO busy error, caused by the software attempting to drive a non-existent e-Paper display.

Solution: Conducted a root-cause analysis of the Python Traceback, identified the conflict in shared.py, and manually patched the source code to bypass the hardware initialization. This allowed the web-based console to function without the physical display.
