# gigabyte-a520m-s2h-hackintosh-opencore-efi
<img src="https://github.com/jjone/gigabyte-a520m-s2h-hackintosh-opencore-efi/blob/main/thumbnail_2023-03-18_15-48-47.jpg?raw=true"><br />
<H1>macOS Ventura 13.2.1 Hackintosh </H1>


<b>Gigabyte A520M S2H (rev. 1.x) Motherboard with Bios F16a</b> <br />
AMD Ryzen 7 2700X<br />
Radeon RX 560 2GB-  native support<br />
16GB DDR4 2400 Memory<br />
1TB WD SN570 NVME hard drive-  native support<br />
FENVI WIFI/BT PCIe card-  native support<br />
<br />



Bios Setting: <b>Disable these</b> 
1. Serial Port
2. Wake by RTC 
3. Above 4G Decoding
4. SATA/NVME Raid
5. SATA Hot Plug / Hot Swap
6. SATA Aggressive Link Power Management
7. CSM
8. Secure Boot
9. Fast Boot

Bios Setting: <b>Enable these</b> 
1. Wake on Keyboard
2. Wake on Mouse (two clicks)
3. Wake on Lan
<br /><br />

<b>ATTENTION: AMD Ryzen CPU physical cores number: </b>, https://github.com/AMD-OSX/AMD_Vanilla<br />
Find the four (algrey - Force cpuid_cores_per_package in Config.plist) patches and alter the Replace value only.

<table>
<thead>
<tr>
<th>macOS Version</th>
<th>Replace Value</th>
<th>New Value</th>
</tr>
</thead>
<tbody>
<tr>
<td>10.13.x, 10.14.x</td>
<td>B8000000 0000</td>
<td>B8 &lt; Core Count &gt; 0000 0000</td>
</tr>
<tr>
<td>10.15.x, 11.x</td>
<td>BA000000 0000</td>
<td>BA &lt; Core Count &gt; 0000 0000</td>
</tr>
<tr>
<td>12.x, 13.0 to 13.2.1</td>
<td>BA000000 0090</td>
<td>BA &lt; Core Count &gt; 0000 0090</td>
</tr>
<tr>
<td>13.3</td>
<td>BA000000 00</td>
<td>BA &lt; Core Count &gt; 0000 00</td>
</tr>
</tbody>
</table>

AMD Ryzen 2700x has 8 physical cores, in EFI Config.plist,<br />
I have these for my CPU, Please find your CPU cores and modify the values <br />
B8<b>08</b>0000 0000<br />
BA<b>08</b>0000 0000<br />
BA<b>08</b>0000 0090<br />
BA<b>08</b>0000 00<br />

<br /><br /><b>Working: everything plus,</b>
DSDT patched for sleep/wake  - fix instant wake due to GPP0 GPP8.
Sleep/Wake fully working. 
<br />("Find My" App wakes up. Also press any key/power button will wake up from sleep:)
<br /><br />! Remember to remove the boot-args "-v" in Config.plist after installation.
<br /><br /><br />
Read this guide, https://dortania.github.io/OpenCore-Install-Guide/<br />
and check https://reddit.com/r/hackintosh/<br />
generate SMBIOS, https://github.com/corpnewt/GenSMBIOS<br />
