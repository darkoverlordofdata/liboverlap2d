# libo2d

## status
on hiatus until Gnome can be more positive about the future of Vala
https://mail.gnome.org/archives/vala-list/2016-September/msg00001.html 

loads the json files:
* project.dt
* scenes/*.dt

providing strongly typed access to the entire model

inspired by https://github.com/UnderwaterApps/overlap2d-runtime-libgdx
I didn't name it overlap2d-runtime-libsdx.
It does not include the ecs (ashley) components.
 
        Overlap2D data is exported and embedded 
        into the application as a gresource:


            ShmupWarz.exe:
            =========================
            | project.dt            |
            | scene-n.dt            |
            | => pack.png           |
            | => pack.atlas         |
            | => *.wav, *.ttf       |
            |-----------------------|
            |  Game                 |
            |  Program              |
            |  => gresource         |
            =========================


```
var sceneLoader = new Overlap2D.SceneLoader("resource:///darkoverlordofdata/shmupwarz")
sceneLoader.loadScene("MenuScene")
var playButtonVO = sceneLoader.loadVoFromLibrary("playButton")

```            

github frontend. todo ~ build on launchpad.

