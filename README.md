# keyforge-deobfuscator
ts a file that came from discord.gg/tbjBPTRnph. static deobfuscator for keyforge obfuscator, output is not runnable
keyforge obfuscation breakdown guide, not a full deobfuscator!!!!
this is a guide for breaking down forgevm

using sample 277

first extract constants, insert the snippet before the last return, run it in lune, get strings like lobby, playing, max

then dump instructions, call hmh in a loop, get newtable, loadk, setk with their args

from constants and the dump you see what the script does, for 277 it's a table with states and methods setstate, addplayer, start

each script has its own opcode ids, for 277 setk is 862939

to deobfuscate any script, extract dispatch from kb42, read the handler for each opcode, figure out the operation from the code

dispatch is nested ifs with numbers, stack a equals const b is loadk, stack a equals empty table is newtable, stack a in brackets const b equals stack c is setk

the output folder has clean versions for all seven, 277 is a state machine, 278 timer, 279 rpg, 280 roblox, 281 score, 282 hello world

automation is hard, each has its own opcodes and everything is renamed, easier to do it manually with lune, extracting constants and instruction dumps

if something is unclear, paste this guide into any ai and it will help you figure it out

also go through the deobf.py code together with this guide to understand what it actually does, it shows how opcodes get mapped, how dispatch is extracted, and why automation fails on most samples
