*Ha, I tried to come back to this project, but of course I messed something up when pushing it to github, so even if it compiles successfully, there's some mix up between newer cura files and my 5.10.2 edits. Working on fixing this, but my release files still drop and work fine into Cura 5.10.2

I used Cura 5.10.2, not sure if this is backwards or forwards compatible. Just use a fresh install, and grab the zip file from the release section, or compile on your own if you'd like. Replacement files are:
fdmprinter.def.json
CuraEngine.exe
Had to modify the .json settings file to add in the castle settings and make them visible. Included a dif report.

https://github.com/SirStreetguru/CuraCastleSlicing/releases/tag/Castle-Slicing

castleslicing@gmail.com or @Lordstreetguru(NSFW) for questions/comments, or:
https://community.ultimaker.com/topic/47478-castle-slicing-is-now-real-automatically-hollow-models-for-faster-drafts-or-if-only-outer-detail-matters/

If I somehow hit $200 in donations I'll grab cursor ultra and get this more feature complete.

Dogecoin(Network):
D5pTVohSFxkrczJGyGaKgyR4iTi8iFDQcJ

Bitcoin(Network):
376TVy4SRV4VQF3jb8gheCfxxtjSeDahY7

Files modified:
CastleInternalBridgeDebug.h | 
FffPolygonGenerator.h | 
infill.h | 
LightningGenerator.h | 
sliceDataStorage.h | 
FffPolygonGenerator.cpp | 
FffGcodeWriter.cpp | 
infill.cpp | 
LightningGenerator.cpp | 
skin.cpp | 
support.cpp | 

Hi, I have no idea what I'm doing. I don't know how to Code in C, nor how to compile, nor any of the deeper concepts I modified within Cura here. I don't know why my CuraEngine.exe file is so much smaller than the original one, might have to do with plug ins. I think there's a bunch of warnings that pop up while compiling, but the software still works so...took quite a bit to get it compiling in the first place even with Cursor helping me at every step. No idea if I screwed anything up here, don't know how to use Github either.

But with the assistance of GPT 5.3 Codex and Cursor I added a feature that I had always dreamed about called "Castle Slicing", where any model could automatically be made hollow for faster draft prints, or extra geometery could be added for more strength, such as internal walls or mixing and matching infill.

Only Zig Zag, Gyroid, and Lightning(kinda) work at this time. If you set "Castle Wall Distance" to 0, normal slicing returns.

For more complex models you'll want to use the "Extra Castle Walls" feature, set that distance to "0" and enable Lightning infill, and the Extra Lightning option. That will generate lightning infill to support internal bridges created from hollowing out the model, it basically enables normal slicing within the center hollow space of the model, it has the side effect of still supporting top layers that may be missing at this time.

TOOL STATUS:
In the order it appears in the list

TOP/BOTTOM LAYERS:
Castle Full Top/Bottom: Working, restores original model geometry on only the top/bottom layers.

Castle Restore Internal Top/Bottom Surfaces: Partially Working, on Internal bridges top/bottom lays may be missing, this tries to restore them. Combine with "Full Top/Bot" to restore everything.

Castle Skin Clean Enabled/Distance:(DEPRECATED, use "Skin Removal Width" at ~2.2mm) On certain models, particularly spheres and pyramids with high angle changes, Top/Bottom Skin lines were bleeding on top of the wall layers. Generating bad geometery Cura has built in tools for this already I didn't know about, not sure if it's needed for special cases, but it's mostly redundant. Skin Removal Width at 2.2mm generally worked well for me, set that to the default while using Castle Slicing. It fixes top/bottom layer generation in general while using castle slicing. Increasing it may erase more top/bottom layers than intended.

INFILL(The star of the show):
Castle Slicing only works with Zig Zag, Gyroid, or Lightning(partial) at this time. Alway use at least 1 Extra Infill Wall for full features/reliability. 

Custom Castle Inner Shape + Castle Hollow Taper + Extra Castle Walls, can all be combined and used together. Uknown what the limits are before geometery breaks at this time. I'm surprised how well they are able to work together, they were designed independently.

Castle Wall Distance: Creates a hollow center that follows the model's geometry, just set the distance and the infill will guide the rest of the geometery. I asked GPT 5.3 to create a tool that capped the distance between the extra infill walls to start this whole thing.

-Castle Wall Layer Generation: Use to add wall layers to the inside of the castle wall.

Castle Continuous Zig Zag Line:(UNFINISHED)Castle Slicing is recursive, but I was unable to finish this tool at this time. It almost creates one single path around the hollow ring when only using infill lines.

Custom Castle Inner Shape:Creates a custom hollow shape to form the inner castle wall, Circle or Polygon at this time. May be completely broken on more complex models.

Custom Hollow Taper:Tapers the inner wall, can be used to great effect to support roofs. You can set a custom hole size as well that will form at the center of the model. Strict Bottom Taper Angle makes the bottom layer angle match the top if desired.

Extra Castle Walls:Max is 1, it creates a 2nd ring of walls, mostly useful for adding Lightning Infill(+Extra Castle Lightning...) to support internal bridges, or keep a model hollow while maintaining a full roof. Set the distance to 0 here to restore normal slicing within that space. Only a few infill options are added at this time, rest use global settings. USE AT LEAST 1 EXTRA INFILL WALL, TY.

Fix Sphere top/bottom layers:(DEPRECATED) It didn't fix what I was trying to fix.

Detect Castle Bridges:(DEPRECATED) Tried to use this to gather data and fix the internal bridging problem.

Detect Internal Bridges:(DEPRECATED) Another attempt to gather better data, may be useful in the future, doesn't break slicing if left on.

Plug Internal Bridges, Plug Support V2, Plug Support V2 Infill, Support Interal Bridges:(DEPRECATED) Various attempts to solve the internal bridging problem.

Castle Walls Supports:(UNFINISHED) Forces support generation to follow only the 1st castle wall ring. It kind of works.

I think that's everything for now. I'm hoping actual cura devs pick up the concept. Not sure how much further I can take it, or how well I could maintain it at this time. I will likely do at least a little more work to get a few more features implemented. Thanks for trying it out.




<br>

<div align = center>

[![Badge Issues]][Issues]   
[![Badge PullRequests]][PullRequests]   
[![Badge Closed]][Closed]

[![Badge Size]][#]   
[![Badge License]][License]   
[![Badge Contributors]][Contributors]

[![Badge Test]][Test]   
[![Badge Conan]][Conan]   

<br>
<br>

<img
    src = 'CuraEngine.ico'
    width = 200
/>

# CuraEngine


*C++ console application for 3D printing GCode generation.*

<br>
<br>

[![Button Install]][Install]   
[![Button Internals]][Internals]

<br>
<br>


Designed as a better and faster alternative to the old <br>
**Skeinforge Engine** and is an integral part of **[Cura]**.

You can use CuraEngine separately, in other <br>
applications and integrate it into your own app.

<br>

[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/Ultimaker/CuraEngine/badge)](https://api.securityscorecards.dev/projects/github.com/Ultimaker/CuraEngine)

<br>

<!----------------------------------------------------------------------------->

[Contributors]: https://github.com/Ultimaker/CuraEngine/graphs/contributors
[PullRequests]: https://github.com/Ultimaker/CuraEngine/pulls
[Internals]: https://github.com/Ultimaker/CuraEngine/wiki/Internals
[Install]: https://github.com/Ultimaker/CuraEngine/wiki/Building-CuraEngine-From-Source
[Closed]: https://github.com/Ultimaker/CuraEngine/issues?q=is%3Aissue+is%3Aclosed
[Issues]: https://github.com/Ultimaker/CuraEngine/issues
[Conan]: https://github.com/Ultimaker/CuraEngine/actions/workflows/conan-package.yml
[Test]: https://github.com/Ultimaker/CuraEngine/actions/workflows/unit-test.yml
[Cura]: https://github.com/Ultimaker/Cura

[License]: LICENSE
[#]: #


<!---------------------------------[ Badges ]---------------------------------->

[Badge Contributors]: https://img.shields.io/github/contributors/ultimaker/CuraEngine?style=for-the-badge&logoColor=white&labelColor=db5e8a&color=ab4a6c&logo=GitHub
[Badge PullRequests]: https://img.shields.io/github/issues-pr/ultimaker/CuraEngine?style=for-the-badge&logoColor=white&labelColor=bb9f3e&color=937d31&logo=GitExtensions
[Badge License]: https://img.shields.io/badge/License-AGPL3-336887.svg?style=for-the-badge&labelColor=458cb5&logoColor=white&logo=GNU
[Badge Closed]: https://img.shields.io/github/issues-closed/ultimaker/CuraEngine?style=for-the-badge&logoColor=white&labelColor=629944&color=446a30&logo=AddThis
[Badge Issues]: https://img.shields.io/github/issues/ultimaker/CuraEngine?style=for-the-badge&logoColor=white&labelColor=c34360&color=933349&logo=AdBlock
[Badge Conan]: https://img.shields.io/github/workflow/status/Ultimaker/CuraEngine/conan-package?style=for-the-badge&logoColor=white&labelColor=6185aa&color=4c6987&logo=Conan&label=Conan%20Package
[Badge Test]: https://img.shields.io/github/workflow/status/Ultimaker/CuraEngine/unit-test?style=for-the-badge&logoColor=white&labelColor=4a999d&color=346c6e&logo=Codacy&label=Unit%20Test
[Badge Size]: https://img.shields.io/github/repo-size/ultimaker/CuraEngine?style=for-the-badge&logoColor=white&labelColor=715a97&color=584674&logo=GoogleAnalytics


<!---------------------------------[ Buttons ]--------------------------------->

[Button Internals]: https://img.shields.io/badge/Internals-00979D?style=for-the-badge&logoColor=white&logo=CodeReview
[Button Install]: https://img.shields.io/badge/Installation-e23345?style=for-the-badge&logoColor=white&logo=DocuSign

