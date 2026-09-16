# Changelog

Every release, newest first. This is generated from the app's own
What's New dialog, so the two always say the same thing.

## v1.0.9

- Fixed: the startup splash jumped up and to the left and shrank a moment before the main window appeared, on any display not set to 100%

## v1.0.8

- SEVERAL IMAGES OPEN AT ONCE, each in its own window with a title bar you can drag and a corner you can resize
- Added TILE and CASCADE to the Editor toolbar, re-fitting each image to its new window
- Added a WINDOW MENU between Settings and Help, listing every open image - minimised ones included - with the active one ticked
- Added KEYBOARD WINDOW CYCLING: Ctrl+Tab and Ctrl+Shift+Tab, with Ctrl+F6 and Ctrl+Shift+F6 doing the same
- Added a 1:1 button to each image window; the toolbar's 1:1 and Fit are now global to match
- Clicking an image window makes it the one the toolbar, tools, Undo, Save and readout all point at
- Picking several files in Open... now shows them all, tiled, instead of one in the Editor and the rest as icons
- Double-clicking a workspace icon now joins the images already on screen instead of replacing them
- Added a SPLASH SCREEN to the built .exe, showing the logo as soon as the icon is double-clicked
- Renamed Clear Editor to CLEAR WORKSPACE - it closes every open image, after a warning listing what would be lost
- The empty Image Editor now offers drag & drop like the Files Viewer, and only when drag & drop is actually working
- Dropping a workspace icon onto a Mini Viewer now MOVES the image rather than copying it
- Opening an icon whose image is sitting in a Mini Viewer now clears that Mini Viewer, so the image is in one place
- Open, Save, Output Folder, Auto-open Result, Tile and Cascade are white on the top toolbar again rather than orange
- Image window title-bar buttons are bigger and held clear of the resize corner
- Drag & drop now reports in the console whether it is working, instead of failing silently
- ONE PICTURE PER IMAGE: every window draws the same full-resolution picture, so switching windows is a redraw rather than a two-second rebuild
- A mono image is stretched once rather than three times - 2.77s against 5.52s on a 24 megapixel frame
- Image pictures are built one at a time, in order, and the image you click goes to the front of the queue
- The rendered-image cache is sized to the workspace instead of being fixed at four
- The History panel is no longer rebuilt while it is collapsed
- Selecting an image no longer forces three full repaints of the application
- Minimising the image you are editing hands over in the same turn of the event loop
- A parked image's icon is made from that image's own picture rather than read from the file again
- The screen stretch belongs to the IMAGE: turning STF off, or switching Linked/Unlinked, no longer disturbs the other windows
- Image windows take the shape of the image rather than of the space they are given
- Every open image is read by the same loader the editor uses, so float data is normalised the same way
- A window you are not editing is drawn with the same stretch curve as one you are
- Fixed: dragging an image window was slow, left a trail of half-drawn edges, and smeared blue streaks behind it
- Fixed: clicking between image windows blanked the one you had just left, and flickered
- Fixed: minimising one window disturbed every other window, or blanked the Editor
- Fixed: closing or minimising the last image left an empty window standing where it had been
- Fixed: SWAP left the window still describing the image that had just left it
- Fixed: the wheel zoomed the wrong image, and hovering a window reported another image's pixels
- Fixed: a window could open larger than the Editor, or slide into its own corner after a Tile or Cascade
- Fixed: opening an image while others were in windows often showed its name but no picture
- Fixed: opening several images at once painted several arrangements before settling on the right one
- Fixed: the empty Image Editor came up completely blank on a fresh start
- Fixed: the empty-workspace logo appeared in the top-left corner for a moment before centring
- Fixed: dropping an icon where two Mini Viewers overlap loaded it into the one underneath
- Fixed: the Camera RAW Editor's live preview failed on every mono image
- Fixed: an XISF window did not take its image's shape, leaving black bands beside the picture
- Fixed: an image window shaped itself from a downscaled copy, and a saved file left the window showing the old version
- Fixed: the picture in every window jumped three pixels for a single frame on each switch
- Fixed: dragging a file onto the editor stopped working over the workspace icons
- GROUNDWORK for the multi-window workspace: each image has its own canvas and its own frame

## v1.0.7

- The crop box TILTS - drag the grip outside its top-right corner and Apply Crop hands the tilted rectangle back upright
- A tilted crop keeps a plate solution pointing at the same sky, verified against astropy
- A tilted crop is refused on a still-Bayer file, where it would blend the colour filter pixels together
- The crop box has eight handles, four corners and four sides, and the opposite one stays put while you drag
- Removed: the green stippled wash inside the crop box - it covered the detail you are framing
- Set Preview Region has the same eight handles, and its overlay no longer flickers while dragging
- Added MINIMISE, FIT and CLOSE in the top-right corner of the Editor; Minimise parks the image as a workspace icon
- Every tool has its own icon, in the sidebar, in the menu and on its own window's title bar and taskbar button
- Blemish Blaster spots stay editable - click to select, drag to move or resize, Delete removes just that one
- Manual Background Extraction's exclusion areas are editable, with Backspace to take back the last corner
- PICK THE MASK LIMITS OFF THE IMAGE: RangeSelection's Lower and Upper can be set by clicking your own sky or nebula
- Background Neutralization has Pick Background - one click on your sky brackets it
- LinearFit has Pick Reject Low and Pick Reject High, set by clicking what you want kept
- Curves can pick from the image - a click marks the value under the cursor, a double-click anchors the curve there
- Renamed Narrowband Addition to ADD NARROWBAND TO RGB, with a Plain add mode alongside the relinearised one
- Add Narrowband to RGB warns when the two images would lift the background rather than add emission
- Continuum Subtraction saves a second, ready-to-combine copy with its black point already placed
- Continuum Subtraction's continuum scale can be typed over the fitted one, with Use fitted to put it back
- LinearFit's reference is chosen with one dropdown - workspace images, then Mini Viewers, then Browse
- The hover readout shows K for mono images, and Preview Region gives its median and mean
- The magnifier has a crosshair and a sample box, showing the single pixel and the box median together
- RangeSelection's Smoothness is now called BLUR, which is what it is, and reaches 80 instead of 10
- Adjusting a RangeSelection mask while it is Active is no longer slow - 2.7 seconds a slider move, gone
- Large mask blurs are built at reduced resolution, which the result cannot tell apart
- Fixed: Undo after LinearFit showed a blown-white image until the stretch was toggled
- Fixed: Ctrl+Z while typing in a box undid the image, and reached past a tool window to the image behind
- Fixed: closing the last workspace icon left the canvas still telling you to double-click one
- Fixed: the View FITS Header window kept the plain application icon and never got the dark title bar
- Fixed: a crash when closing a tool dialog - the viewer was asked to re-render with no file given
- Fixed: cancelling Save As New discarded the result instead of leaving it in the editor
- Fixed: renaming an image did not follow it onto a workspace icon, which came back with a generic name

## v1.0.6

- A PIXINSIGHT-STYLE IMAGE WORKSPACE - every open image is a document with its own Undo history, stretch, zoom and pan, and extra images minimise to draggable icons
- Live previews now genuinely match Apply - the proxy they previewed from was brightening the background
- Tool source pickers list the open workspace images by name instead of Main Viewer and Mini Viewer entries
- Added a built-in engine SELF-TEST: run with --selftest and 22 checks verify every hard guarantee, no window
- Iterative tools no longer grow the image title on every pass - six runs of GHS adds _GHS once, not six times
- Fixed: the white flash on Apply with the screen stretch engaged
- Fixed: GHS could leave dark dots in star cores at the smaller preview sizes
- Fixed: the GHS symmetry-point dropper could throw the image half off screen if your hand moved during the pick
- Fixed: double-clicking a workspace icon could freeze the whole app on Windows
- Fixed: images could open off-centre, inheriting the previous image's pan
- Fixed: wheel zoom was dead in Mini Viewers for mono images arriving via icon drops, and the empty editor's watermark could be dragged around

## v1.0.5

- Added MANUAL BACKGROUND EXTRACTION, the DBE-style tool the app was missing - place samples on sky, a surface is fitted through them and removed
- Manual Background Extraction colours each sample by whether it is really measuring sky, as Astro Pixel Processor does
- Manual Background Extraction is much faster - the fitted surface took minutes on a 26 megapixel frame
- Manual Background Extraction samples now sit closer to the frame edge, so the surface extrapolates less
- Its model is shown contrast-stretched, matching Background Extraction, and no longer with a colour cast
- Added a PREVIEW QUALITY control to the Editor toolbar - Fast, Normal, High or Maximum
- Added a Mask menu beside Preview Quality, replacing three icon buttons that could not be made legible at 20px
- The Crop Tool tints the area being KEPT a translucent green, and has Size boxes for the selection
- The crop box no longer flickers while you drag its handles
- The Image Solver asks for focal length and pixel size when the header has none, and remembers them per rig
- SPCC has the same focal length box as the Image Solver, since it plate solves first and fails for the same reason
- XISF images now have their header read everywhere FITS ones do
- The background tools now say so when the image is 16-bit integer data, where a fitted surface has little to work with
- Combine RGB has separate Custom (RGB) and Custom (LRGB) modes, and says what it is doing during the pause after a run
- Mini Viewers load far more quickly - they were stretching at full resolution rather than from a proxy
- Mini Viewers no longer sit unpainted while they open, or appear on the taskbar before they appear in the app
- Mini Viewers scroll and zoom much more quickly, and no longer go blocky
- Tool previews no longer go blocky when zoomed in
- Curves is much faster, especially at the higher preview settings
- GHS now computes in float32, tested against the old code across 420 parameter combinations
- SCNR, Background Neutralization and Star Stretch moved to float32, bit-identical where it matters
- The mask overlay is blended in integer arithmetic, so a scroll wheel with a mask active is no longer sluggish
- Every path that changes what the Editor shows now goes through one function
- FIXED, and this one could destroy a file: after a successful plate solve the app copied Siril's working copy back over the original
- Fixed: plate solving and SPCC failed on any non-FITS image, and ignored an XISF image's pixel size and coordinates
- Fixed: Background Extraction, SPCC and Image Solver all failed outright on XISF and TIFF images
- Fixed: stepping back through Undo, or closing a tool, brought the colour cast back on an Unlinked stretch
- Fixed: toggling the screen stretch while inspecting the Manual Background Extraction model replaced it with the working image
- Fixed: Show Background in GraXpert and Background Extraction displayed the model as a solid green frame
- FIXED in Manual Background Extraction: the model came out pure black with the stretch off and pure white with it on
- FIXED in Manual Background Extraction: it wrote its result as .fits regardless of the source format
- FIXED in Manual Background Extraction: every failure was reported as nothing at all
- FIXED in Manual Background Extraction: applying twice wrote to the same file while the viewer still had it open
- FIXED in Manual Background Extraction: samples survived closing the tool and sat on the previous state of the image
- Fixed: a Mini Viewer could produce hundreds of identical minimised icons
- Fixed: closing a tool without applying could leave the unapplied preview in the viewer as though committed
- Fixed: the Shape Mask overlay vanished when you zoomed or panned

## v1.0.4

- Renamed to ASTROSUITE PRO - settings, profiles and history saved under the old name are moved across on first run
- Added a MENU BAR and ICON TOOLBAR across the top - File, Edit, Tools, Settings and Help, each showing its shortcut
- The Image Editor toolbar is now a single row of drawn icons instead of two rows of text buttons
- The left panel can be collapsed from the tabs on the window's edge, from Edit, or with F9
- The left edge carries STACKING and HISTORY tabs choosing what the left column shows
- Added a HISTORY VIEW: every tool applied to the image, in order, with a click taking you back to that step
- The History view keeps a permanent record, written to a log beside the settings
- The Information Panel and Console can be hidden together - toolbar icon, Edit menu, or F8
- Every Process Tools category is now collapsible, not just four of them
- Added SHAPE MASK - draw regions on the image and what you run next affects only those areas
- Added Show/Hide, Invert and Delete Mask buttons to the Editor toolbar
- A RangeSelection mask survives closing its window, and reopening the tool shows the settings that made it
- Tool previews now show the MASKED result rather than the whole image changing
- A mask is cleared whenever a genuinely different image is loaded, and the filename reads [MASK ACTIVE] while one is live
- The mask overlay is drawn at display size rather than onto all 26 megapixels
- Added a MAGNIFIER to the toolbar - a panel showing the spot under the pointer closer, without zooming the view
- Added a BEFORE/AFTER COMPARE button, instant after the first use
- Added a red CLOSE IMAGE button to the Editor toolbar
- Added zoom in and zoom out buttons to the Editor toolbar
- Added File > RECENT IMAGES, the last ten you opened, surviving a restart
- The frame list survives closing the app, with Restore Last Session to bring it back
- Added Save Image alongside Save Image As, writing straight back over the file after confirming
- File menu now offers all four frame types plus Smart Import Files and Folder
- Added Clear Siril Work Files, in Settings and on the Maintenance tab
- Added a target coordinates box to the Image Solver, and the same box to SPCC
- The target box takes the object's NAME as well as coordinates - M42, NGC 7000, Rosette Nebula
- Plate solving now reads OBJCTRA/OBJCTDEC as well as RA/DEC and CRVAL
- Added a Licence Panel for the RC-Astro tools, using their account system - one code activates every product
- Added Check Version and Update CLI buttons for the RC-Astro CLI, and a Compute Device choice
- Added a device BENCHMARK button - it times BlurXTerminator on every compute device and saves the fastest
- The Xterminator tabs are built from the CLI's own layout description, and gained an ML Version dropdown
- BlurXTerminator gained its Lunar / Planetary toggle, new with ML5
- Help > Check Engine Versions reports all three engines against their latest releases
- What's New now shows the whole history in its own window, and Help windows open centred on the app
- Narrowband Normalization, Astro Color Mixer and Color Saturation have their own preview panels
- Multiscale Local Contrast now accepts mono images
- The Color Masks Strength slider is no longer linear, matching the original PixelMath
- Blemish Blaster no longer asks whether to save after every Apply
- Undo and Redo are now instant across the last few steps, and name the tool in their tooltips again
- Opening an image that has been shown before reuses what was rendered rather than re-reading the file
- Mini Viewers reuse their rendered images too, so swapping is quick in both directions
- Mini Viewers gained a Linked / Unlinked choice and the same icon toggles the Editor uses
- Mini Viewer toolbars use the app's drawn icons throughout instead of emoji and text
- Window title bars are forced to a solid dark colour on Windows 11
- Flips and rotations appear immediately and are much quicker, with the readout and crop overlay following
- Applying a tool no longer throws away your zoom
- The screen stretch works in float32, roughly 8x faster, and no longer repairs data that needs no repair
- Turning the screen stretch OFF no longer costs more than leaving it on
- The metrics columns fill DURING a run instead of all at once at the end
- The readout bar and Console header show CPU, RAM, GPU and the engine's thread count
- Toolbar icons are drawn with Pillow at run time instead of unicode arrows, and grouped by what they do
- Tooltips appear as a bubble under the pointer after a short pause, name the tool, and no longer hang off the sidebar
- Save prompts, message boxes and file dialogs always appear in front of whatever tool window is open
- A Siril crash now says so, rather than reading as an ordinary failure
- The scratch folder is now PhotonWorks_Temp, and choosing it directly no longer nests it inside itself
- Fixed: the red mask overlay vanished the moment any tool was opened
- Fixed: a mask was applied on Apply and then immediately undone on screen
- Fixed: with a mask active, opening any tool brightened stars across the whole frame
- Fixed: opening a previously-viewed image left the previous image's name in the toolbar
- Fixed: closing a tool after applying it snapped the view back to 1:1
- Fixed: Blemish Blaster repairs undid themselves
- Fixed: a Mini Viewer stayed blank when an image was loaded into it a second time, or after a swap
- Fixed: after a swap a Mini Viewer could show the image far too large or small while still reporting Fit
- Fixed: after a flip or rotate the hover Readout could report that values were not available
- Fixed: the processing history file appeared in the Stacking Profiles dropdown as a profile
- Fixed: saving a FITS whose header contains lowercase keywords failed
- Fixed: menu clicks fell through to whatever sat underneath, and the Tools submenu stayed on screen
- Fixed: the Image Solver and SPCC dialogs were slow to open - the coordinate check reached the online name resolver
- Restored the xisf version shim, without which a built .exe dies at startup

## v1.0.3

- Added HISTOGRAM TRANSFORMATION - the PixInsight-style stretch, with black, midtone and white handles under a live RGB histogram
- Every option Siril's stack command accepts is now available - all five methods, all eight rejection types and every flag
- Added FRAME FILTERING - let Siril leave the worst frames out by FWHM, roundness, background, star count or quality
- Registration now offers everything Siril's register command accepts, including all six interpolation methods
- Star detection now exposes search radius, roundness, PSF fit iterations, Gaussian or Moffat, and relaxed star checks
- Star detection resets to Siril's defaults at the start of every run, so nothing carries over between sessions
- Drizzle restored, on the registration step where Siril actually implements it, with pixel fraction and kernel choice
- Drizzle on OSC data now works properly as Bayer drizzle, and applies with Mosaic and Intersection framing too
- Added a registration output scale (0.1 to 3), which is what sets the drizzle factor
- Added Centre of Gravity framing, Siril's fourth framing method
- Added Fuji X-Trans autofocus correction and the choice to calibrate excluded frames
- Cosmetic correction passes -cfa for Bayer data, with cold and hot sigma thresholds exposed
- Every stacking run ends with a timing summary - each step with its duration, frame count and share of the total
- Added an optional OFFLINE STAR CATALOGUE download, or point the app at a copy you already have
- Added a General / Updates tab to Advanced Settings, holding the app's own behaviour
- Added Remember window size and position - turn it off and the app always opens maximized
- Added a warning on exit when a session has results you never saved, with a Don't warn me again option
- Added Reset All Settings, which leaves your profiles and images alone
- Added an interface size adjustment, scaling buttons, text and dialogs relative to your Windows setting
- Temp files are kept one folder per session and cleared automatically at startup, with 0 to 3 sessions kept
- You can now move the temp scratch folder and the Siril working folder onto another drive
- Clear Temp Files now clears every session at once, for when you want the space back immediately
- Advanced Settings tabs now scroll, so the window need not be as tall as its longest tab
- Tool windows are kept on screen - a tall dialog is moved up, and shortened only if it still would not fit
- Tool previews can be zoomed and panned - wheel to zoom, drag to pan, Fit or double-click for the whole image
- The Process Tools sidebar reopens the same groups you had open when you last closed the app
- Update notices are now a small box under About / Credits instead of a dialog opening over the app
- The frame list's column headers explain themselves on hover - FWHM, Roundness, RMSE, BG Noise and the rest
- Renamed the Image Viewer tab to IMAGE EDITOR, and the Mini Viewer's swap button to Swap with Editor
- Reorganised Core Parameters around what actually changes between targets
- Moved Pre-Stacking Correction into the Calibration tab and removed the now-empty Cosmetic tab
- Split Channels no longer labels the boxes Ha/OIII in full RGB mode, where those names are not true
- Split Channels: synthetic Luminance can be built from equal weights, Rec.709 or CIE L*
- Added a Licensing section to About / Credits - GPL v3, with Siril bundled unmodified
- REMOVED Upscale x2 before stacking - the Output scale control does the same job better at registration
- Fixed: three of the five stacking methods wrote a command Siril could not run
- Fixed: the registration interpolation choices sent the wrong algorithm
- Fixed: the Equalize CFA switch sent the cosmetic correction flag instead
- Fixed: the drizzle switches used a flag that does not exist on Siril 1.4's stack command
- Fixed: stacking options were sent to methods that reject them
- Fixed: the debayer override now restores your Siril setting on every failure path, including a crash mid-run
- Fixed: a thread-safety bug in the Blink Tool when changing the stretch mode
- Fixed: two scrollbars appeared on the Light and Calibration tabs
- Fixed: the unsaved results warning on exit counted tool scratch files as results

## v1.0.2

- Added an opt-in auto-updater, ready for public releases - set UPDATE_REPO and it switches itself on, leave it empty and it does nothing at all
- Added Correct Magenta Stars - removes the magenta fringing chromatic aberration leaves around stars (Colour Tools)
- Improved the console - Siril progress spam is filtered out, cutting a typical run by about 90 percent
- Fixed Copy Log producing an empty clipboard, and added a Clear Log button beside it
- Added RGB Stars to Narrowband - puts real broadband star colour onto a narrowband image (Star Tools)
- Added Sensor Un-Mix to Split Channels - inverts your sensor's Ha/OIII crosstalk instead of a fixed channel split (linear data only)
- Added the Foraxx palette to Combine LRGB - blends per pixel from the data rather than assigning channels (stretched data only)
- Added Warmth, Tint and Hue Rotation to the Camera RAW Editor, all luminance-preserving
- Added tabs to the Camera RAW Editor so 17 sliders no longer make one very tall window
- Renamed Ratio Palette Synthesis to Dual-Band to SHO - the old name implied a choice of palettes it does not offer
- Improved the Camera RAW preview - Clarity, Texture and Sharpen now show the structure scale Apply will actually produce
- Improved SPCC feedback - a short summary of the fit quality and star counts now prints at the end of a run
- Fixed stacking failing outright when a single master dark, flat or bias was used instead of raw calibration frames
- Fixed a crash when a picker-based tool was opened with an empty viewer and then closed
- Fixed Combine LRGB, NB to RGB Stars, Screen Stars and RGB Stars to NB not explaining that an empty viewer is fine for them
- Fixed the Blink Tool having no tooltip, and widened the file list's Filter column

## v1.0.1

- Added Split Channels - splits an image into separate mono channels, with a duo-band Ha/OIII mode
- Added Pixel Math - applies an arithmetic expression to every pixel, and can combine several open images into a new one
- Added Multiscale Local Contrast - boosts contrast only at the structure sizes you select
- Added Ratio Palette Synthesis - turns a duo-band image into a gold-and-teal SHO-style palette
- Added 90 degree rotation, clockwise and anticlockwise, beside Flip H/V
- Added a Show Background toggle to Background Extraction and to GraXpert
- Added a Match Luminance to Colour slider to Combine LRGB
- Added an OIII from control to Ratio Palette Synthesis - green only, or the average of green and blue
- Added an in-dialog mask preview to Color Masks
- Added a faint app-logo watermark to the empty main viewer and file list
- Added multi-file opening everywhere - the Open button, drag and drop, the file list, and auto-open after stacking
- Added Enter as a shortcut to open the selected rows in the file list
- Added a Save As button to the Mini Viewer toolbar
- Rebuilt the Process Tools sidebar as collapsible drawers with plain buttons
- Rebuilt Combine LRGB's channel selection, and applied the same simpler picker to NB to RGB Stars and Screen Stars
- Moved the information panel and console into a single bottom bar, matched in height
- Moved settings and saved profiles to a fixed per-user folder in AppData
- Improved Multiscale Local Contrast, Dark Structure Enhance and Dust Lane Enhancer with a side-by-side preview layout
- Improved SCNR's Preserve Lightness to match Bill Blanshan's Modified SCNR v4
- Improved Combine LRGB and NB to RGB Stars so sources are read-only and nothing overwrites a master
- Improved the Save Result dialog - the Overwrite button now names the file it would replace
- Improved the stars-only image from StarXTerminator - it now opens straight into a Mini Viewer with STF off
- Sped up Multiscale Local Contrast, Star Reduction's preview, and 90 degree rotation
- Fixed SCNR producing magenta artefacts on stars and bright areas
- Fixed the SCNR Amount slider being permanently stuck at 0.70
- Fixed Combine LRGB needing every source picked twice, and going mono when a Luminance channel was added
- Fixed Mini Viewers appearing to duplicate when the app was minimized and restored, and the crash when closing one
- Fixed Mini Viewers not appearing in the source dropdowns
- Fixed the white flash when dialogs and the main window open
- Fixed Ratio Palette Synthesis losing saturation on Apply, showing too little teal, and appearing to apply twice
- Fixed a blue halo in the sky around every object
- Fixed a startup crash and the watermark never staying visible
- Fixed rotation and flip corrupting the working image
- Removed the collapsible left stacking sidebar - it worked, but flashed on collapse and is parked for now

## v1.0.0

- Rebuilt the app as a single window instead of a separate popup for the viewer
- Added Dark Structure Enhance and Dust Lane Enhancer for bringing out dust and dark structure
- Added Blemish Blaster, Star Stretch and NBtoRGB Stars, ported from Franklin Marek's Seti Astro scripts
- Added VeraLux HyperMetric Stretch, ported from Riccardo Paterniti's original
- Added RangeSelection Mask and an app-wide masking system, so any tool can be applied through a mask
- Added Astro Color Mixer - hue-targeted colour and luminance adjustment
- Added Camera RAW Editor, expanded from the original Brightness/Contrast/Sharpen tool
- Added LinearFit, Background Neutralization and Color Saturation
- Added Bin/Downscale, Flip Horizontal/Vertical, and a Preview Region tool
- Added Image Solver as a standalone plate-solve tool alongside SPCC
- Added the Subframe Selector dashboard with Stars, FWHM and Roundness charts, usable before stacking
- Added an Analyze Frames button and a Roundness column to the file list
- Added a Readout bar below the viewer showing pixel values under the cursor
- Added Mini Viewer windows, with Swap, minimize-to-icon and drag-and-drop loading
- Added the ability to rename images within the app, so channels can be labelled Ha, OIII or SII
- Added XISF support throughout - open, edit and save
- Added drag-and-drop image loading to the main viewer and every Mini Viewer
- Added SII + OIII as a filter pair for dual-band extraction, alongside Ha + OIII
- Added mono image support to every tool where it makes sense
- Added apply-this-crop-to-other-open-images to the Crop tool
- Added auto-align to Combine RGB, and channel pickers that can take any open image
- Split the Process Tools sidebar into five labelled groups
- Renamed Combine RGB to Combine LRGB / Narrowband, and Compare to Mini Viewer
- Changed every toggle switch, radio button and checkbox from blue to green when enabled
- Improved tooltips app-wide - larger hover targets, no flicker, and none missing
- Improved live previews across 15 dialogs so they match what Apply actually produces
- Improved the metrics table with a real per-frame noise measurement
- Fixed a widespread crash affecting 48 places across nearly every tool
- Fixed Debayer silently corrupting mono images if left on from a previous load
- Fixed white flashes when dialogs, the main window and the Subframe Selector open
- Fixed windows taking several seconds to close
- Fixed the Save button greying out after every save
- Fixed dark haloing around stars during noise-aware stretching
- Fixed the built .exe's own icon not showing in the taskbar and title bar
- Fixed the Blink Tool re-reading every file from disk on each toggle, and needing Debayer set manually
- Fixed the metrics table showing nothing after a stack, and the first frame never getting a Roundness reading
- Fixed two stacking bugs found in real runs - darks not shared across filters, and a mismatched sequence
- Fixed the STF Stretch toggle not actually skipping the stretch when turned off
- Removed Noise-Aware Stretch after measurement showed it was not earning its place
- Ran a full code audit with two static analyzers and fixed everything they found

## Beta 12

- Added a MINI VIEWER - a second, independent viewer window for looking at another image side by side
- Added COLOR MASKS - Bill Blanshan's hue-based colour masking, ported from his own PixelMath source
- Color Masks now offers 12 colours instead of 6, with the original 6 being Bill Blanshan's own

## Beta 11

- GHS, Curves, Star Reduction and Combine RGB windows live-resize to fit whatever controls are visible

## Beta 10

- Added COMBINE RGB - combines separate mono masters into one colour image, with an optional Luminance

## Beta 9

- GHS: added PixInsight's own graphical display - a live histogram and transformation curve with hover readout
- GHS: Stretch Amount is now parametrized as PixInsight's Stretch factor, giving finer control at the low end
- GHS: added Low/High Clip Proportion for the Linear type, with a live readout of what would clip

## Beta 8

- Rebuilt STAR REDUCTION from scratch - the previous version's own approach was genuinely broken
- Fixed: Star Reduction auto-filled the wrong image into Original Image after running StarXTerminator

## Beta 7

- Added SCREEN STARS - recombines a starless image with a processed stars-only one, per Blanshan and Cranfield

## Beta 6

- Added Star Reduction - shrinks/dims stars without removing them, built from scratch (masked morphological erosion), with live preview

## Beta 5

- Added a native GHS tool built from the published specification (David Payne and Mike Cranfield)
- This replaces the Siril-scripted GHS, Modified Arcsinh, Histogram Transformation and Linear Stretch tools

## Beta 4

- Added Narrowband Normalization (Bill Blanshan & Mike Cranfield's process) and Apply Stretch tools to the image viewer, both with live preview
- STF Stretch now works like PixInsight's own STF - computes its curve once and reuses it, instead of recalculating on every render
- Fixed several image viewer display bugs found along the way (linear data handling, raw sub-exposure bit depth, toolbar/tool-dialog coordination)

## Beta 3

- Added Undo/Redo and a manual Save button to the image viewer
- Image viewer can now be opened independently of the frame list, with drag & drop support for adding frames
- Added a global crash handler, temp file cleanup, and a startup check for missing tool paths
- Added an STF Stretch toggle to view the raw linear data vs the auto-stretched preview

## Beta 2

- Added GraXpert integration (Background Extraction and Denoising)
- Added a Crop Tool with direct Python/astropy cropping
- Moved SPCC from an automatic step to a manual, on-demand one

## Beta 1

- Added RC-Astro Xterminator Tools (BlurXTerminator, StarXTerminator, NoiseXTerminator)
- Added manual Background Extraction
