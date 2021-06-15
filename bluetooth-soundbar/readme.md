# Squeezebox-Soundbar
Portable Squeezebox player using a existing [bluetooth sound bar](https://www.ebay.com/itm/154052571509) and squeezelite-esp32.

Using an existing production bluetooth player is cost-effective alternative to buying speaker components (as a bonus it comes with a shiny case plus a battery and holder too!)

The current protoype uses a a1s audio kit.  The solution works well, is well supported by the squeezelite-esp32 dev team, but does required a pretty ugly add on box as the board is a little large.  The result is a promising solution, with half decent sound quality and suprisingly good battery life (using a 1500mAh battery)

Todo: 
- Look at a final solution with electronics that fit into the existing compartment (SqueezeAmp?)
- Replace the display module with a SPI/I2C module
- Investiage ways to extend battery life (especially in standby)

## Deconstruction
I resorted to brute force, a hack-saw, and dykes to get into the first unit!  In retrospect, the correct method is to peel back the right side of the display sticker to expose the 2 screws mounting the display module cover to the body extrusion.  Once removed the cover can be pulled out from under the end cap exposing 2 additional screws securing the end cap to the body extrusion.  With these screws removed, I am assuming the complete cap assembly (with the electronics and battery pack) would have come off as easily as the speaker end cap.




