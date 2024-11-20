1. Download this firmware  
[github.com/foostan/kbd_firmware/raw/main/keyboards/crkbd/vial-kb/vial-qm...](https://github.com/foostan/kbd_firmware/raw/main/keyboards/crkbd/vial-kb/vial-qmk/.build/crkbd_rev4_0_standard_vial.uf2)  
2. Unplug keyboard  
3. Unplug audio cable  
4. While holding down Q (top row, second column from left), plug in left keyboard with USB C cable. Do not plug audio cable back in while you do this.  
5. In Finder, you should find RPI-RP2 appear in Locations section from sidebar. Drag and drop UF2 file you have downloaded into this location. This will flash the keyboard with the new firmware.  
6. Unplug left keyboard.  
7. Do the same for right keyboard. Plug it in with USB C cable while holding down P key (top row, second column from right), then flash it with same firmware.  
8. Unplug right keyboard.  
9. Now plug audio cable between the two keyboard halves, and then plug USB C cable into left keyboard.  
10. Your keyboard hopefully should have the issue resolved. If not, please let me know, and we will look into this issue further.