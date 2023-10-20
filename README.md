# Hello World!

This example project shows you how to load background tiles into memory on the NES using 6502 assembly language. There's an accompanying video on [YouTube]. (https://www.youtube.com/watch?v=CyxznT1JgBghttps:/)

Some clarification around the world.bin file. The world.bin file format is literally just raw data to be loaded into the NES nametable. If you were to look at it in a hex editor, you'd see the following:

![Hex editor view of data.](https://i.imgur.com/CkUXoDQ.png "Hex editor view")

Notice the little block of characters on the right in the form of a rectangle (EESTEE / GGUVGG). These visually resemble the floating blocks because that's what they represent. The letters are ASCII equivalents of the more important hex-values that you see on th left (0x45, 0x45, 0x53, etc). If you look at the tiles when you load the ROM In the emulator, you'll see that highlighting the brick tile shows you $45 as the tile value:

![Image tiles.](https://i.imgur.com/sSdCHKQ.png "Image tiles, 45 hex")

This is where the value comes from. Depending on how your CHR data is loaded, the background tiles will have a specific tile index that you reference in your background data. In order to change the tiles in this code, you can directly modify the data in the first 960 bytes of the file to update your background. The remaining 64 bytes in the file (```$B4, $B5```) are used to configure the palettes (the nametable attributes) used by the background tiles. In this case, we're not doing anything dynamic with the backgrounds, so I've just hard-coded them all to use the values we need to show the background with the proper colors.
