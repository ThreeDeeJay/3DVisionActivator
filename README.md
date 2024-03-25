# 3DVisionActivator
Program to drive the Nvidia 3D Vision Shutter glasses without the Nvidia 3D Vision driver.
Initially made by "cms": https://www.mtbs3d.com/phpbb/viewtopic.php?p=23830#p23830

Keys:
- F1 - toggles stereo
- F2 - swaps eyes
- F3 - goes to the next refresh rate (or loops to the first)
- F5/Shift-F5 - modifies the convergence
- F6/Shift-F6 - modifies the separation

How it works:
There are two rendering contexts (in separate threads).
The offscreen thread is not bound by vsync and continually renders the scene to a set of frame buffer objects (one for each eye).
The visible context is bound by vsync and has access to these fbos.
It renders the appropriate eye fbo to the window and toggles the 3dVision's "eye."
A file named "validRefreshRates.ini" holds a refresh rate per line. The program will initially use the top refresh rate. (You may want to change this)

Dependencies:
- Visual Studio 2022
- GLEW 2.2.0
- SFML 2.6.1

Known Bugs:
- When app is closed with the "X", the Offscreen Thread will stay active in background - Please close with "ESC" key for now!
- When Nvidia IR emitter goes to sleep mode and the app is started, Win10 will crash with the BSOD "SYSTEM_SERVICE_EXEPTION" "ucx01000.sys" !
- Sync to Monitor refresh is still not working!
