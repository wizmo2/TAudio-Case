# Squeezebox-Soundbar
Portable Squeezebox player using a bluetooth sound bar and a1S audio kit board


This project was looking at a low cost solution for a portable head-less squeezebox player.  Using an existing production bluetooth player is cost-effective alternative to buying speaker box components (as a bonus it came iwht a decent battery and holder too!)

The current solution uses a a1s audio kit.  It works well but required a pretty ugly add on box.  The result is a promising solution, with decent sound quality and suprisingly good battery life (using a 1500mAh battery)

The idea would be to use smaller components (possibly a SqueezeAmp) to fit into the existing compartment.  In theory, the display can be replaced with a supported I2C/SPI version.

## Deconstruction
I resorted to brute force, a hack-saw, and cutters to get into the first unit.  

In retrospect(!), the correct method is to peel back the right side of the display sticker to access 2 screws mounting the display module cover to the main extrusion.  If these are removed, you may beable to pry open the other side to access the left screws.  Once these are removed, I am assuming the cap with the electronics assembly would come off as easily as the speaker end cap.

