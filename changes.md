# Changelog and Notes

## SOLENS rev. A (first PCB)

#### Rev. A PCB/schematic issues

* Power LED on wrong side of R400/R403, power LED should illuminate when 3V3 buck is on, regardless of rest of board.
* TP\_TINY footprint is missing soldermask and got pasted
    * TP202 missing mask
    * TP500 missing mask
    * TP501 missing mask
* 0402 footprints need a slight change of shape, pads should be slightly closer together and enlarged slightly
    * This should fix the few tombstoned capacitors
* Fuel gauge footprint (DFN) needs larger pads (more paste volume) for better reflow
* Fuel gauge is mis-wired, only senses current _into_ battery.
* SDRAM data (DQ*) termination is listed as 49R9, should be 33R per Hyperlynx sims
* Slight undershoot issue on camera parallel interface (need scope captures to document)
    * Add termination arrays on all camera interface lines, value unknown (need to rework SJ* on bus before value decision)
* LT3652 charging circuit had regulation issues (bad/damaged chip?)

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
* Shrink inductor sizes
* Move components to back, particularly current sources
* Switch 2- and 3-pos Pheonix to single 5-pos Pheonix
* Replace WiFi UART jumpers to 2x2 header
* Reduce wasted board space
* Change selected power jumpers to solder jumpers i.e. they should be NC instead of NO
* Clean up SDRAM schematic sheet
* LT3652 charging circuit:
    * Change output voltage circuit to tracking-optional
    * Change input voltage to non-temperature compensated, adjustable MPP voltage
    * See Sparkfun Sunny Buddy for more flexible circuit

## SOLENS rev. A -> B changelog

No changes committed yet.
