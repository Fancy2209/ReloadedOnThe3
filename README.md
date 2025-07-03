# Requirements
- Portal 2 for PS3
- Portal 2 on Steam
- Portal 2 Authoring Tools
- Portal Reloaded on Steam
- VPKEdit
- BSPSource
- Dino D-Day
- Dino D-Day SDK

# Steps
1. Make a folder on your PC to do this converion work
2. Make a folder called game in that folder
3. Copy the bin folder from Dino D-Day to the game folder
4. Copy the platform and portalreloaded folders from Portal Reloaded into the game folder
5. Extract pak01_dir.vpk and place the contents in the portalreloaded folder (make sure to extract the contents of pak01_dir, so that you don't end up with a pak01_dir folder inside of portalreloaded)
6. Extract the models folder and the materials/tile folder from pak01_dir.vpk from portal2_dlc2 in the Portal Reloaded installation and place them in the portal reloaded folder, the game uses these assets
7. Some files need to be copied with different names, as makegamedata.exe only loads .vtx files with .dx90 in the name
Open the terminal/cmd in the portalreloaded and run the following command to fix this:
Linux:
```sh
cp ./a4_destruction/bts_chambercluster_04.vtx ./a4_destruction/bts_chambercluster_04.dx90.vtx
cp ./effects/vol_light.vtx ./effects/vol_light.dx90.vtx
cp ./effects/vol_light64x128.vtx ./effects/vol_light64x128.dx90.vtx
cp ./effects/vol_light64x256.vtx ./effects/vol_light64x256.dx90.vtx
cp ./effects/vol_light128x128.vtx ./effects/vol_light128x128.dx90.vtx
cp ./effects/vol_light128x256.vtx ./effects/vol_light128x256.dx90.vtx
cp ./effects/vol_light128x384.vtx ./effects/vol_light128x384.dx90.vtx
cp ./effects/vol_light128x512.vtx ./effects/vol_light128x512.dx90.vtx
cp ./effects/vol_light256x384.vtx ./effects/vol_light256x384.dx90.vtx
cp ./effects/vol_light256x512.vtx ./effects/vol_light256x512.dx90.vtx
cp ./hiyu/vol_model.vtx ./hiyu/vol_model.dx90.vtx
cp ./props_underground/stasis_chamber_outro_skybox.vtx ./props_underground/stasis_chamber_outro_skybox.dx90.vtx
cp ./props/switch002.vtx ./props/switch002.dx90.vtx 
cp ./props/switch003.vtx ./props/switch003.dx90.vtx
```

Windows:
```
xcopy ./a4_destruction/bts_chambercluster_04.vtx ./a4_destruction/bts_chambercluster_04.dx90.vtx
xcopy ./effects/vol_light.vtx ./effects/vol_light.dx90.vtx
xcopy ./effects/vol_light64x128.vtx ./effects/vol_light64x128.dx90.vtx
xcopy ./effects/vol_light64x256.vtx ./effects/vol_light64x256.dx90.vtx
xcopy ./effects/vol_light128x128.vtx ./effects/vol_light128x128.dx90.vtx
xcopy ./effects/vol_light128x256.vtx ./effects/vol_light128x256.dx90.vtx
xcopy ./effects/vol_light128x384.vtx ./effects/vol_light128x384.dx90.vtx
xcopy ./effects/vol_light128x512.vtx ./effects/vol_light128x512.dx90.vtx
xcopy ./effects/vol_light256x384.vtx ./effects/vol_light256x384.dx90.vtx
xcopy ./effects/vol_light256x512.vtx ./effects/vol_light256x512.dx90.vtx
xcopy ./hiyu/vol_model.vtx ./hiyu/vol_model.dx90.vtx
xcopy ./props_underground/stasis_chamber_outro_skybox.vtx ./props_underground/stasis_chamber_outro_skybox.dx90.vtx
xcopy ./props/switch002.vtx ./props/switch002.dx90.vtx 
xcopy ./props/switch003.vtx ./props/switch003.dx90.vtx
```

8. now in this terminal run 
```sh
mkdir OUT
../bin/makegamedata.exe -r -z OUT/zip1.ps3.zip -ps3
mkdir OUT/maps
```
then copy all maps with .ps3. to OUT/maps

9. Finally, copy the contents of the OUT folder to portal2_dlc3 in your PS3, it needs to be modded for this to be possible.
   
# Additional Information
You may notice some issues, like maps only loading on RPCS3 and the videos not showing up  
Some videos are 1440p, so you need to downscale them using the bink tools and then copy the media folder   
Maps need the Lightmap Scale downgraded, so you'll need to decompile them with BSPSource, and then use hammer to manually set the Lightmap Scale to something like 64 and then recompile them, after that run them trough makegamedata.exe (you can just do something like `../bin/makegamedata.exe path/to/map.bsp -ps3` and it'll convert just the map)  
You will need to rename media/startupvids.txt to media/startupvids.ps3.txt and re run makegamedata to remake the zip for the intro video to show up  

