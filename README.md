# BK7231 GUI Flash Tool

BK7231 GUI Flash Tool a simple Windows Application that allows you to flash new firmware to BK7231T/BK7231N devices without having computer and programming knowledge.
Futhermore, it automatically creates an original firmware backup, so you can submit the original firmware dump for futher analysis (NOTE: it may contain SSID if paired).

# Short usage instruction

Connect UART to USB converter to Beken TXD1/RXD1, start flasher tool, select N or T platform, click "Download latest from web" to get firmware binary, click "Do backup and flash new", reset/repower Beken, tool will do both read and flash in one row. Done!

No command line and no strange arguments required.

# Detailed usage instruction

1. Download and unpack executable from Releases tab on the right
2. Prepare flashing circuit for BK7231 (both T and N)
2.1 get USB to UART converter with 3.3V voltage signals
2.2 connecte RX to TXD1 of Beken, TX to RXD1 of Beken
2.3 you may also need to solder a wire to CEN signal, more about that later
2.4 of course, you also need to power device from some reliable power supply, Beken runs on 3.3V, do not try hacking devices connected to mains!
3. Open our flasher:

![image](https://user-images.githubusercontent.com/85486843/210281085-6141160b-df6d-486c-b574-ef784f5cbd56.png)

4. Select proper platform - BK7231T or BK7231N
5. Select your COM port of USB to UART converter
6. Click "Download latest from Web" to get proper binary file
7. Wait for download to finish

![image](https://user-images.githubusercontent.com/85486843/210281125-a3e25ab2-3144-4e02-a30c-6e135ecefd24.png)

8. Close download window
9. Click "Backup and flash new"
10. When the log window is waiting for "Getting bus", do a device reboot. You can do this in two ways, choose one:
  Option A: short CEN to GND for 0.25s (it is tricky to get this right, requires precise timing)
  Option B: power off and on device (of course, it should not be connected to mains, use your own safe 3.3V power supply that can supply enough current)
  
![image](https://user-images.githubusercontent.com/85486843/210281194-27decf09-723e-41f7-8b47-6fe2b6bb4857.png)

11. It will begin reading (it does first backup, then write)

![image](https://user-images.githubusercontent.com/85486843/210281251-cd69ddab-f0ab-4389-8476-0eb33045aa76.png)

12. After reading, it will start the new firmware erase

![image](https://user-images.githubusercontent.com/85486843/210281467-10129860-61da-4420-a9aa-9910f0e57099.png)

13. And then, automatically, write:

![image](https://user-images.githubusercontent.com/85486843/210281482-0eb62054-f44e-4c10-959a-65f4147cefca.png)

14. Done:

![image](https://user-images.githubusercontent.com/85486843/210281504-b592db7d-9e6e-47f9-81fc-3619a2f00204.png)

15. Firmware access point show appear now. Connect to it and enter 192.168.4.1 configuration page.
16. Remember that saved firmware backup is in the "backups" dir

# CRC Mismatch?
CRCs are calculated correctly for both N and T. If you get CRC mismatch, you are most likely selecting a wrong chip type.
![image](https://user-images.githubusercontent.com/85486843/210281290-31d037f5-61c1-403b-a9c5-891fbda75914.png)

# Can't auto download firmware?
Firmware download will not work on systems without newer TLS version required by Github. You can always manually download release from here:
https://github.com/openshwprojects/OpenBK7231T_App
and put into firmwares bin, then restart flasher.


# Other problems?
You can also try changing the baudrate for flashing. Remember - sometimes higher baud rate might worker better than lower one!

If you still need help, you can ask on our forums: https://www.elektroda.com/
