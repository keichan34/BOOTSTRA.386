<pre>
     ____  ____  ____  _____________________  ___    ____        __   _____ ____  _____
    / __ )/ __ \/ __ \/_  __/ ___/_  __/ __ \/   |  / __ \     _/_/  |__  /( __ )/ ___/
   / __  / / / / / / / / /  \__ \ / / / /_/ / /| | / /_/ /   _/_/     /_ &lt;/ __  / __ \ 
  / /_/ / /_/ / /_/ / / /  ___/ // / / _, _/ ___ |/ ____/  _/_/     ___/ / /_/ / /_/ / 
 /_____/\____/\____/ /_/  /____//_/ /_/ |_/_/  |_/_/      /_/      /____/\____/\____/  

      The Definitive All-in-one Graphical Tool-Kit for Micros and Terminals.  
 - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

  There's a lot of micros and a lot of        this future has arrived.
  graphics modes. Today there's CGA,          
  Hercules, MDA, and EGA. And that's only     Use primitives like buttons, "toolbars"
  on the IBM-PC.                              and various "widgets" that will control
                                              your application. We handle rendering
  What about Tandy, CDC, Honeywell,           these abstractions on screen for you.
  DEC, and Zenith? That's a different          
  problem. How about the portables on         Think of your software in terms of
  tomorrows' horizon? Plan to ignore the      Windows, Icons, Menus, and Pull-Downs.
  Compaq-1? Your customers won't.             Even a WIMP can do it (TM).
                                              
  Such incompatibilities shouldn't be         That's the new paradigm of full-screen
  your concern. You focus on making           interactive applications. Give your
  great microcomputer applications. We        customers the rich interface that are
  focus on making your application work       easy to use and also, easy to create.
  on tomorrow's computer.                     Give yourself that one-leg up on your
                                              competition. GUI is Good. GUI is God.
  It's called a "Graphical User Interface"    
  They've been in development for years       Just look at how beautiful
  at places like XEROX Parc in Palo Alto      your application can look with
  and Carnegie Mellon. And now, finally       BOOTSTRAP/386:

</pre>

<img src=http://i.imgur.com/CZKrANV.png>

## Less sarcastic introduction

Bootstrap/386 is a [Twitter bootstrap](http://twitter.github.io/bootstrap/) theme intended to make
webpages look like they are from the 80s.  Here's a few things that are utilized to get it there:

### EGA-16 color palette

This color palette was available on color terminals as far as back as the IBM XT and AT. It was known
as the 16 color EGA palette.  These 16 colors were available for character mode graphics on CGA cards
and for raster graphics on EGA.  CGA couldn't fully-rasterize all the 16 colors because of the graphics
memory (which was a premium back then) needed. (more about that below).

The resolution at the time was nominally 640x350 pixels. Each character was 8 pixels across and 14 pixels tall.
This gave the classic 80x25 character resolution of the terminals at the time (in DOS known as mode CO25).  For
CGA, the resolution was 640x200 and the character was 8x8 pixels - giving a 1:2.4 pixel aspect ratio since the
pixels here weren't squares.

<q>
<b>Why weren't they squares?</b>
The monitors themselves were 4:3.  Across this was 640 pixels and top to bottom it was 200.  Pretend you had a 15 inch
monitor.  This means that the hypotenuese is 15 inches.  We can use the pythagorean theorem here:

    (4x)^2 + (3x)^2 = 15^2 ... x = 3

This means that horizontally you had 12 inches viewable and vertically you had 9.  Now,

    640 / 12 = horizontal dpi = 53.3
    200 / 9 = vertical dpi = 22.2

    53.3 / 22.2 =~ 2.4

So our "8x8" actually produced a tall character.  In the EGA world, things were a bit different since we had a 640x350 resolution.
Using the same math from above:

    640 / 12 = horizontal dpi = 53.3
    350 / 9 = vertical dpi = 38.8

    53.3 / 38.8 =~ 1.37

Now remember, we have a 14x8 character resolution for ega, so let's throw that back in

    1.37 * (14 / 8) =~ 2.4

And there we go.  This is why CGA and EGA 16 text graphics look relatively similar. It's because they fit
the same characters on the screen, in the same proportion to the eye, by utilizing different rasterized fonts.
</q>

Each character additionally had a foreground and a background color. This means that video memory cost was at least

    80 rows * 25 columns * 1 byte per character (MSDOS supported 8-bit extended ASCII, see below) * 4/8 bits FG * 3/8 bits BG * 1/8 bits "style"
    80 * 25 * 2 = 4000 bytes.

Standard EGA was 16kB which means that there were 4 pages.

#### The colors themselves

EGA is technically a 64 bit palette, but the 16 'default' colors are what made it famous.  The logic here is that each of the 4 bits were for
one of the channels

  * Bit 0 - brightness
  * Bit 1 - red
  * Bit 2 - green
  * Bit 3 - blue

So this means that 1100 (color 12) is a bright red. You can see the [colors here](http://en.wikipedia.org/wiki/Enhanced_Graphics_Adapter#Color_palette).

For all intents and purposes, the background color was always dark.
