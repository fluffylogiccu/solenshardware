# Changelog and Notes

## SOLENS rev. A (first PCB)

#### Rev. A PCB/schematic issues


* Power LED on wrong side of R400/R403, power LED should illuminate when 3V3 buck is on, regardless of rest of board. (done)
* TP\_TINY footprint has paste mask and shouldn't (fixed)
    * TP202 got paste
    * TP500 got paste
    * TP501 got paste
* 0402 footprints need a slight change of shape, pads should be slightly closer together and enlarged slightly (fixed)
    * This should fix the few tombstoned capacitors
    * Pad size was: 0.8 mm (X) x 0.6 mil (Y)
* Fuel gauge footprint (DFN) needs larger pads (more paste volume) for better reflow (fixed)
    * Pad size was: 0.25 mm (X) x 0.7 mm (Y)
* Fuel gauge is mis-wired, only senses current _into_ battery. (fixed)
* SDRAM data (DQ*) termination is listed as 49R9, should be 33R per Hyperlynx sims (fixed)
* Slight undershoot issue on camera parallel interface (need scope captures to document)
    * Add termination arrays on all camera interface lines, value unknown (need to rework SJ* on bus before value decision)
    * SJ replaced by termination, 33R determined as suitable termination value (done)
* LT3652 charging circuit had regulation issues (bad/damaged chip?)
* XCLK termination (R602) is on the wrong end of the line, need to be near MCU (fixed)

#### Rev. A assembly issues

* U203 pin 1 looks unconnected
* U203 most pads have poor fillets
* C504 east pad cold
* C503 west pad cold
* C109 west pad cold
* U100 pin 124 poor fillet
* J102 poor alignment

#### Rev. A wishlist

* Use stainless steel stencil instead of polyimide
* Shrink inductor sizes (done)
* Move components to back, particularly current sources (done)
* Switch 2- and 3-pos Pheonix to single 5-pos Pheonix (done)
* Replace WiFi UART jumpers to 2x2 header (done)
* Reduce wasted board space (done enough)
* Change selected power jumpers to solder jumpers i.e. they should be NC instead of NO (done)
* Clean up SDRAM schematic sheet (done)
* LT3652 charging circuit:
    * Change output voltage circuit to tracking-optional (done)
    * Change input voltage to non-temperature compensated, adjustable MPP voltage (done)
    * See Sparkfun Sunny Buddy for more flexible circuit
* Change LT8608 switching frequency (move out of AM broadcast band, > 1.7 MHz) (done)
* ~~Change WiFi UART connection between MCU-ESP from RXD0/TXD0 to RXD2/TXD2 (done)~~
* (Keep WiFi UART to MCU UART on RXD0/TXD0, for esp-link firmware) (done)
* Move SJ200 (LT3652 TIMER solder jumper) to bottom (done)
* Move WiFi GPIO header to bottom, make DNP (done)
* Move MCU GPIO header to bottom, make DNP (done)
* Add board dimensions to top overlay (done)
* Add screw hole sizes/coordinates to bottom overlay (done)
* Remove extraneous testpoints, solder jumpers, and debug circuitry where possible (done)
* Add chamfered corners, adjusting screw hole footprints as necessary (done)
* Connect PV voltage through voltage divider to MCU ADC input for monitoring (done)

## SOLENS rev. A -> B changelog

* Moved D400 (3V3 power LED) to regulator side of 3V3 jumpers.
* Fixed fuel gauge wiring, renaming VBAT to VBAT_INT where appropriate.
* Cleaned up SDRAM schematic page
* Updated SDRAM data termination arrays to 33R
* Added termination resistor arrays to camera data and control lines (still not sure on value)
* Removed paste mask from TP_TINY
* Changed 0402 pad dimensions to 0.9 mm (X) x 0.6m mil (Y), no pad spacing changes
* Changed DFN8-3X3 pad dimensions to 0.25 mm (X) x 0.9 mm (Y), moving pads away from center to preserve ePad to pad spacing
* Removed R208, R209 (CHRG and FAULT 100k pullups)
* Removed input tracking circuitry from LT3652, preparing for updated tracking circuit
* Updated input tracking circuitry (now with trimpot!)
* Simplified output voltage set circuitry
* Combined PV input and battery connector into a single 5-pin Euroblock
* Updated LT3652 inductor selection to Taiyo Yuden NRS8040T150MJGJ
* Updated LT8608 inductor selection to Taiyo Yuden NR6028T2R2N
* Changed WiFi MCU-ESP UART to UART2 (programming on UART0)
* WiFi is now powered by default
* Added optional LT3652 tempco charging circuit
* Shrunk both power sections
* Shrunk WiFi section, changed WiFi GPIO header to bottom/DNP
* Rotated camera footprint placement by 180 deg, connector is now near board edge
* Shrank board dimensions, both vertically and horizontally
* Connected PV panel input voltage through voltage divider to MCU ADC input for monitoring
* Added two (optionally-bridged) GPIO between MCU and WiFi per BH suggestion
