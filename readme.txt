INC 2007 Alignment
------------------

Only one of these cartirdges (if any) will pass on your console.
Further down in this document, I provide a table of results.
My console passes the tests of "INC2007Alignment.nes".
Console A passes the tests of "INC2007Alignment_A.nes" and so on.

This cartridge is designed to determine the current alignment of the CPU clock and PPU clock.

This cartridge is expecting the values that my console uses, though results may vary.
If this fails on your console, try running INC2007Alignment_A.nes

Setup: The VRAM Read Buffer is prepared with the value $55.
All bytes in VRAM $2000 through $23BF are set to $00.
The VRAM Read/Write address is moved to $2110
This setup step is ran before the INC $2007, and it is ran again before the INC $2007, X.

Suite 1: INC $2007
Test 1: Read $2111
Test 2: Read $2112
Test 3: Read $2156

Suite 2: INC $2007, X (Alignment 0)
Test 4: Read $2111
Test 5: Read $2112
Test 6: Read $21xx, where xx is the expected result of test 5.

Suite 2: INC $2007, X (Alignments 1, 2, and 3)
Test 4: Read $2112
Test 5: Read $2113
Test 6: Read $21xx, where xx is the expected result of test 5.

-----------------------

My console: NES-CPU-10. RP2A03G, RP2C02G-0

Additional consoles tested with the help of 
members from the nesdev and tasbot discords:

jroweboy (Same behavior as my console)
CutterCross (Console A)
Bigbass (Console B)

There are likely more potential results. 
This table will be updated as more research is conducted.

Expected results:
┌──────┬────────────┬────────────┬────────────┐
│ Test │ My console │ Console A  │ Console B  │
├──────┴────────────┴────────────┴────────────┤
│                 Alignment 0                 │
├──────┬────────────┬────────────┬────────────┤
│  1   │ $2111 = 11 │ $2111 = 10 │ $2111 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  2   │ $2112 = 00 │ $2112 = 00 │ $2112 = 00 │
├──────┼────────────┼────────────┼────────────┤
│  3   │ $2156 = 56 │ $2156 = 56 │ $2156 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  4   │ $2111 = 11 │ $2111 = 11 │ $2111 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  5   │ $2112 = 00 │ $2112 = 00 │ $2112 = 00 │
├──────┼────────────┼────────────┼────────────┤
│  6   │ $2156 = 56 │ $2156 = 56 │ $2156 = 56 │
├──────┴────────────┴────────────┴────────────┤
│                 Alignment 1                 │
├──────┬────────────┬────────────┬────────────┤
│  1   │ $2111 = 11 │ $2111 = 10 │ $2111 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  2   │ $2112 = 56 │ $2112 = 56 │ $2112 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  3   │ $2156 = 56 │ $2156 = 56 │ $2156 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  4   │ $2112 = 12 │ $2112 = 12 │ $2112 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  5   │ $2113 = 56 │ $2113 = 56 │ $2113 = 00 │
├──────┼────────────┼────────────┼────────────┤
│  6   │ $2156 = 56 │ $2156 = 56 │ $2156 = 56 │
├──────┴────────────┴────────────┴────────────┤
│                 Alignment 2                 │
├──────┬────────────┬────────────┬────────────┤
│  1   │ $2111 = 11 │ $2111 = 10 │ $2111 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  2   │ $2112 = 56 │ $2112 = 56 │ $2112 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  3   │ $2156 = 56 │ $2156 = 56 │ $2156 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  4   │ $2112 = 12 │ $2112 = 10 │ $2112 = 11 │
├──────┼────────────┼────────────┼────────────┤
│  5   │ $2113 = 11 │ $2113 = 11 │ $2113 = 11 │
├──────┼────────────┼────────────┼────────────┤
│  6   │ $2111 = 11 │ $2156 = 11 │ $2111 = 11 │
├──────┴────────────┴────────────┴────────────┤
│                 Alignment 3                 │
├──────┬────────────┬────────────┬────────────┤
│  1   │ $2111 = 11 │ $2111 = 10 │ $2111 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  2   │ $2112 = 56 │ $2112 = 56 │ $2112 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  3   │ $2156 = 56 │ $2156 = 56 │ $2156 = 56 │
├──────┼────────────┼────────────┼────────────┤
│  4   │ $2112 = 12 │ $2112 = 00 │ $2112 = 01 │
├──────┼────────────┼────────────┼────────────┤
│  5   │ $2113 = 01 │ $2113 = 01 │ $2113 = 00 │
├──────┼────────────┼────────────┼────────────┤
│  6   │ $2101 = 01 │ $2156 = 01 │ $2101 = 01 │
└──────┴────────────┴────────────┴────────────┘


See the screenshots provided in the screenshots folder for the test screens and results.

--------------
RMW $2007 Test
--------------

This cartridge runs a series of INC $2007 instructions with different PPUADDR values and different buffer contents.
It runs 3 tests.

Test 1: Verify that INC $2007 is creating extra writes
Test 2: Verify that the high byte of the extra write's address changes if PPUADDR crosses a page boundary during the INC isntruction.
Test 3: Verify that the extra write is incapable of updating color palette information; instead, the write can be seen by reading the mirror at $2Fzz.

-----------------------

Test 1: runs 4 tests.
- Buffer holds 55, VRAM Address = $2110. INC $2007. Result: Vram $2156 = $56
- Buffer holds 7F, VRAM Address = $2000. INC $2007. Result: Vram $2080 = $80
- Buffer holds 00, VRAM Address = $2F7F. INC $2007. Result: Vram $2F01 = $01
- Buffer holds FF, VRAM Address = $2222. INC $2007. Result: Vram $2200 = $00

It's worth noting that there's potentially another extra write occuring, though it's different depending on the console revision, as well as the alignment between the CPU and PPU clocks.
This ROM only tests for one of the writes.

Test 2: runs 2 tests
- Buffer holds 55, VRAM Address = $21FF. INC $2007. Result: Vram $2256 = $56
- Buffer holds 7F, VRAM Address = $1FFF. INC $2007. Result: Vram $2080 = $80

Test 3: runs 2 tests
- Buffer holds 04, VRAM Address = $3F00. INC $2007. Result: Vram $2F05 = $05
- Buffer holds 20, VRAM Address = $3F14. INC $2007. Result: Vram $2F11 = $11
Test 3 only verifies that the palettes aren't being modified. The extra write doesn't appear to occur if the CPU and PPU clocks are on the same master clock cycle. (alignment 0)