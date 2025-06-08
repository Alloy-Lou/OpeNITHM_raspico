# OpeNITHM_raspico
Because OpeNITHM is too cool to be abandonned just because the Teensy LC was discontinued.  
This version uses instead a Raspberry Pi Pico and a bunch of MPR121 modules to get the work done.  
This repository is intended to be a fool-proof and beginner-friendly guide for the assembly of this build.  
This is one of my first DIY projects, so I believe it can be quite accessible with a minimum of technical knowledge.  
I made all the mistakes (even the awkward ones) so you don't have to!  
As a heads-up, this guide will be written in a casual tone (because why not)  

## Sources & Thanks
Special thanks to the original author(s) and contributors of the following repositories, guides, and communities:
- https://github.com/Yona-W/OpeNITHM/
- https://github.com/mnm-isola/chupico_openithm_pcb
- https://github.com/whowechina/chu_pico/
- Cons&Stuff [Website](https://consandstuff.github.io/) [Discord](https://discord.gg/t96u85FG2q)
- [Original guide](https://github.com/Yona-W/OpeNITHM/issues/8#issuecomment-775383127)
- [Another useful guide](https://docs.google.com/document/d/105rUEiN73gfQaTJluvr7cBXek0CN0OwznHBYRm4jEQY/)
- [Yet another useful guide](

## Disclaimer
This build have very very little testing (I'm the only one to have completed it as far as I know... for now!) so there might be some hidden little issues I haven't encountered yet.  
Proceed at your own risk! I'm not responsible for anything that breaks or don't work. (Scary disclaimer but I have to give warnings).  
If you encounter anything that goes wrong, feel free to open an issue!

## List of Hardware
If full DIY-ed, this build can be quite cheap to assemble!  
Here are the list of items I needed, the (approximate) price I paid to build mine as well as the links to where I bought them:

| Part | Link | Qty | ~Price |
| --- | --- |:---:|:---:|
| PLA filament | [Amazon](https://amzn.eu/d/09YLfO2) | 1 | 18€<sup>1</sup> |
| Acrylic | Bought in a small local plastic shop | 1 | 8€<sup>1</sup> |
| PCB | [JLCPCB](https://jlcpcb.com) | 1<sup>2</sup> | $1 + $9.42<sup>4</sup> |
| Raspberry Pi Pico | [Aliexpress](https://a.aliexpress.com/_Eyv5vcO) | 1 | 1€39<sup>3</sup> |
| MPR121 | [Aliexpress](https://a.aliexpress.com/_EufFj5C) | 3<sup>2</sup> | 3€70 |
| 74HC4051 | [Aliexpress](https://a.aliexpress.com/_Exj6LtC) | 1 | 1€13 |
| WS2812B LED strip | [Aliexpress](https://a.aliexpress.com/_Ey5HEZc) | 1 | 3€67 |
| Dupont wires | [Aliexpress](https://a.aliexpress.com/_EIvt6Ke) | 1 set | 0€71<sup>3</sup> |
| Pin Header, Right Angle, 2x24 pos | [LCSC](https://www.lcsc.com/product-detail/New-Arrivals_XFCN-PZ254R-12-24P_C492440.html) | 2<sup>2</sup> | $0.84 |
| 2.54mm Socket, 1x20 pos | [LCSC](https://www.lcsc.com/product-detail/Female-Headers_Shenzhen-Kinghelm-Elec-KH-2-54FH-1X20P-H8-5_C2905423.html) | 2<sup>2</sup> | $0.81 |
| 2.54mm Socket, 1x12 pos | [LCSC](https://www.lcsc.com/product-detail/Female-Headers_Shenzhen-Kinghelm-Elec-KH-2-54FH-1X12P-H8-5_C2905419.html) | 3<sup>2</sup> | $0.56 |
| LCSC shipping<sup>4</sup> | - | - | $8.62<sup>4</sup> |  

Total : 36€60 & $21.25 so around 55€ with a decent conversion rate

<ins>Notes :</ins>  
1 : You'll likely not use the entire thing (i barely used 20% of my acrylic pane, and had a lot of filament left)  
2 : You'll likely have to buy more since the item is usually sold in bulk (typically sets of 5)  
3 : Aliexpress bulk prices are variable. Order all the items at once, using the bulk order system, to save money  
4 : Shipping + taxes. Very likely to change depending your location. I ordered from France.  
- I haven't checked if LCSC items are available on Aliexpress. If so, you might be able to save money on shipping.
- The Raspberry Pi clone worked fine for me (I ordered multiple ones from three different sellers). Apparently it's hard to make a bad clone of it. And you can get a USB-C version of it. [Source](https://www.reddit.com/r/raspberrypipico/comments/1b0x44y/comment/ksbhkre/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
- I did get one faulty MPR121 module out of the 10 I ordered though. (Or I killed it. Also possible)
- I don't recommand cheaping out on the PLA filament to avoid messing with your printer or the quality of prints
- You can get coupons, especially on JLCPCB, if you're a new client (that's how I got 10 PCBS for $1)

### Optionnal
| Part | Link | Qty | ~Price |
| --- | --- |:---:|:---:|
| 51k ohm Resistor<sup>1</sup> | [LCSC](https://www.lcsc.com/product-detail/Through-Hole-Resistors_VO-CR1-8W-51K-5-ST52_C2897072.html) | 6 | $0.25 |
| 33 ohm Resistor<sup>1</sup> | [LCSC](https://www.lcsc.com/product-detail/Through-Hole-Resistors_Huaxing-Mechanical-Elec-MF1-4W-33-1-T52_C713968.html) | 3 | $0.67 |
| 2.54mm Socket, 1x6 pos<sup>2</sup> | [LCSC](https://www.lcsc.com/product-detail/Female-Headers_Shenzhen-Kinghelm-Elec-KH-2-54FH-1X6P-H8-5_C2905416.html) | 3 | $0.37 |
| 2.54mm Socket, 1x8 pos<sup>2</sup> | [LCSC](https://www.lcsc.com/product-detail/Female-Headers_Shenzhen-Kinghelm-Elec-KH-2-54FH-1X8P-H8-5_C2905417.html) | 1 | $0.45 |
| 2.54mm Socket, 1x11 pos<sup>2</sup> | [LCSC](https://www.lcsc.com/product-detail/Female-Headers_Shenzhen-Kinghelm-Elec-KH-2-54FH-1X11P-H8-5_C2932674.html) | 1 | $0.55 |

<ins>Notes :</ins>  
1 : Mine works fine without any, but I think it was supposed to have some... It's pretty cheap, so you might want to get them, just in case it turns out it's needed.  
2 : You can cut your leftover from 20 and 12pos, but it's not made to be cut (so it's not super easy, but doable). Get those only if you're not confortable with cutting things.  
