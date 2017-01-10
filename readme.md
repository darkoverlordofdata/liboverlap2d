# liboverlap2d

## status
loads the json files:
* project.dt
* scenes/*.dt

providing stronly typed read-only access to the entire model

inspired by https://github.com/UnderwaterApps/overlap2d-runtime-libgdx
but does not include the ecs or ui components.
 
        Overlay2D data is exported and embedded 
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

