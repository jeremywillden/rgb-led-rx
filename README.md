# rgb-led-rx
Raspberry Pi Pico PIO receiver for addressable RGB LED data streams

I built this to enable translation between different RGB LED string protocols.  It enables hardware-timed reception of WS2812 / Neopixel or other similar protocols so the data can be received, processed, stored, modified, or re-transmitted in a different format.

Watch the timing closely - the WS2812 protocol stops and displays the current result if a gap of 50 us occurs.  When translating between different protocols, if they have different bitrates, you will need to buffer the data to avoid creating gaps (when going from a lower-pixel-rate protocol to a higher-rate one) or to avoid losing data (when going from a higher-pixel-rate protocol to a lower one).  This is working well in an application to convert a 36-bit protocol to a 24-bit version, in which case I buffer an entire frame and emit it 100 us after the input data stop.
