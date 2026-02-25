# Computer Graphics — Complete Study Material

# UNIT 1 — Introduction to Computer Graphics
## 1.1 What is Computer Graphics?

**Simple Take:** Computer Graphics is the field of using a computer to create, manipulate, and display visual content — from a simple line on screen to a full CGI movie.

**Technical Definition:** Computer Graphics is a sub-discipline of Computer Science concerned with the algorithmic generation, representation, manipulation, and rendering of visual data using computational hardware and software. It involves computations, creation, and manipulation of data.

Key terms you must know:
- **Pixel (Picture Element / pel):** The smallest addressable graphical unit on a computer screen. Every image is made up of a grid of pixels.
- **Rasterization:** The special procedure that determines which pixels will provide the best approximation to a desired picture or graphics object.
- **Scan Conversion:** The process of representing a continuous picture or graphics object as a collection of discrete pixels.

## 1.2 Advantages of Computer Graphics

- **Most effective communication medium between human and computer.** Before CG, all interaction with computers was through typed text commands (CLI). CG introduced the ability to point, click, and visually manipulate — e.g., the Xerox Star (1981) was the first commercial computer to replace text commands entirely with graphical icons and a mouse.

- **Can produce pictures of both real-world and synthetic objects.** CG is not limited to photographing reality — it can render things that don't physically exist. Example: Pixar's *Coco* (2017) used Renderman to render the Land of the Dead, a fully fictional city with millions of lights that would be impossible to build or film physically.

- **Enables moving pictures and animation.** Unlike static diagrams, CG allows time-varying visual output. Example: NVIDIA's Omniverse platform can simulate and animate entire factory environments in real time — BMW uses it to animate and validate their manufacturing line before physically constructing it.

- **Motion dynamics** — users can move objects and observe them from any angle in real time. Example: In Autodesk Maya, an animator can grab a character's arm and drag it, and the full skeleton follows through inverse kinematics — the software continuously recomputes geometry and renders the update live.

- **Update dynamics** — shape, colour, material, and other object properties can be changed interactively. Example: Adobe Substance 3D Painter lets artists repaint a car's surface texture in real time; the GPU re-renders photorealistic reflections and shadows instantly as the colour changes.

- **Provides audio-visual feedback simultaneously.** Modern graphics systems integrate GPU rendering with audio chips on the same pipeline. Example: Unreal Engine 5's audio system (MetaSounds) spatially positions sound in 3D space synced to the rendered scene — when an explosion happens on screen, the audio direction and reverb update in real time to match the camera position.

## 1.3 Applications of Computer Graphics

### 1. Graphical User Interface (GUI) — The Origin

- **Before GUI:** All computers ran on CLI — users typed every command. No icons, no mouse, no windows.
- **Origin — Xerox PARC (1973):** Built the **Xerox Alto** — first computer with a graphical desktop, overlapping windows, icons, and a mouse. Never sold commercially, but introduced the **WIMP model (Windows, Icons, Menus, Pointer)** and bitmap graphics where every pixel was CPU-controlled.
- **Steve Jobs (1984):** Visited Xerox PARC in 1979, recognised what Xerox had failed to commercialise, and took the idea to Apple. Launched the **Macintosh** — first mass-market GUI computer. Ran on a Motorola 68000 CPU, 512×342 raster display, and **QuickDraw** (Apple's 2D graphics library for all pixel-level rendering). Icons were 32×32 bitmaps. First time a non-technical person could use a computer.
- **Bill Gates (1985):** Launched **Windows 1.0** on top of MS-DOS using **GDI (Graphics Device Interface)** — Microsoft's drawing API. Used tiled windows (non-overlapping). Gates' position: GUI should be an open platform — licensed Windows to any PC manufacturer.
- **The Lawsuit (1988–1994):** Apple sued Microsoft (*Apple v. Microsoft*) claiming Windows stole the Macintosh's "look and feel." Court ruled against Apple — GUI elements were either already licensed to Microsoft, not copyrightable as functional concepts, or borrowed from Xerox PARC by Apple itself. Established that **GUI concepts cannot be owned**, opening the market to all.
- **Legacy:** Led to the 1990s PC boom, Netscape Navigator (1994 — first graphical web browser), and every modern smartphone OS. All current GUI frameworks — **Qt** (VLC, Maya), **GTK** (GIMP, GNOME), **Apple UIKit** (iOS), **Android Canvas API**, **Microsoft WPF** (Windows 11) — descend directly from Xerox PARC's raster windowing model.

- **Tools Used:** Qt, GTK, Apple Core Graphics / UIKit, Android Canvas API, Microsoft WPF / DirectComposition, Electron (cross-platform desktop apps — used by VS Code, Slack, Figma desktop).
- **Built Using CG:** Windows 11 desktop shell, macOS Finder, Android home screen, iOS SpringBoard, GNOME Linux desktop, Google Chrome browser UI, VS Code editor interface.
- **Research Area:** Reducing UI rendering latency (Google's Jank-free rendering research), accessibility — WCAG contrast standards for visually impaired users, adaptive layouts across foldable and multi-screen devices.

### 2. Plotting and Charting

- **What it is:** Converting numerical data into visual representations — bar charts, line graphs, pie charts, scatter plots, heatmaps, histograms — so patterns and trends become immediately visible.
- **Tools Used:** Matplotlib and Seaborn (Python — used in data science), D3.js (JavaScript — interactive web charts), Tableau (business intelligence), Microsoft Power BI, Google Charts, Plotly (interactive scientific charts), Chart.js.
- **Built Using CG:** Tableau dashboards used by Netflix to analyse which content regions perform best; Matplotlib-generated graphs in COVID-19 research papers published in *Nature* and *The Lancet*; D3.js powering The New York Times interactive election results visualizations; Bloomberg Terminal's real-time financial chart rendering.
- **Research Area:** High-dimensional data visualization (t-SNE and UMAP plots for machine learning embeddings), real-time chart rendering for live stock market feeds, accessible colour palettes for colour-blind users (IBM's Color Blind Safe palette, built into Observable Plot).

### 3. Office Automation and Desktop Publishing (DTP)

- **What it is:** Creating, formatting, and printing professional documents — reports, magazines, newspapers, books — combining text, images, tables, and graphical layouts.
- **Tools Used:** Adobe InDesign (industry-standard layout), Microsoft Word, LaTeX (mathematical/scientific publishing), Scribus (open source DTP), Canva (online design), Adobe Illustrator (vector graphics for print).
- **Built Using CG:** *Vogue* and *The New York Times* print editions (laid out in InDesign); every academic paper in IEEE, ACM, and Springer journals (written in LaTeX); Apple's product packaging design (Adobe Illustrator); Oxford University Press textbooks.
- **Research Area:** Font hinting and sub-pixel rendering for screen legibility (Microsoft's ClearType, Apple's Quartz text rendering), automatic intelligent layout engines (Adobe's content-aware layout AI), print-to-screen colour fidelity (ICC colour profile management).

### 4. CAD/CAM — Computer-Aided Design and Manufacturing

- **What it is:** Using computers to design physical objects in 2D/3D before manufacturing them — replacing paper blueprints entirely. CAM extends this by directly driving manufacturing machines (CNC mills, 3D printers) from the digital design.
- **Tools Used:** AutoCAD (2D/3D drafting — used across all engineering fields), SolidWorks (mechanical parts and assemblies), CATIA (aerospace and automotive — Dassault Systèmes), Fusion 360 (product design + CAM), Revit (architecture — Building Information Modelling), ANSYS (structural and fluid simulation).
- **Built Using CG:** Boeing 777 — designed entirely in CATIA, the first commercial aircraft to be designed without physical blueprints (called the "paperless airplane"); Tesla Model S body panels modelled in SolidWorks/CATIA; Burj Khalifa's structural engineering designed in Revit and AutoCAD; every Intel CPU layout designed in electronic design automation (EDA) tools like Cadence Virtuoso.
- **Research Area:** Generative design using AI (Autodesk Generative Design — an algorithm explores thousands of design iterations and proposes the lightest structure that meets strength requirements), real-time FEA (Finite Element Analysis) rendering, immersive design review in VR (engineers walk through a full-scale virtual car before physical prototyping).

### 5. Simulation and Animation

- **What it is:** Creating time-varying visual representations of real or fictional phenomena — character animation, physics simulations, fluid dynamics, crowd simulations — for film, gaming, science, and engineering.
- **Tools Used:** Autodesk Maya (character rigging and animation — industry standard for film), Houdini (procedural VFX, fluid and destruction simulations — SideFX), Blender (open source 3D — used commercially by studios), Unreal Engine 5 (real-time rendering with Nanite and Lumen), Unity, Pixar's RenderMan (offline photorealistic rendering), MATLAB Simulink (engineering system simulation).
- **Built Using CG:** *Toy Story* (1995, Pixar) — first fully CGI feature film; every frame rendered in RenderMan on a render farm of SGI workstations, each frame taking 45–90 minutes to compute. *Avatar* (2009, Weta Digital) — used proprietary motion capture with 140 cameras in a 270° rig, then reconstructed and rendered Pandora using custom volumetric rendering tools. SpaceX uses MATLAB and custom CFD (Computational Fluid Dynamics) tools to simulate Falcon 9 re-entry trajectories before every launch. NASA's Jet Propulsion Laboratory uses Unreal Engine to simulate Mars surface terrain for Perseverance rover mission planning.
- **Research Area:** Real-time neural rendering using NeRF (Neural Radiance Fields — trains a neural network to synthesize a 3D scene from 2D photographs; NVIDIA Instant-NGP can do this in seconds), real-time fluid simulation (NVIDIA FleX), AI-driven character animation (Ubisoft's research on motion matching for game characters).

### 6. Art and Commerce — Advertising and Media

- **What it is:** Creating digitally rendered artwork, product visualizations, motion graphics, and advertising content — replacing physical photography and hand-drawn art in most commercial contexts.
- **Tools Used:** Adobe Photoshop (image compositing and editing), Adobe Illustrator (vector art and logos), Cinema 4D (motion graphics — used heavily in broadcast design), Adobe After Effects (compositing and visual effects), Substance 3D Painter (physically based texture painting for 3D models), DaVinci Resolve (colour grading).
- **Built Using CG:** Apple's product launch keynote videos — iPhone and Mac renders created in Cinema 4D with photorealistic materials before physical prototypes exist; Nike's shoe campaign visuals — soles, mesh, and materials rendered in Substance Painter achieving photorealism that outperforms studio photography; Coca-Cola's "Holidays Are Coming" campaign — fully CGI truck rendered in Houdini; Marvel Studios' visual effects — Iron Man suit (Maya + Nuke compositing by ILM, Industrial Light & Magic).
- **Research Area:** Text-to-image generation (Stable Diffusion, DALL-E 3, Midjourney) — these use diffusion models to synthesize images from text prompts; Physically Based Rendering (PBR) — standard in all modern renderers (Cycles in Blender, Arnold in Maya); procedural texture synthesis using GANs.

### 7. Process Control and Industrial Monitoring

- **What it is:** Real-time graphical visualization of automated industrial systems — power grids, oil pipelines, nuclear reactors, factory floors — allowing operators to monitor sensor data and control systems through visual dashboards instead of interpreting raw numbers.
- **Tools Used:** SCADA (Supervisory Control and Data Acquisition) systems — Wonderware InTouch (Aveva), Siemens WinCC, LabVIEW (National Instruments), OSIsoft PI System (for time-series data visualization), GE iFIX.
- **Built Using CG:** Siemens WinCC drives the control room displays at nuclear power plants across Europe — operators see live animated P&ID (Piping and Instrumentation Diagrams) with colour-coded status indicators; SCADA dashboards monitor the Trans-Alaska Pipeline System (800 miles of pipeline, visualized on a single graphical overview screen); LabVIEW interfaces control the Large Hadron Collider's (CERN) magnet cooling systems; air traffic control radar screens at every major airport (built on custom real-time raster graphics systems).
- **Research Area:** Digital twins — a live 3D simulation of the physical plant that mirrors real sensor data in real time (Siemens Digital Twin, GE Digital); AR maintenance overlays using Microsoft HoloLens so a technician sees equipment diagnostics projected onto the physical machinery; predictive failure visualization using AI anomaly detection.

### 8. Cartography and Geographic Information Systems (GIS)

- **What it is:** Creating, analysing, and displaying geographic and spatial data — maps, terrain models, satellite imagery, and route overlays — from raw coordinate and altitude data.
- **Tools Used:** ArcGIS (Esri — industry standard GIS platform), QGIS (open source), Google Maps Platform (JavaScript API), Mapbox GL JS (WebGL-based vector tile rendering), NASA WorldWind, ENVI (satellite imagery analysis), Cesium JS (3D globe rendering in browser).
- **Built Using CG:** Google Maps and Google Earth — combine satellite imagery tiles, terrain elevation data (SRTM), and Street View photospheres into a continuous zoomable 3D globe rendered via WebGL; NOAA's weather forecast maps — GIS layers of atmospheric pressure, temperature, and precipitation rendered over a geographic base map updated hourly; the Johns Hopkins University COVID-19 Dashboard (2020) — built on ArcGIS Online, it visualized global case counts as a proportionally scaled dot map that became the most visited website in the world during early 2020; city planning authorities use ArcGIS to simulate how a new building's shadow will fall across neighbouring properties at different times of year.
- **Research Area:** Real-time processing of satellite imagery from Planet Labs' fleet (200+ satellites, images the entire Earth daily); lidar point cloud rendering for autonomous vehicle HD maps (Waymo, Mobileye); 3D indoor mapping (Google's indoor maps for shopping malls and airports).

### 9. Education and Training

- **What it is:** Building interactive simulations, 3D visualizations, and virtual environments to teach concepts that are difficult, dangerous, expensive, or physically impossible to demonstrate in a classroom.
- **Tools Used:** Unity (interactive learning simulations), Unreal Engine (photorealistic training environments), MATLAB (mathematical modelling and visualization), GeoGebra (browser-based geometry and calculus visualization), zSpace (AR/VR education hardware + platform), Visible Body (3D human anatomy software).
- **Built Using CG:** NASA astronaut EVA (spacewalk) training simulations built in Unreal Engine — astronauts rehearse the exact sequence of actions they will perform outside the ISS before launch; Osso VR (surgical training platform built in Unity) — used by hospitals including the Hospital for Special Surgery in New York to train orthopaedic surgeons on new implant techniques; Lockheed Martin's Prepar3D — a full flight simulation platform used by airlines (United, Delta) and military (USAF) to train pilots without ever leaving the ground; Khan Academy's interactive calculus exercises — powered by D3.js and custom WebGL shaders to render graphs that respond to student input in real time.
- **Research Area:** Effectiveness of VR vs traditional training (University of Maryland study found VR training improves retention by 75% vs. lecture); AI tutors that generate personalized visual explanations based on student progress; haptic feedback in surgical simulators to simulate tissue resistance.

### 10. Medical Imaging and Visualization

- **What it is:** Converting raw data from medical scanners (MRI, CT, X-ray, PET, ultrasound) into interpretable 2D/3D visual representations used for diagnosis, surgical planning, and research.
- **Tools Used:** ITK (Insight Toolkit) and VTK (Visualization Toolkit) — open source C++ libraries for medical image processing and 3D rendering; OsiriX / Horos — DICOM image viewers used in hospitals; Materialise Mimics — for segmenting scan data and 3D printing patient-specific surgical guides; 3D Slicer (open source surgical planning platform); NVIDIA Clara (GPU-accelerated AI medical imaging); Brainlab (surgical navigation).
- **Built Using CG:** Materialise Mimics is used by surgeons at Mayo Clinic and Johns Hopkins to segment MRI/CT scans, create 3D reconstructions of tumours and bone structures, and 3D print patient-specific surgical guides before complex operations; GE Voluson ultrasound machines render real-time 4D (3D + time) fetal models using custom GPU pipelines; NVIDIA Clara was used during COVID-19 to segment and quantify lung damage from CT scans automatically, helping radiologists process backlogs; Brainlab's AR surgical navigation system overlays a 3D MRI model onto a patient's head in the operating room, guiding neurosurgeons to tumour locations with sub-millimetre accuracy.
- **Research Area:** Google DeepMind's AI detecting over 50 eye diseases from retinal scans with accuracy matching specialist ophthalmologists; real-time intraoperative AR (augmented reality) overlays using HoloLens 2 in surgery; photoacoustic imaging — a new modality combining light and ultrasound to produce high-resolution vascular maps without radiation.

### 11. Image Processing

- **What it is:** Algorithmically modifying, enhancing, analysing, compressing, or extracting information from digital images — from smartphone camera post-processing to satellite imagery classification.
- **Tools Used:** OpenCV (open source computer vision library — C++/Python), Adobe Photoshop (manual and AI-assisted editing), MATLAB Image Processing Toolbox, PIL/Pillow (Python lightweight image manipulation), ImageJ (scientific microscopy image analysis — used in biology research), GIMP (open source editing), scikit-image (Python).
- **Built Using CG:** Instagram and Snapchat filters — face detection (Viola-Jones algorithm or deep learning via OpenCV), mesh-warping, and shader-based colour grading applied in real time at 60 fps on a smartphone GPU; Apple's Computational Photography pipeline in iPhone — every photo taken on an iPhone goes through Deep Fusion (a neural network that pixel-merges 9 frames captured before and after shutter press) and Smart HDR, all implemented on the Apple Neural Engine; satellite imagery classification — the European Space Agency's Sentinel Hub uses scikit-image and custom deep learning to classify land cover types (forests, cities, farmland) from Sentinel-2 satellite images; Waymo's autonomous vehicle perception system processes LiDAR and camera images using OpenCV and custom deep learning at 10 frames per second to detect pedestrians, vehicles, and road signs.
- **Research Area:** Computational photography (Adobe Research's content-aware fill, which uses deep inpainting to reconstruct missing regions of images); super-resolution (NVIDIA DLSS — Deep Learning Super Sampling — upscales a low-resolution rendered frame to 4K using a neural network trained on high-resolution image pairs); medical image segmentation using U-Net (a deep learning architecture designed for biomedical image segmentation at the University of Freiburg, now used universally in medical AI).

## 1.4 Display Devices (Output Devices)

### 1.4.1 Cathode Ray Tube (CRT)

**Simple Take:** An electron gun fires a beam of electrons at a phosphor-coated screen, making it glow. By steering the beam very quickly across the whole screen, you trick the eye into seeing a full picture.

**Technical Working:**
1. The **electron gun** emits a beam of electrons (cathode rays).
2. The beam passes through **focusing and deflection systems** that direct it toward specified positions on the phosphor-coated screen.
3. When the beam hits the screen, the **phosphor emits a small spot of light** at each contacted position.
4. The picture is continuously redrawn by directing the electron beam back over the same screen points quickly (this is why it's called a **Refresh CRT**).

**Advantages of CRT:**
- Operates at any resolution, geometry and aspect ratio without rescaling.
- Runs at the highest pixel resolutions generally available.
- Produces very dark blacks and highest contrast levels — suitable for dim environments.
- Best colour and gray-scale accuracy; reference standard for professional calibrations — **infinite number of intensity levels**.
- Fast response times; no motion artefacts — best for rapidly moving images.
- Less expensive than comparable display technologies.

**Disadvantages of CRT:**
- Gaussian beam profile produces images with **softer edges** — not as sharp as LCD at native resolution.
- All colour CRTs produce annoying **Moiré patterns**.
- Subject to **geometric distortion** and affected by magnetic fields.
- Not suitable for very brightly lit environments.
- Some have a rounded/spherical screen.
- Emits electric, magnetic, and electromagnetic fields — health controversy.
- Large, heavy, bulky; consume a lot of electricity and produce a lot of heat.

### 1.4.2 Raster Scan Display

**Simple Take:** Like reading a book — the electron beam goes left to right, line by line, from top to bottom. Each pixel's colour is stored in memory (the frame buffer) and painted on screen row by row.

**Technical:**
- The electron beam is swept across the screen one row at a time, **from top to bottom**.
- As the beam moves across each row, its **intensity is turned on and off** to create a pattern of illuminated spots.
- Picture definition is stored in a memory area called the **Refresh Buffer** or **Frame Buffer** — this holds the set of intensity values for all screen points.
- Stored values are retrieved and "painted" on screen **one scan line at a time**.
- Each screen point is a **pixel (picture element or pel)**.
- At the end of each scan line, the beam returns to the left side for the next line (**horizontal retrace**).
- After the last line, the beam returns to the top-left (**vertical retrace**).

### 1.4.3 Random Scan (Vector Scan) Display

**Simple Take:** Instead of scanning every single pixel, the beam is steered directly to draw only the lines and shapes. Like a robotic pen that only goes where it needs to draw.

**Technical:**
- Also called **vector display**, **stroke-writing display**, or **calligraphic display**.
- The electron beam is directed **only to the parts of the screen where the picture is to be drawn**, rather than scanning row by row.
- Picture definition is stored as a set of **line-drawing commands** in memory referred to as the **refresh display file**.
- The system cycles through the display file, drawing each component line in turn, then cycles back to the first line.
- Designed to draw all component lines **30 to 60 times per second** to avoid flicker.

**Difference between Raster Scan and Random Scan:**

| Basis | Raster Scan | Random Scan |
|---|---|---|
| Electron Beam | Swept across screen row by row, top to bottom | Directed only to parts of screen where picture is drawn |
| Resolution | Poor — produces zigzag (jagged) lines as discrete point sets | Good — produces smooth lines; CRT beam follows line path directly |
| Picture Definition | Stored as set of intensity values for all pixels in a frame buffer | Stored as set of line-drawing instructions in a display file |
| Realistic Display | Well-suited for realistic display of scenes with shadows and colour | Designed for line drawing; cannot display realistic shaded scenes |
| Drawing Method | Screen points/pixels used to draw image | Mathematical functions used to draw image |

### 1.4.4 Plasma Display

**Simple Take:** Each pixel is a tiny neon-xenon gas cell. Apply voltage → gas becomes plasma → emits UV → excites phosphor → you see colour. Like thousands of tiny neon signs packed into one screen.

**Technical:**
- Each pixel is illuminated by a tiny bit of **plasma or charged gas**, like a tiny neon light.
- Contains a grid of cells where **gas reacts with phosphors** in red, green, or blue sub-pixels → produces over 16 million colours.
- Plasma displays are **thinner than CRT** and **brighter than LCD**.
- Flat (unlike the slightly curved CRT screen) → **free of edge distortion**.
- Offer a very **wide viewing angle** unlike many LCDs.
- Available in sizes up to **60 inches** for home theatre and HDTV.

**Advantages:**
- Larger screen size availability.
- Better contrast ratio and ability to render **deeper blacks**.
- Better colour accuracy and saturation.
- Better **motion tracking** — little or no motion lag in fast-moving images.

**Disadvantages:**
- More susceptible to **"burn-in" or "screen burn"** of static images.
- Requires more power — **more heat** produced than LCDs.
- Does **not perform well at higher altitudes**.
- **Shorter display lifespan** than LCD.

### 1.4.5 LCD (Liquid Crystal Display)

**Simple Take:** An LCD doesn't make its own light. It has a backlight behind it, and liquid crystals in the middle that twist or untwist to let light through (or block it) pixel by pixel.

**Technical:**
- Combination of two states of matter — **solid and liquid** — using liquid crystals.
- Composed of several layers: **two polarized panel filters**, electrodes, liquid crystals, a colour filter, and front/rear glass.
- Light is projected from a lens onto a layer of liquid crystal. Electric current flowing through the crystal creates a grayscale image; combined with a colour filter it produces a colour image.
- **Much thinner** than CRT technology.
- Used in laptops, TVs, cell phones, portable video games.

**Advantages:**
- Produces very **bright images** due to high peak intensity — suitable for brightly lit environments.
- Produces considerably **lower electric, magnetic, and electromagnetic fields** than CRT.
- Consumes **less than 1/3rd the power** of a comparable CRT.
- Life span: **50,000–100,000 hours**.
- Screen size: **13–57 inches**.
- Viewing angle: **up to 165°**.

**Disadvantages:**
- **Aspect ratio and resolution are fixed**.
- **Lower contrast than CRT** due to poor black-level.
- **Slow response times** result in severe motion artefacts and image degradation for moving or rapidly changing images.

### 1.4.6 Plotters

**Simple Take:** A plotter is like a robotic pen that draws directly on paper. Unlike printers that spray ink dot by dot, plotters draw **continuous lines** — perfect for technical blueprints and engineering drawings.

**Technical:** A printer designed for **printing vector graphics**. Instead of printing individual dots, plotters **draw continuous lines** using pens or markers. Available in various designs, primarily used for large-format prints.

**Types of Plotters:**

1. **Flatbed Plotter:** Writing pen moves in both X and Y directions across a flat surface; paper is placed stationary. Pen can be of different sizes and colours.

2. **Drum Plotter:** A drum/cylindrical surface rotates in the vertical direction while the pen moves in the other axis. Width of output is limited by drum width; no limit to paper length.

3. **Pinch Roller Plotter:** Paper is placed on a mechanism with pinch rollers; paper moves in one direction while the pen moves in another.

4. **Electrostatic Plotter:** Produces images using **raster graphics** rather than vector graphics. Uses a toner ink attracted to high-voltage charges on paper. Lower quality than pen plotters but faster and more economical.

5. **Inkjet Plotter:** Liquid ink is sprayed on paper. Uses two technologies:
   - **Thermal:** Heating element disperses droplets when high current is passed.
   - **Piezo-electric:** Pressure releases ink when current passes through piezo-electric material.

6. **Cutting Plotter:** Uses **knives** instead of pens to cut vinyl, paper, or Mylar sheets for signs, logos, and advertising designs.

**Applications of Plotters:** CAD drawings, architectural blueprints, building plans, line art, charts, circuit layouts, banners, billboards, geographical layouts, textile printing.

### 1.4.7 Printers

**Simple Take:** A printer takes digital data and produces a hard-copy output on paper.

**Two broad categories:** 2D Printers (print text/graphics on paper) and 3D Printers (create physical objects).

#### Impact Printers

**1. Dot-Matrix Printer:**
- Print heads contain **9 to 24 pins** — pins produce patterns of dots to form characters.
- 24-pin produces much better quality than 9-pin (more pins = clearer letters).
- Pins strike the ribbon as the mechanism moves **left-to-right and right-to-left**.
- Can produce **colour output** by changing the ribbon.
- Speed: **100–600 characters/second**; **inexpensive**.

**2. Daisy-Wheel Printer:**
- Print mechanism looks like a **daisy** — at the end of each "petal" is a fully formed character.
- A hammer strikes a petal against the ribbon → character prints.
- Produces **typewriter-quality** solid-line print.
- Speed: slow — **25–55 characters/second**.

**3. Line Printers (Line-at-a-time printers):** Used where enormous amounts of material are printed — character-at-a-time printers are too slow for business use.

- **Drum Printer:** A solid cylindrical drum with raised characters in bands on its surface. Number of print positions across the drum = positions available on page (typically 80–132). Speed: **300–2000 lines/minute**.
- **Chain Printer:** Uses a chain of print characters wrapped around two pulleys. One hammer per print position. Speed: **400–2500 lines/minute**.
- **Band Printer:** Similar to chain printer but uses a steel **band** divided into 5 sections of 48 characters each. Hammers mounted on a cartridge that moves across paper. Font styles easily changed by replacing the band.

#### Non-Impact Printers

**4. Inkjet Printer:**
- Forms images using **tiny droplets of ink** sprayed from nozzles through an electrical field.
- Electrically charged droplets guided by deflecting plates (positive upper, negative lower).
- Speed: approximately **250 characters/second**.
- Can use **multiple nozzles** for CMYK full-colour printing.
- Ink absorbed into paper and dries instantly.
- Some printers use all-in-one cartridges; others allow individual colour replacement.

**5. Laser Printer:**
- Works like a **photocopy machine** using a laser beam.
- **Process:** Laser beam → mirror → drum (with special coating) → toner (ink powder) sticks to discharged areas → paper rolls by → toner transfers → hot roller fuses toner to paper.
- Uses **buffers** that store an entire page before printing.
- Speed: home printers ~**8 pages/minute**; fast printers ~**21,000 lines/minute** (~437 pages/minute at 48 lines/page).
- **Advantages:** Speed, efficiency, high quality, quiet, capable of colour.
- **Disadvantages:** Costly; high maintenance/repair charges; emits small amounts of **ozone** (hazardous to health).

**Other 2D Printer Types:**
- **LED Printer:** Similar to laser but uses **light-emitting diodes** rather than a laser to produce the image on the drum.
- **Thermal Printer:** Pushes **heated pins** against heat-sensitive paper. Used in calculators, ATMs, and cash registers.
- **Dye-Sublimation Printer:** Uses heat to transfer dye to paper, fabric, plastic cards. Often used for **photos or ID cards**.

**2D Printer Characteristics:** Colour capability, resolution (DPI), quality of type (letter/near-letter/draft), speed (PPM), monthly duty cycle, warm-up time, all-in-one capabilities (scanner + copier + fax), ports (USB/Ethernet/wireless/networking).

#### 3D Printers

**Simple Take:** Instead of printing on paper, a 3D printer deposits layers of material on top of each other to build a physical 3D object — called **additive manufacturing**.

**Types of 3D Printing:**
1. **DLP (Digital Light Processing):** Liquid plastic resin hardens quickly when exposed to large amounts of light.
2. **DMLS (Direct Metal Laser Sintering):** Fuses powdered metal and alloy with a high-wattage laser.
3. **EBM (Electron Beam Melting):** Uses metal powder and an electron beam to melt and form a metal part layer by layer.
4. **FDM (Fused Deposition Modeling):** Creates parts layer by layer using engineering-grade thermoplastics.
5. **LS (Laser Sintering):** Uses a CO₂ laser to heat and fuse durable thermoplastic powder.
6. **LOM (Laminated Object Manufacturing):** Layers of adhesive-coated paper fused by heat and pressure, then cut by a laser.
7. **PolyJet:** Uses jets to cure thin layers of liquid photopolymer with UV energy.
8. **SLA (Stereolithography):** Builds parts layer by layer using a UV laser to solidify liquid photopolymer resins.

## 1.5 Input Devices

### 1. Keyboard
**Simple Take:** The most basic input device — you type and the computer receives characters.

**Technical:** Most common and popular input device. Layout like a traditional typewriter with additional keys for extra functions. Sizes: 84 keys, 101/102 keys, 104 keys, 108 keys (for Windows/Internet).

**Key categories:**
| S.No | Key Type | Description |
|---|---|---|
| 1 | **Typing Keys** | Letter keys (A–Z) and digit keys (0–9) — standard typewriter layout |
| 2 | **Numeric Keypad** | 17 keys for numeric data entry or cursor movement — same layout as calculators |
| 3 | **Function Keys** | 12 keys (F1–F12) arranged in a row at top — each has a unique specific purpose |
| 4 | **Control Keys** | Four directional arrow keys + Home, End, Insert, Delete, Page Up, Page Down, Ctrl, Alt, Esc |
| 5 | **Special Purpose Keys** | Enter, Shift, Caps Lock, Num Lock, Space bar, Tab, Print Screen |

### 2. Mouse
**Simple Take:** A pointing device — move it around to move the cursor on screen; click to select.

**Technical:** Most popular pointing device. A cursor-control device with a small palm-size box with a round ball at its base (mechanical) or optical sensor (modern) that senses movement and sends signals to the CPU. Has left button, right button, and a scroll wheel.

**Advantages:** Easy to use; not very expensive; moves cursor faster than arrow keys.

### 3. Joystick
**Simple Take:** A stick you tilt in any direction to move a cursor or control something on screen.

**Technical:** A pointing device — a stick with a spherical ball at both lower and upper ends; the lower ball moves in a socket. Can be moved in **all four directions**. Function is similar to a mouse. Mainly used in **CAD** and **computer games**.

### 4. Light Pen
**Simple Take:** A pen-shaped device you point directly at the CRT screen to draw or select — the screen detects where the pen is pointing.

**Technical:** Contains a **photocell and an optical system** in a small tube. When the pen tip is moved over the CRT monitor and the pen button is pressed, the photocell sensing element **detects the screen location** and sends the corresponding signal to the CPU. Used to select menu items or draw pictures on screen.

### 5. Track Ball
**Simple Take:** Like an upside-down mouse. You rotate a ball with your fingers/thumb while the device stays stationary — the pointer moves.

**Technical:** Mostly used in **notebook/laptop computers** instead of a mouse. A ball which is half-inserted; by moving fingers on the ball, the pointer is moved. Requires **less space than a mouse** (whole device is not moved). Comes in various shapes: ball, button, or square.

### 6. Scanner
**Simple Take:** Works like a photocopy machine but converts the physical image into a digital file.

**Technical:** Captures images from the source (paper, photo) and converts them into **digital form** that can be stored on disk. These images can be edited before being printed. Used when information available on paper needs to be transferred to a computer's hard disk.

### 7. Digitizer (Graphics Tablet)
**Simple Take:** A flat pad you draw on with a stylus — the drawing appears on screen. Used by graphic designers and illustrators.

**Technical:** An input device that **converts analog information into digital form**. Can convert a signal from TV or camera into a series of numbers stored in a computer. Also known as a **Tablet or Graphics Tablet** because it converts graphics and pictorial data into binary inputs. Used for **fine works of drawing and image manipulation**.

### 8. Microphone
**Simple Take:** An input device that captures sound and converts it to digital data.

**Technical:** Input device for **inputting sound** stored in digital form. Used for adding sound to multimedia presentations or mixing music.

### 9. Magnetic Ink Card Reader (MICR)
**Simple Take:** Reads special magnetic ink printed on bank cheques to process them automatically.

**Technical:** Generally used in **banks** to process large numbers of cheques daily. Bank's code number and cheque number are printed with a special ink containing **particles of magnetic material** that are machine-readable. Process is called **Magnetic Ink Character Recognition (MICR)**. Main advantages: **fast and less error-prone**.

### 10. Optical Character Reader (OCR)
**Simple Take:** Scans printed text and converts it into editable digital text the computer can process.

**Technical:** Input device used to **read printed text**. OCR scans text optically, **character by character**, converts them into machine-readable code, and stores on system memory.

### Additional Input Devices (from syllabus notes):

### 11. Bar Code Reader
**Simple Take:** The handheld scanner at supermarkets — scans the striped barcode on products.

**Technical:** Device used for reading **bar coded data** (data in the form of light and dark lines). Used in labelling goods, numbering books. Scans a bar code image, converts it into an **alphanumeric value**, then feeds it to the connected computer. Available as handheld or stationary scanner.

### 12. Optical Mark Reader (OMR)
**Simple Take:** The machine that reads your MCQ answer sheets by detecting pencil/pen marks.

**Technical:** A special type of optical scanner that recognizes marks made by pen or pencil. Used where **one out of a few alternatives is to be selected and marked**. Specially used for **checking answer sheets of examinations** with multiple choice questions.

## 1.6 Dithering

**Simple Take:** When a display or printer can't show a colour directly, it places dots of two nearby available colours very close together. From a distance, your eye blends them into the desired in-between colour — like how a newspaper photo looks smooth from far away.

**Technical:** Dithering is a quantization noise-shaping technique. When reducing colour depth, the **quantization error** (difference between desired and available colour) is diffused to neighbouring pixels.
- **Ordered Dithering (Bayer Matrix):** Compares each pixel to a threshold matrix; produces a regular, patterned result.
- **Error-Diffusion Dithering (Floyd-Steinberg):** Spreads the error to the right and lower neighbours using weights 7/16, 3/16, 5/16, 1/16. Produces a more natural-looking result.

## 1.7 Half-toning

**Simple Take:** Newspapers can only print black or white — no grey. To simulate grey, they print black dots of varying sizes. Large dots = dark grey. Tiny dots = light grey. From reading distance, it looks like continuous grey.

**Technical:** Half-toning simulates continuous-tone images using **binary output** (ink / no-ink). A **halftone cell** contains a grid of pixels. The number of pixels enabled within the cell represents the grey level.

### Solved Numerical 1 — Half-toning

**Q:** A laser printer operates at 600 DPI. A 4×4 halftone cell is used.
(a) How many grey levels can be produced?
(b) What is the effective image resolution?

```
(a) Grey levels = n² + 1 = 4² + 1 = 16 + 1 = 17 grey levels

(b) Effective resolution = Printer DPI / n = 600 / 4 = 150 DPI
```

### Solved Numerical 2 — Half-toning (extended)

**Q:** You need at least 65 grey levels for a printed image. A 1200 DPI printer is available.
(a) What is the minimum halftone cell size n needed?
(b) What is the effective image resolution?

```
(a) n² + 1 ≥ 65
    n² ≥ 64
    n ≥ 8
    → Minimum n = 8 (an 8×8 halftone cell)
    Grey levels = 8² + 1 = 65 ✓

(b) Effective resolution = 1200 / 8 = 150 DPI
```

## 1.8 Aliasing

**Simple Take:** When you draw a diagonal line using square pixels, it looks like a staircase. That jagged, staircased appearance is **aliasing** — the pixel grid simply cannot perfectly represent a smooth diagonal edge.

**Technical:** Aliasing is a **sampling artefact** caused by under-sampling a continuous signal. According to the **Nyquist theorem**, a signal of frequency f must be sampled at ≥ 2f to be accurately represented. On a display, the pixel grid is the sampler. When fine details (sharp edges, diagonals) are under-sampled, they appear as:
- **Spatial aliasing:** jagged edges ("jaggies") on diagonal/curved objects.
- **Temporal aliasing:** strobing effects in animation (the "wagon-wheel effect" where spokes appear to spin backwards).

## 1.9 Anti-aliasing

**Simple Take:** To fix the jagged staircase, you colour the edge pixels partially — blending the line's colour with the background colour. Your eye perceives a smooth edge even though the underlying pixels are still square.

**Technical:** Anti-aliasing increases the effective sampling rate or approximates sub-pixel coverage.

| Method | Description |
|---|---|
| **SSAA (Super Sampling)** | Render at 2×/4× resolution, then downsample — most expensive, highest quality |
| **MSAA (Multi-Sample AA)** | Super-samples only at geometry edges — good balance of quality and speed |
| **FXAA (Fast Approx AA)** | Post-process filter applied to the final rendered image — fastest, slight blurriness |
| **Weighted Area Sampling** | Pixel colour = weighted average based on area covered by the primitive |
| **Pre-filtering** | Low-pass filter applied before sampling to remove high frequencies |

## 1.10 Frame Buffer & Resolution — Numericals

### Solved Numerical 3 — Frame Buffer Size

**Q:** A monitor has a resolution of 1920×1080 with 24-bit true colour. Calculate:
(a) Total pixels
(b) Frame buffer size in MB
(c) Bandwidth required for 60 fps

```
(a) Total pixels = 1920 × 1080 = 2,073,600 pixels ≈ 2.07 megapixels

(b) Frame buffer size = 1920 × 1080 × 24 bits
                      = 49,766,400 bits
                      = 49,766,400 / 8 = 6,220,800 bytes
                      = 6,220,800 / (1024 × 1024) ≈ 5.93 MB ≈ 6 MB

(c) Bandwidth = 6,220,800 bytes × 60 fps
              = 373,248,000 bytes/sec
              ≈ 373 MB/sec ≈ 2.99 Gbps
```

### Solved Numerical 4 — Number of Colours

**Q:** A system uses 8 bits per pixel. How many distinct colours can it display?
What bit depth is needed to display 16 million colours?

```
Colours at 8 bpp = 2^8 = 256 colours

For 16 million colours:
2^n ≥ 16,000,000
n ≥ log₂(16,000,000) = log(16,000,000) / log(2) ≈ 23.93
→ n = 24 bits (True Colour)

Verify: 2^24 = 16,777,216 ≈ 16.7 million colours ✓
```

### Solved Numerical 5 — PPI Calculation

**Q:** A 27-inch monitor has a resolution of 2560×1440. Calculate its PPI.

```
Diagonal in pixels = √(2560² + 1440²)
                   = √(6,553,600 + 2,073,600)
                   = √8,627,200
                   ≈ 2937.2 pixels

PPI = 2937.2 / 27 ≈ 108.8 PPI ≈ 109 PPI
```

### Solved Numerical 6 — Video Storage

**Q:** A 30-second uncompressed video is recorded at 1280×720, 30 fps, 24-bit colour. Calculate storage needed.

```
Frame size = 1280 × 720 × 24 bits = 22,118,400 bits
           = 22,118,400 / 8 = 2,764,800 bytes ≈ 2.64 MB per frame

Total frames = 30 fps × 30 seconds = 900 frames

Total size = 900 × 2,764,800 = 2,488,320,000 bytes
           = 2,488,320,000 / (1024³) ≈ 2.32 GB
```

### Solved Numerical 7 — Frame Buffer with different bit depths

**Q:** A system has a display resolution of 640×480. Calculate frame buffer size (in KB) for:
(a) 1 bit per pixel (monochrome)
(b) 8 bits per pixel (256 colours)
(c) 16 bits per pixel (high colour)

```
(a) 1 bpp: 640 × 480 × 1 = 307,200 bits = 38,400 bytes = 37.5 KB

(b) 8 bpp: 640 × 480 × 8 = 2,457,600 bits = 307,200 bytes = 300 KB

(c) 16 bpp: 640 × 480 × 16 = 4,915,200 bits = 614,400 bytes = 600 KB
```

## 1.11 Parametric Equations of Line and Conics

### Parametric Line

**Simple Take:** Instead of y = mx + c (which breaks for vertical lines and is awkward in 3D), parametric form uses a variable t: at t=0 you're at the start point; at t=1 you're at the end point.

For a line segment from P1(x1,y1) to P2(x2,y2):

### Parametric Circle

**Verification:** x² + y² = r²cos²t + r²sin²t = r²(cos²t + sin²t) = r² ✓

**Example:** Circle x² + y² = 9 → x = 3cos t, y = 3sin t (r = 3)

### Parametric Ellipse

**Example:** Ellipse x²/36 + y²/25 = 1 → x = 6cos t, y = 5sin t (a=6, b=5)

### Parametric Parabola

**Example:** y² = 8x (a=2) → x = 2t², y = 4t

**Verification:** x = 2t², y = 4t → t = y/4 → t² = y²/16 → x = 2(y²/16) = y²/8 → y² = 8x ✓

### Parametric Hyperbola

**Verification:** x²/a² − y²/b² = (a sec t)²/a² − (b tan t)²/b² = sec²t − tan²t = 1 ✓

**Example:** x²/9 − y²/4 = 1 → x = 3sec t, y = 2tan t

### Translated Conics (Centre not at origin)

| Curve | Cartesian Equation | Parametric Equations |
|---|---|---|
| Circle | (x−3)² + (y+2)² = 16 | x = 4cos t + 3, y = 4sin t − 2 |
| Ellipse | (x+3)²/25 + (y−1)²/16 = 1 | x = 5cos t − 3, y = 4sin t + 1 |

**General rule:** If centre is at (h, k) and radius/axis is r:
- Circle: x = h + r·cos t, y = k + r·sin t
- Ellipse: x = h + a·cos t, y = k + b·sin t

### Differentiating Parametric Equations

**Simple Take:** One major reason to use parametric equations is that differentiation becomes much easier.

**Technical — Chain Rule:**

**Example:** Circle x² + y² = 9, parametric: x = 3cos t, y = 3sin t

```
dx/dt = −3sin t
dy/dt = 3cos t

dy/dx = (dy/dt) / (dx/dt) = 3cos t / (−3sin t) = −cot t
```

### Solved Numerical 8 — Parametric Circle Point

**Q:** A circle has centre C(3, 4) and radius 5.
(a) Write its parametric equations.
(b) Find the point at t = 60°.
(c) Verify the point satisfies the standard equation.

```
(a) x(t) = 3 + 5cos(t),   y(t) = 4 + 5sin(t)

(b) At t = 60°:
    x = 3 + 5cos(60°) = 3 + 5(0.5)    = 3 + 2.5  = 5.5
    y = 4 + 5sin(60°) = 4 + 5(0.866)  = 4 + 4.33 = 8.33
    Point = (5.5, 8.33)

(c) Standard equation: (x−3)² + (y−4)² = 25
    (5.5−3)² + (8.33−4)² = 2.5² + 4.33² = 6.25 + 18.75 = 25 ✓
```

### Solved Numerical 9 — Parametric Ellipse

**Q:** Ellipse x²/36 + y²/9 = 1. Find the point at t = 45°. Verify it lies on the ellipse.

```
a = 6, b = 3
x(t) = 6cos(45°) = 6 × 0.707 = 4.243
y(t) = 3sin(45°) = 3 × 0.707 = 2.121

Verify: (4.243)²/36 + (2.121)²/9
      = 18/36 + 4.5/9
      = 0.5 + 0.5 = 1 ✓
```

### Solved Numerical 10 — Parametric Line

**Q:** Line from P1(2, 5) to P2(10, 9).
(a) Write parametric form.
(b) Find point at t = 0.5.
(c) At what t does x = 6?
(d) Is point (8, 8) on this segment?

```
(a) x(t) = 2 + t(10−2) = 2 + 8t
    y(t) = 5 + t(9−5)  = 5 + 4t

(b) t = 0.5:
    x = 2 + 8(0.5) = 6,   y = 5 + 4(0.5) = 7 → Point (6, 7)
    [This is the midpoint: ((2+10)/2, (5+9)/2) = (6,7) ✓]

(c) x = 6: 2 + 8t = 6 → t = 0.5

(d) From x=8: 2 + 8t = 8 → t = 0.75
    y at t=0.75: 5 + 4(0.75) = 8
    → Both x and y give t=0.75, and 0 ≤ 0.75 ≤ 1 → (8,8) IS on the segment ✓
```

# UNIT 2 — Mathematics for Computer Graphics
## 2.1 Point Representation

**Simple Take:** A point is just a location — a dot with an address. In 2D it needs two numbers (x, y). In 3D it needs three (x, y, z).

**Technical:** A point defines a **location in a coordinate system**.
- **2D:** Represented by an ordered pair **(x, y)** — distances from X-axis and Y-axis respectively.
- **3D:** Represented by an ordered triplet **(x, y, z)** — distances from X-axis, Y-axis, and Z-axis respectively.

**Types of Point Arrangements:**

| Type | Definition |
|---|---|
| **Collinear Points** | 3 or more points present on the **same straight line** |
| **Non-Collinear Points** | Points that do **not** lie on the same straight line |
| **Coplanar Points** | A group of points present on the **same plane** |
| **Non-Coplanar Points** | Points that do **not** lie on the same plane |

**Homogeneous Coordinates (important for transformations):**
- **2D:** P = [x, y, w]ᵀ — actual point is (x/w, y/w). For w=1: P = [x, y, 1]ᵀ.
- **3D:** P = [x, y, z, w]ᵀ — used with 4×4 transformation matrices.
- **Why?** In standard coordinates, **translation cannot be done by matrix multiplication**. Homogeneous coordinates allow ALL 2D/3D transformations (including translation) to be expressed as a single matrix multiplication.

## 2.2 Vector and Scalar

**Simple Take:**
- A **scalar** is just a number with magnitude only — like your weight (70 kg) or temperature (25°C).
- A **vector** is a number with both magnitude AND direction — like "walk 5 km north" or "push with 10N to the right."

**Scalar Quantity:** Has only magnitude. Examples: mass, speed, distance, time, energy, density, volume, temperature.

**Vector Quantity:** Has both magnitude and direction. Examples: displacement, acceleration, force, momentum, weight, velocity of light, gravitational field.

**Difference Table:**

| Scalar Quantity | Vector Quantity |
|---|---|
| Has magnitude only | Has both magnitude and direction |
| Does not have direction | Has direction |
| Specified by a number and a unit | Specified by a number along with direction and unit |
| Represented by quantity symbol | Represented by bold symbol or arrow above (e.g., **a** or ā) |
| Example: Temperature, speed | Example: Acceleration, velocity |

## 2.3 Vector Representation

**Simple Take:** A vector is like a directed arrow drawn from point A to point B. The arrow shows direction; the length shows magnitude.

**Technical:** A vector in a plane is represented by a **directed line segment** (an arrow). The endpoints are the **initial point** and **terminal point**.

- The directed line segment from A to B is denoted as **AB** (in bold).
- The **magnitude** (length) is denoted |**AB**| = a.
- If **AB** = **a**, then |**AB**| = a (the magnitude).
- Single-letter notation: vectors written as **a**, **b**, **c** (bold) or ā, b̄, c̄ (with bar).

**Characteristics of Vectors:**
- Possess both magnitude and direction.
- Do NOT obey ordinary laws of algebra (non-commutative for cross product).
- Either the magnitude or direction changes, or both change.

**Vectors in Computer Graphics (Uses):**
1. **Represent Points:** Every pixel/object position is stored as a vector. Example: screen point = (120, 300).
2. **Direction of Line:** Line from A to B = **B** − **A**. Used in drawing algorithms.
3. **Motion in Animation:** Speed, velocity, force are all vectors. Example: car moving right → velocity vector pointing right.
4. **Lighting & Shading:** Normal vector decides how light hits a surface. Used in reflection, brightness calculation, 3D rendering.
5. **Camera Direction:** Camera position vector and viewing direction vector.

## 2.4 Vector Addition

**Simple Take:** Adding two vectors is like combining two journeys. "Walk 3 east + 4 north" added to "walk 1 east + 2 north" = "walk 4 east + 6 north."

**Technical:** Two vectors **a** and **b** can be added to get resultant **a + b**.

**Rules:**
- Vectors can only be added if they are **of the same nature** (acceleration + acceleration ✓; acceleration + mass ✗).
- Cannot add vectors and scalars together.

**Algebraic Method (Component Form):**

For **C** = Cx**i** + Cy**j** + Cz**k** and **D** = Dx**i** + Dy**j** + Dz**k**:

**Geometric Method:** Two ways —

### Triangle Law of Vector Addition
If two vectors are represented by two sides of a triangle taken in the **same order**, the **third side** represents the resultant in magnitude and direction.

Using the Pythagoras theorem:

Direction:

### Parallelogram Law of Vector Addition
If two non-zero vectors are the **two adjacent sides of a parallelogram**, the resultant is given by the **diagonal of the parallelogram** passing through the point of intersection.

### Solved Numerical 1 — Vector Addition (Component Form)

**Q:** **A** = [3, −2], **B** = [−1, 5], k = 4.
Find: (a) **A** + **B**, (b) **A** − **B**, (c) k**A**, (d) |**A** + **B**|

```
(a) A + B = [3+(−1), −2+5] = [2, 3]

(b) A − B = [3−(−1), −2−5] = [4, −7]

(c) kA = 4×[3, −2] = [12, −8]

(d) |A + B| = |[2,3]| = √(2² + 3²) = √13 ≈ 3.606
```

### Solved Numerical 2 — Triangle / Parallelogram Law

**Q:** Two vectors have magnitudes |**a**| = 3 and |**b**| = 4. The angle between them is 60°. Find the magnitude of the resultant.

```
|R| = √(|a|² + |b|² + 2|a||b|cos θ)
    = √(3² + 4² + 2×3×4×cos 60°)
    = √(9 + 16 + 24 × 0.5)
    = √(9 + 16 + 12)
    = √37
    ≈ 6.08

Direction: β = tan⁻¹(4×sin60° / (3 + 4×cos60°))
             = tan⁻¹(4×0.866 / (3 + 4×0.5))
             = tan⁻¹(3.464 / 5)
             = tan⁻¹(0.6928)
             ≈ 34.7° from vector a
```

## 2.5 Matrices

**Simple Take:** A matrix is a grid (table) of numbers. In computer graphics, matrices are "transformation machines" — multiply a point's coordinates by a matrix and you get the transformed point (rotated, scaled, translated, etc.).

**Technical Definition:** A **matrix** is an ordered rectangular array of numbers, symbols, or characters arranged in rows and columns, used to express linear equations.

### Key Matrix Concepts:

**Determinant:** A scalar value calculated from a square matrix.
- For 2×2 matrix A = [[a, b], [c, d]]: **|A| = ad − bc**
- For 3×3: expand along first row using cofactors.
- For 4×4: expand similarly (cofactor expansion).

**Trace:** Sum of the **principal diagonal elements** of a square matrix.

**Minor (Mij):** Determinant of the matrix obtained by **deleting row i and column j**.

**Cofactor (Cij):** Cij = (−1)^(i+j) × Mij

**Adjoint (adj A):** **Transpose of the cofactor matrix** of A.

**Inverse (A⁻¹):** For a square matrix with det ≠ 0:

**Properties of Transpose:**
- (Aᵀ)ᵀ = A
- (A+B)ᵀ = Aᵀ + Bᵀ
- (AB)ᵀ = BᵀAᵀ

**Matrix Formulas (for adjoint/inverse):**
- A⁻¹ = adj(A)/|A|
- A(adj A) = (adj A)A = I
- |adj A| = |A|^(n−1) where n = order of A
- adj(adj A) = |A|^(n−2) × A
- |adj(adj A)| = |A|^(n−1)²
- adj(AB) = (adj B)(adj A)
- adj(Aᵖ) = (adj A)ᵖ
- adj(I) = I, adj(0) = 0
- (AB)⁻¹ = B⁻¹A⁻¹
- If A is symmetric, adj(A) is also symmetric
- If A is singular, |adj A| = 0

### Matrices in Computer Graphics

**Uses of Matrices:**
1. **Translation (Move Object):** Moves object from one place to another.
2. **Rotation (Turn Object):** Rotates object around origin or axis.
3. **Scaling (Resize Object):** Enlarges or shrinks shapes.
4. **Reflection:** Flips object across an axis.
5. **Shearing:** Slants shape sideways.
6. **Projection:** Converts 3D scene → 2D screen.

**USE OF VECTOR vs MATRIX:**

| Vector | Matrix |
|---|---|
| Represents direction/position | Performs transformation |
| Stores point coordinates | Moves or rotates points |
| Used in lighting & motion | Used in animation & projection |

### Solved Numerical 3 — Determinant (2×2)

**Q:** Find |A| for A = [[4, 3], [2, 5]]

```
|A| = (4×5) − (3×2) = 20 − 6 = 14
```

### Solved Numerical 4 — Determinant (3×3)

**Q:** Find |A| for A = [[1,2,3],[4,5,6],[7,8,9]]

```
|A| = 1×(5×9 − 6×8) − 2×(4×9 − 6×7) + 3×(4×8 − 5×7)
    = 1×(45−48) − 2×(36−42) + 3×(32−35)
    = 1×(−3) − 2×(−6) + 3×(−3)
    = −3 + 12 − 9
    = 0

(This matrix is singular — no inverse exists)
```

### Solved Numerical 5 — Matrix Multiplication

**Q:** A = [[2,3],[1,4]], B = [[5,1],[2,3]]. Find A×B.

```
C[0][0] = 2×5 + 3×2 = 10 + 6 = 16
C[0][1] = 2×1 + 3×3 = 2  + 9 = 11
C[1][0] = 1×5 + 4×2 = 5  + 8 = 13
C[1][1] = 1×1 + 4×3 = 1  + 12 = 13

A×B = [[16, 11], [13, 13]]

Note: Matrix multiplication is NOT commutative — A×B ≠ B×A in general.
```

### Solved Numerical 6 — Matrix Inverse (2×2)

**Q:** Find the inverse of A = [[3, 1], [2, 4]]

```
|A| = 3×4 − 1×2 = 12 − 2 = 10

Cofactor matrix:
C11 = +4,  C12 = −2
C21 = −1,  C22 = +3

adj(A) = Cᵀ = [[4, −1], [−2, 3]]

A⁻¹ = (1/|A|) × adj(A) = (1/10) × [[4,−1],[−2,3]]
     = [[0.4, −0.1], [−0.2, 0.3]]

Verify: A × A⁻¹ = [[3,1],[2,4]] × [[0.4,−0.1],[−0.2,0.3]]
       = [[3×0.4+1×(−0.2), 3×(−0.1)+1×0.3],
          [2×0.4+4×(−0.2), 2×(−0.1)+4×0.3]]
       = [[1.2−0.2, −0.3+0.3], [0.8−0.8, −0.2+1.2]]
       = [[1, 0], [0, 1]] = I ✓
```

### Solved Numerical 7 — Transformation Matrix Application

**Q:** Apply T = [[2,0,3],[0,2,4],[0,0,1]] to point P(1, 2) using homogeneous coordinates.

```
Homogeneous P = [1, 2, 1]ᵀ

T × P:
x' = 2×1 + 0×2 + 3×1 = 5
y' = 0×1 + 2×2 + 4×1 = 8
w' = 0+0+1 = 1

Transformed point = (5/1, 8/1) = (5, 8)

Interpretation: The matrix scaled by 2 and then translated by (3,4).
Original (1,2) → New (5,8)
```

## 2.6 Dot Product (Scalar Product)

**Simple Take:** The dot product measures "how much" two vectors point in the same direction. Result is a **single number** (scalar). Zero = perpendicular; positive = same general direction; negative = opposite directions.

**Technical:**

For **a** = x1**i** + y1**j** + z1**k** and **b** = x2**i** + y2**j** + z2**k**:

**Properties:**
- Commutative: **a · b** = **b · a**
- Distributive: **a · (b + c)** = **a · b** + **a · c**
- If **a · b** = 0 and neither is zero → vectors are **perpendicular**

**Applications in CG:**
- Finding angle between two vectors
- **Lambert's Law lighting:** diffuse intensity = **N** · **L** (surface normal · light direction)
- Back-face culling (checking if surface faces viewer)
- Projection of one vector onto another

### Solved Numerical 8 — Dot Product & Angle

**Q:** **a** = [3, 4], **b** = [1, 2]. Find dot product, angle between them, and projection of **a** onto **b**.

```
a · b = 3×1 + 4×2 = 3 + 8 = 11

|a| = √(9+16) = √25 = 5
|b| = √(1+4)  = √5 ≈ 2.236

cos θ = 11 / (5 × 2.236) = 11/11.18 ≈ 0.9839
θ = cos⁻¹(0.9839) ≈ 10.3°

Projection of a onto b:
scalar proj = a·b / |b| = 11/2.236 ≈ 4.919
vector proj = (a·b / |b|²) × b = (11/5) × [1,2] = [2.2, 4.4]
```

### Solved Numerical 9 — Check Perpendicularity

**Q:** Are **A** = [3, 4, 0] and **B** = [4, −3, 0] perpendicular?

```
A · B = 3×4 + 4×(−3) + 0×0 = 12 − 12 + 0 = 0

Since A · B = 0 → A and B are PERPENDICULAR ✓
```

## 2.7 Cross Product (Vector Product)

**Simple Take:** The cross product of two 3D vectors gives you a **new vector perpendicular to both**. Use the right-hand rule: point fingers along **A**, curl toward **B**, your thumb points in **A × B**. It only works in 3D.

**Technical:** For **A** = [Ai, Aj, Ak] and **B** = [Bi, Bj, Bk]:

Expanded:

Or equivalently:

**Properties:**
- |**A × B**| = |**A**||**B**|sin θ (= area of parallelogram formed by **A** and **B**)
- Anti-commutative: **A × B** = −(**B × A**)
- **A × A** = **0**
- **A × B** = **0** iff **A** and **B** are parallel (sin 0° = 0)

**Applications in CG:**
- Computing **surface normals** (essential for lighting calculations)
- Determining winding order (clockwise/counter-clockwise) of polygon vertices

### Solved Numerical 10 — Cross Product

**Q:** **A** = [1, 2, 3], **B** = [4, 5, 6]. Find **A × B**.

```
A × B = [(2×6 − 3×5), (3×4 − 1×6), (1×5 − 2×4)]
      = [(12−15), (12−6), (5−8)]
      = [−3, 6, −3]

Verify perpendicular to A: (−3×1) + (6×2) + (−3×3) = −3+12−9 = 0 ✓
Verify perpendicular to B: (−3×4) + (6×5) + (−3×6) = −12+30−18 = 0 ✓
```

### Solved Numerical 11 — Surface Normal using Cross Product

**Q:** Triangle has vertices P1=(1,0,0), P2=(0,1,0), P3=(0,0,1). Find its unit surface normal.

```
E1 = P2 − P1 = [−1, 1, 0]
E2 = P3 − P1 = [−1, 0, 1]

N = E1 × E2:
Ni = (1×1 − 0×0)         = 1
Nj = (0×(−1) − (−1)×1)   = 1
Nk = ((−1)×0 − 1×(−1))   = 1

N = [1, 1, 1]
|N| = √3 ≈ 1.732

Unit Normal N̂ = [1/√3, 1/√3, 1/√3] ≈ [0.577, 0.577, 0.577]

Verify: N · E1 = (1)(−1) + (1)(1) + (1)(0) = 0 ✓
        N · E2 = (1)(−1) + (1)(0) + (1)(1) = 0 ✓
```

## 2.8 Parametric Equations (Unit 2 Perspective)

**Definition (from Unit 2 notes):** Parametric equations show the position of a point using variables called **parameters**. These help describe how a point, curve, or surface moves or behaves in space.

**Types:**
1. **Linear Parametric Equations:** Represent straight lines. x(t) = at + b, y(t) = ct + d.
2. **Circular Parametric Equations:** x(t) = r cos(t), y(t) = r sin(t).
3. **Elliptical Parametric Equations:** x(t) = a cos(t), y(t) = b sin(t).
4. **Parametric Curves:** x(t) = f(t), y(t) = g(t) for arbitrary functions f and g.

**Parametric Equations in 3D:**

| Curve | Parametric Equations |
|---|---|
| Line | x = x0 + at, y = y0 + bt, z = z0 + ct |
| Plane | x = x0 + at + bu, y = y0 + ct + dv, z = z0 + et + fw |
| Sphere | x = h + r sinθ cosφ, y = k + r sinθ sinφ, z = l + r cosθ |
| Ellipsoid | x = h + r cosθ sinφ, y = k + r sinθ sinφ, z = l + r cosφ |

# UNIT 3 — Line Drawing, Clipping & Filling
## 3.1 Why Line Drawing Algorithms?

**Simple Take:** A real line is continuous and infinitely thin. A screen is a grid of discrete square pixels. We need an algorithm to decide *which* pixels to turn on so they approximate the desired line.

**Technical:** Given two integer endpoint coordinates, determine the minimal set of pixels that best represents the ideal mathematical line. Requirements: (1) straight-line appearance, (2) endpoints are plotted, (3) consistent pixel density along the line, (4) computationally efficient (millions of lines drawn per second in real-time graphics).

## 3.2 DDA Algorithm (Digital Differential Analyzer)

**Simple Take:** Calculate the slope. Step along the longer axis one pixel at a time. At each step, add the slope fraction to the shorter axis. Round off to get the pixel.

**Technical:**
- Compute Δx = x2−x1, Δy = y2−y1
- If |Δx| ≥ |Δy|: step 1 in x, increment y by slope m = Δy/Δx
- Else: step 1 in y, increment x by 1/m
- **Round (x,y) to nearest integer** at each step → pixel coordinate
- **Disadvantage:** Uses floating-point arithmetic — slower than Bresenham's

### Algorithm — DDA

```
Input: P1(x1, y1), P2(x2, y2)

1. dx = x2 − x1,   dy = y2 − y1
2. if |dx| >= |dy|: steps = |dx|
   else:            steps = |dy|
3. xInc = dx / steps
   yInc = dy / steps
4. x = x1,  y = y1
5. For k = 0 to steps:
       Plot(round(x), round(y))
       x = x + xInc
       y = y + yInc
```

### Solved Numerical 1 — DDA

**Q:** Use DDA to draw a line from P1(1,1) to P2(9,5).

```
dx = 8, dy = 4
steps = max(8, 4) = 8
xInc = 8/8 = 1.0,  yInc = 4/8 = 0.5

k     x      y      Plot
0     1.0    1.0    (1, 1)
1     2.0    1.5    (2, 2)
2     3.0    2.0    (3, 2)
3     4.0    2.5    (4, 3)
4     5.0    3.0    (5, 3)
5     6.0    3.5    (6, 4)
6     7.0    4.0    (7, 4)
7     8.0    4.5    (8, 5)
8     9.0    5.0    (9, 5)

Pixels: (1,1)(2,2)(3,2)(4,3)(5,3)(6,4)(7,4)(8,5)(9,5)
```

## 3.3 Bresenham's Line Algorithm

**Simple Take:** The smarter, faster version of DDA. Uses **only integer arithmetic** (no floats, no division). Keeps a running "error" value that decides whether to go straight across or diagonally at each step.

**Technical (for 0 ≤ slope m ≤ 1):**
- At each x step, the next pixel is either **E (East, y stays)** or **NE (North-East, y+1)**
- Decision parameter **d** tells which to pick
- If d < 0 → choose E; d += 2Δy
- If d ≥ 0 → choose NE; d += 2Δy − 2Δx; y++
- Initial d₀ = 2Δy − Δx
- **ALL operations are integer additions only** — ideal for hardware

### Algorithm — Bresenham's Line (0 ≤ m ≤ 1)

```
Input: P1(x1,y1), P2(x2,y2)  [assume x2 > x1, slope 0 to 1]

1. dx = x2−x1,  dy = y2−y1
2. d    = 2*dy − dx          (initial decision parameter)
3. incE  = 2*dy              (increment for East choice)
4. incNE = 2*(dy − dx)       (increment for NE choice)
5. x = x1,  y = y1
6. Plot(x, y)
7. While x < x2:
       if d < 0:
           d += incE          (choose East: y stays)
       else:
           d += incNE         (choose NE: y increases)
           y = y + 1
       x = x + 1
       Plot(x, y)
```

### Solved Numerical 2 — Bresenham's Line

**Q:** Draw a line from (2,1) to (9,5) using Bresenham's algorithm.

```
dx = 7, dy = 4
d₀   = 2×4 − 7 = 1
incE  = 2×4 = 8
incNE = 2×(4−7) = −6

Plot (2, 1)

x=3: d=1  ≥0 → NE: y=2, d=1+(−6)=−5     → Plot (3,2)
x=4: d=−5 <0 → E:  y=2, d=−5+8=3        → Plot (4,2)
x=5: d=3  ≥0 → NE: y=3, d=3+(−6)=−3     → Plot (5,3)
x=6: d=−3 <0 → E:  y=3, d=−3+8=5        → Plot (6,3)
x=7: d=5  ≥0 → NE: y=4, d=5+(−6)=−1     → Plot (7,4)
x=8: d=−1 <0 → E:  y=4, d=−1+8=7        → Plot (8,4)
x=9: d=7  ≥0 → NE: y=5, d=7+(−6)=1      → Plot (9,5)

Pixels: (2,1)(3,2)(4,2)(5,3)(6,3)(7,4)(8,4)(9,5)
```

### DDA vs Bresenham's Comparison

| Feature | DDA | Bresenham's |
|---|---|---|
| Arithmetic | Floating point | Integer only |
| Speed | Slower | Faster |
| Accuracy | Rounding errors accumulate | More precise |
| Hardware suitability | Not ideal | Ideal |
| Memory | More (floats) | Less (integers) |
| Complexity | Simpler | Slightly more complex |
| Usage | Educational/simple | Industry/hardware implementation |

## 3.4 Bresenham's Circle Drawing Algorithm (Midpoint Circle)

**Simple Take:** A circle has 8-fold symmetry — find one point, get 7 more for free by mirroring. So only compute 1/8th of the circle, then use symmetry to plot all 8 sectors.

**Technical:**
- Start at (0, r). Algorithm decides between **E (East: x+1, y stays)** and **SE (South-East: x+1, y−1)**
- Decision parameter d₀ = 1 − r
- If d < 0 → choose E: d += 2x + 3
- If d ≥ 0 → choose SE: d += 2x − 2y + 5; y decrements
- Stop when x > y

**8-fold symmetry:** For each computed (x, y), plot all 8:

### Algorithm — Midpoint Circle

```
Input: Centre (cx, cy), radius r

1. x = 0,  y = r
2. d = 1 − r
3. Plot8(cx, cy, x, y)
4. While x < y:
       if d < 0:
           d += 2*x + 3          (choose East)
       else:
           d += 2*x − 2*y + 5    (choose SE)
           y = y − 1
       x = x + 1
       Plot8(cx, cy, x, y)

Plot8(cx, cy, x, y):
   Plot (cx+x, cy+y), (cx−x, cy+y), (cx+x, cy−y), (cx−x, cy−y)
   Plot (cx+y, cy+x), (cx−y, cy+x), (cx+y, cy−x), (cx−y, cy−x)
```

### Solved Numerical 3 — Midpoint Circle

**Q:** Draw a circle with centre (0,0) and radius r = 6 using the Midpoint Circle Algorithm.

```
r=6, x=0, y=6
d₀ = 1 − 6 = −5

Step  x   y   d (before)  Choice   d (after)
0     0   6   −5          E(d<0)   −5+3=−2       Plot (0,6)
1     1   6   −2          E(d<0)   −2+5=3        Plot (1,6)
2     2   6   3           SE(d≥0)  3+4−12+5=0    Plot (2,6)→y=5
3     3   5   0           SE(d≥0)  0+6−10+5=1    Plot (3,5)→y=4
4     4   4   1           SE(d≥0)  1+8−8+5=6     Plot (4,4)
       (x=y=4, stop)

Points computed: (0,6)(1,6)(2,6)(3,5)(4,4)

8-fold for (3,5):
(3,5)(−3,5)(3,−5)(−3,−5)(5,3)(−5,3)(5,−3)(−5,−3)
```

## 3.5 Ellipse Generation Algorithm (Midpoint Ellipse)

**Simple Take:** An ellipse is a stretched circle — different horizontal and vertical radii. It has **4-fold symmetry** (not 8), so we compute one quadrant and mirror to the other three. The algorithm splits into two regions based on slope.

**Technical:**
- Let rx = x-radius, ry = y-radius.
- **Region 1:** where |slope| < 1 — step in x direction. Stop when 2·ry²·x ≥ 2·rx²·y.
- **Region 2:** where |slope| > 1 — step in y direction.
- Use ry² and rx² to avoid floating point.

**4-fold symmetry:** For each (x,y), plot (±x, ±y).

**Region 1:**
- d1₀ = ry² − rx²·ry + (1/4)·rx²
- If d1 < 0: d1 += 2·ry²·x + 3·ry²; x++
- Else: d1 += 2·ry²·x − 2·rx²·y + 2·rx² + 3·ry²; x++; y--

## 3.6 Clipping

### A. Point Clipping

A point P(x, y) is **inside** the window iff:

### Solved Numerical 4 — Point Clipping

**Q:** Window: xmin=2, xmax=9, ymin=1, ymax=7. Test: A(5,4), B(10,3), C(1,6), D(7,8), E(2,7), F(9,1).

```
A(5,4):  2≤5≤9 ✓  1≤4≤7 ✓  → INSIDE
B(10,3): 10>9  ✗            → OUTSIDE (right of window)
C(1,6):  1<2   ✗            → OUTSIDE (left of window)
D(7,8):  2≤7≤9 ✓  8>7 ✗    → OUTSIDE (above window)
E(2,7):  2≤2≤9 ✓  1≤7≤7 ✓  → INSIDE (on boundary — included)
F(9,1):  2≤9≤9 ✓  1≤1≤7 ✓  → INSIDE (corner — included)
```

### B. Line Clipping — Cohen-Sutherland Algorithm

**Simple Take:** Assign each endpoint of a line a 4-bit code based on its position relative to the window. Use these codes to instantly accept (both inside), reject (both outside on same side), or clip (one endpoint outside — compute intersection and repeat).

**Technical — Region Codes (4 bits: TBRL):**

```
Bit 3 (T): y > ymax  → set if ABOVE window
Bit 2 (B): y < ymin  → set if BELOW window
Bit 1 (R): x > xmax  → set if RIGHT of window
Bit 0 (L): x < xmin  → set if LEFT of window
```

**Region map:**
```
1001 | 1000 | 1010
-----+------+-----
0001 | 0000 | 0010     ← 0000 = inside window
-----+------+-----
0101 | 0100 | 0110
```

**Decision Rules:**
- Both codes = 0000 → **Trivially Accept** (line entirely inside)
- (code1 AND code2) ≠ 0000 → **Trivially Reject** (line entirely outside)
- Else → **Clip** at the boundary indicated by the first set bit

**Intersection Formulas:**
- Left boundary (x = xmin):   y = y1 + m(xmin − x1),  x = xmin
- Right boundary (x = xmax):  y = y1 + m(xmax − x1),  x = xmax
- Bottom boundary (y = ymin): x = x1 + (ymin − y1)/m, y = ymin
- Top boundary (y = ymax):    x = x1 + (ymax − y1)/m, y = ymax

where m = (y2−y1)/(x2−x1)

### Solved Numerical 5 — Cohen-Sutherland (Full Clip)

**Q:** Window: xmin=1, xmax=8, ymin=1, ymax=6. Clip line from P1(−1, 3) to P2(10, 5).

```
Assign codes:
P1(−1,3): x<xmin → Left bit set  → code1 = 0001
P2(10,5): x>xmax → Right bit set → code2 = 0010

Test: code1 AND code2 = 0001 AND 0010 = 0000 → cannot trivially reject
Neither code is 0000 → must clip

Clip P1 (bit 0 = Left set): clip at x = xmin = 1
m = (5−3)/(10−(−1)) = 2/11 ≈ 0.1818
y = 3 + 0.1818 × (1−(−1)) = 3 + 0.3636 = 3.364
New P1 = (1, 3.364), code = 0000

Retest:
P1(1, 3.364): code = 0000
P2(10, 5):    code = 0010
0000 AND 0010 = 0 → cannot reject; clip P2

Clip P2 (Right bit set): clip at x = xmax = 8
y = 3.364 + 0.1818 × (8−1) = 3.364 + 1.273 = 4.637
New P2 = (8, 4.637), code = 0000

Both codes = 0000 → ACCEPT

Final clipped line: from (1, 3.364) to (8, 4.637)
```

### Solved Numerical 6 — Cohen-Sutherland (Trivial Reject)

**Q:** Window: xmin=2, xmax=7, ymin=2, ymax=8. Clip line P1(8,3) to P2(10,6).

```
P1(8,3):  x>xmax → code = 0010 (Right)
P2(10,6): x>xmax → code = 0010 (Right)

code1 AND code2 = 0010 AND 0010 = 0010 ≠ 0000
→ Both endpoints are on the RIGHT side → TRIVIALLY REJECTED
No intersection computation needed — line is completely outside.
```

### Solved Numerical 7 — Cohen-Sutherland (Top + Right case)

**Q:** Window: xmin=0, xmax=6, ymin=0, ymax=5. Clip P1(−2, 6) to P2(7, 2).

```
P1(−2,6): x<0 → L bit, y>5 → T bit → code1 = 1001
P2(7, 2): x>6 → R bit             → code2 = 0010

AND = 1001 & 0010 = 0000 → cannot reject, need to clip

m = (2−6)/(7−(−2)) = −4/9 ≈ −0.444

Clip P1: start with T bit (y > ymax = 5):
x = x1 + (ymax−y1)/m = −2 + (5−6)/(−4/9) = −2 + (−1)(−9/4) = −2 + 2.25 = 0.25
New P1 = (0.25, 5), code: x=0.25 is in [0,6], y=5 in [0,5] → code = 0000

Retest:
P1(0.25, 5): 0000
P2(7, 2):    0010 (Right)
AND = 0 → clip P2

Clip P2: R bit (x > xmax = 6):
y = 6 + (−0.444)×(6−(−2)) = 6 + (−0.444)×8 = 6 − 3.556 = 2.444
Wait — we now use updated P1 as reference:
y = 5 + (−0.444)×(6−0.25) = 5 + (−0.444)×5.75 = 5 − 2.553 = 2.447
New P2 = (6, 2.447), code = 0000

Both codes = 0000 → ACCEPT
Clipped line: from (0.25, 5) to (6, 2.447)
```

### C. Polygon Clipping — Sutherland-Hodgman Algorithm

**Simple Take:** Clip the polygon against **one window edge at a time** (left, then right, then bottom, then top). For each edge, walk through all consecutive vertex pairs and apply one of four rules.

**Technical — Four cases for each edge pair (S = current vertex, P = next vertex):**

| S inside? | P inside? | Output |
|---|---|---|
| Yes | Yes | Output P |
| Yes | No | Output intersection point |
| No | Yes | Output intersection point, then P |
| No | No | Output nothing |

The output polygon of one clipping step becomes the input to the next.

## 3.7 Filling Algorithms

### A. Inside Tests

Before filling a polygon, we need to determine whether a point is inside it.

#### Even-Odd Rule (Ray Casting)
**Simple Take:** Cast a ray from the point in any direction. Count how many times it crosses the polygon boundary. **Odd = inside. Even = outside.**

**Technical:** Works for simple and complex polygons. Handle special cases: count only non-horizontal edges; count a vertex only once (use the lower endpoint rule).

#### Non-Zero Winding Rule
**Simple Take:** Walk along the polygon edges. Count +1 when an edge crosses the ray going left-to-right; count −1 going right-to-left. If the total ≠ 0, the point is inside.

**Technical:** Better for self-intersecting polygons. Used in SVG, PostScript, and OpenGL fill rules.

### Solved Numerical 8 — Inside Test (Ray Casting)

**Q:** Is point P(5,5) inside triangle A(2,2), B(8,2), C(5,9)? Cast a ray in the +x direction.

```
Edge AB: (2,2)→(8,2) — horizontal → SKIP

Edge BC: (8,2)→(5,9)
y range [2,9]. Does ray y=5 straddle? 2 < 5 < 9 → YES
x at y=5: x = 8 + (5−2)/(9−2) × (5−8) = 8 + (3/7)(−3) = 8 − 1.286 = 6.714
Is 6.714 > 5 (to the right of P)? YES → count = 1

Edge CA: (5,9)→(2,2)
y range [9,2]. Does ray y=5 straddle? 2 < 5 < 9 → YES
x at y=5: x = 5 + (5−9)/(2−9) × (2−5) = 5 + (−4/−7)(−3) = 5 − 12/7 = 3.286
Is 3.286 > 5? NO → does not count

Total crossings = 1 (ODD) → P(5,5) is INSIDE ✓
```

### B. Flood Fill Algorithm

**Simple Take:** Like the MS Paint bucket tool. Start at a seed point inside a region. Fill it with the new colour. Then check all 4 neighbours — if they have the old colour, fill them too. Repeat until no unfilled old-colour neighbours remain.

**Technical:**
- **4-connected:** fills through up/down/left/right connections
- **8-connected:** also fills through diagonals (useful when boundaries have diagonal gaps)

```
FloodFill(x, y, oldColor, newColor):
    if getPixel(x,y) ≠ oldColor: return
    setPixel(x,y, newColor)
    FloodFill(x+1, y, oldColor, newColor)   [right]
    FloodFill(x−1, y, oldColor, newColor)   [left]
    FloodFill(x, y+1, oldColor, newColor)   [up]
    FloodFill(x, y−1, oldColor, newColor)   [down]
```

**Limitation:** Deep recursion can cause **stack overflow** for large regions. Use an explicit stack or **span-filling** variant for efficiency.

### C. Boundary Fill Algorithm

**Simple Take:** Fill outward from a seed point until you hit pixels of a specific boundary colour. Keep filling anything that is not the boundary colour and not already filled.

**Technical:**

```
BoundaryFill(x, y, fillColor, boundaryColor):
    current = getPixel(x,y)
    if current = boundaryColor: return
    if current = fillColor:     return
    setPixel(x,y, fillColor)
    BoundaryFill(x+1, y, fillColor, boundaryColor)
    BoundaryFill(x−1, y, fillColor, boundaryColor)
    BoundaryFill(x, y+1, fillColor, boundaryColor)
    BoundaryFill(x, y−1, fillColor, boundaryColor)
```

**Flood Fill vs Boundary Fill:**

| | Flood Fill | Boundary Fill |
|---|---|---|
| Stopping condition | Pixel ≠ old colour | Pixel = boundary colour |
| Input | Seed + old colour | Seed + boundary colour |
| Use case | Replace enclosed solid region of known colour | Fill region enclosed by a drawn boundary |

### D. Scan-Line Polygon Fill Algorithm

**Simple Take:** For each horizontal row of the screen (scan line), find where it enters and exits the polygon — then fill all pixels between those two x positions.

**Technical:** Uses two data structures:
- **Edge Table (ET):** Built once at start. For each non-horizontal edge, stores: ymax, x-value at ymin, and 1/slope (= Δx/Δy = (x2−x1)/(y2−y1)).
- **Active Edge Table (AET):** Contains edges currently intersected by the scan line. Updated as scan line moves upward.

### Algorithm — Scan-Line Fill

```
1. Build Edge Table (ET):
   - For each non-horizontal edge: store (ymax, xAtYmin, 1/slope)
   - Sort edges by ymin, then by x within same ymin

2. Initialize AET = empty

3. For y = ymin to ymax (scan line by scan line):
   a. Move edges from ET to AET where edge.ymin = y
   b. Remove edges from AET where edge.ymax = y
   c. Sort AET by current x value
   d. Fill pixels between pairs: (AET[0].x → AET[1].x), (AET[2].x → AET[3].x), ...
   e. Update each edge in AET: x = x + (1/slope)  [advance x for next scan line]
```

**Special vertex rule:** When scan line passes through a vertex, count it once if it's a local min/max (both adjacent edges on same side), twice if it's a pass-through (one edge going up, one coming down).

### Solved Numerical 9 — Scan-Line Fill

**Q:** Triangle vertices: A(2,1), B(8,3), C(10,7). Find intersections at scan line y=5.

```
Edges:
AB: (2,1)→(8,3): 1/slope = (8−2)/(3−1) = 6/2 = 3
BC: (8,3)→(10,7): 1/slope = (10−8)/(7−3) = 2/4 = 0.5
CA: (10,7)→(2,1): 1/slope = (2−10)/(1−7) = −8/(−6) = 4/3 ≈ 1.333

Active edges at y=5 (ymin ≤ 5 < ymax):
Edge BC: ymin=3, ymax=7 → active
         x at y=3 is 8; at y=5: x = 8 + 0.5×(5−3) = 8 + 1 = 9
Edge CA: ymin=1, ymax=7 → active
         x at y=1 is 10; at y=5: x = 10 + 1.333×(5−7) = 10 − 2.667 = 7.333
         Wait: for CA going from (10,7) to (2,1):
         xAtYmin(=1) = 2; at y=5: x = 2 + 1.333×(5−1) = 2 + 5.333 = 7.333

Sort by x: 7.333, 9
Fill pixels x = 7 to x = 9 on scan line y = 5
→ Pixels filled: (7,5)(8,5)(9,5) [using floor/ceil appropriately]
```

### Solved Numerical 10 — Scan-Line Edge Table Construction

**Q:** Polygon vertices (in order): P1(2,1), P2(6,1), P3(8,5), P4(4,7), P5(0,5).
Build the Edge Table.

```
Edges (non-horizontal only):
Edge P1P5: (2,1)→(0,5): ymin=1, ymax=5, xAtYmin=2, 1/slope=(0−2)/(5−1)=−0.5
Edge P5P4: (0,5)→(4,7): ymin=5, ymax=7, xAtYmin=0, 1/slope=(4−0)/(7−5)=2
Edge P4P3: (4,7)→(8,5): ymin=5, ymax=7, xAtYmin=8, 1/slope=(4−8)/(5−7)=2
Edge P3P2: (8,5)→(6,1): ymin=1, ymax=5, xAtYmin=6, 1/slope=(6−8)/(1−5)=0.5

Horizontal edge P1P2 (y=1): SKIPPED

Edge Table (sorted by ymin):
ymin=1: Edge P1P5 (ymax=5, x=2, 1/slope=−0.5)
        Edge P3P2 (ymax=5, x=6, 1/slope=0.5)
ymin=5: Edge P5P4 (ymax=7, x=0, 1/slope=2)
        Edge P4P3 (ymax=7, x=8, 1/slope=2)
```

# FORMULA & ALGORITHM CHEAT SHEET
## UNIT 1 — Key Formulas

| Formula | Description |
|---|---|
| Total pixels = W × H | Screen resolution |
| Frame buffer (bits) = W × H × Bit_depth | Memory for one frame |
| Frame buffer (MB) = W × H × Bits / (8 × 1024²) | Memory in megabytes |
| Bandwidth = FB_bytes × FPS | Data rate required |
| Colours = 2^(bit_depth) | Number of displayable colours |
| n = ceil(log₂(colours)) | Bits needed for N colours |
| PPI = √(W² + H²) / diagonal_in | Pixels per inch |
| Grey levels (halftone) = n² + 1 | Levels in n×n halftone cell |
| Halftone resolution = DPI / n | Effective resolution after halftoning |

## UNIT 2 — Key Formulas

| Formula | Description |
|---|---|
| \|V\| = √(vx² + vy²) | 2D vector magnitude |
| \|V\| = √(vx²+vy²+vz²) | 3D vector magnitude |
| V̂ = V / \|V\| | Unit vector (normalize) |
| \|R\| = √(\|a\|²+\|b\|²+2\|a\|\|b\|cosθ) | Resultant magnitude (triangle/parallelogram law) |
| tan φ = (\|b\|sinθ) / (\|a\|+\|b\|cosθ) | Direction of resultant |
| a·b = x1x2 + y1y2 + z1z2 | Dot product (component form) |
| a·b = \|a\|\|b\|cosθ | Dot product (geometric form) |
| cosθ = (a·b) / (\|a\|\|b\|) | Angle between vectors |
| A×B = [(a2b3−a3b2), −(a1b3−a3b1), (a1b2−a2b1)] | Cross product |
| \|A×B\| = \|A\|\|B\|sinθ | Magnitude of cross product |
| proj_B(A) = (A·B / \|B\|²) B | Vector projection of A onto B |
| x(t)=x1+t(x2−x1), y(t)=y1+t(y2−y1) | Parametric line |
| x=r cosт, y=r sinт | Parametric circle (origin centred) |
| x=h+r cosт, y=k+r sinт | Parametric circle (centre h,k) |
| x=a cosт, y=b sinт | Parametric ellipse (origin centred) |
| x=at², y=2at | Parametric parabola (y²=4ax) |
| x=a sect, y=b tant | Parametric hyperbola |
| dy/dx = (dy/dt)/(dx/dt) | Differentiation of parametric equations |
| \|A\| = ad−bc (2×2) | Determinant |
| A⁻¹ = adj(A) / \|A\| | Matrix inverse formula |

## UNIT 3 — Algorithm Key Steps

### DDA Line
```
steps = max(|dx|, |dy|)
xInc = dx/steps,  yInc = dy/steps
Loop steps+1 times: Plot(round(x), round(y)); x+=xInc; y+=yInc
```

### Bresenham's Line (0 ≤ m ≤ 1)
```
d₀ = 2dy − dx
If d < 0: d += 2dy           (East: y unchanged)
If d ≥ 0: d += 2(dy−dx); y++ (NE: y increments)
x++ at every step
```

### Midpoint Circle
```
d₀ = 1 − r;  x=0; y=r
If d < 0: d += 2x+3           (East: y unchanged)
If d ≥ 0: d += 2x−2y+5; y--  (SE: y decrements)
x++ at every step; stop when x > y
Plot 8 symmetric points each step
```

### Cohen-Sutherland Codes
```
Bit3=Top(y>ymax), Bit2=Bottom(y<ymin), Bit1=Right(x>xmax), Bit0=Left(x<xmin)
Both 0000 → Accept
AND ≠ 0   → Reject
Else      → Clip at boundary of first set bit
Intersections:
  Left:   x=xmin, y=y1+m(xmin−x1)
  Right:  x=xmax, y=y1+m(xmax−x1)
  Bottom: y=ymin, x=x1+(ymin−y1)/m
  Top:    y=ymax, x=x1+(ymax−y1)/m
```

### Scan-Line Fill
```
Build ET: (ymax, xAtYmin, 1/slope) per non-horizontal edge
For each y bottom→top:
  ET→AET (edges where ymin=y)
  AET remove (edges where ymax=y)
  Sort AET by x
  Fill pixel pairs: AET[0].x → AET[1].x, etc.
  Update each AET edge: x += 1/slope
```

## Quick Concept Reference

| Concept | One-Line Exam Answer |
|---|---|
| Pixel | Smallest addressable unit on screen |
| Rasterization | Determining which pixels best approximate a picture |
| Scan Conversion | Representing continuous image as discrete pixels |
| Frame Buffer | Memory area storing intensity values of all screen pixels |
| Raster Scan | Beam sweeps L→R, T→B, row by row |
| Random Scan | Beam directed only to parts where picture is drawn |
| Refresh Rate | Number of times/second the full screen is redrawn (Hz) |
| Aliasing | Jagged edges from under-sampling (pixel grid ≠ continuous shape) |
| Anti-aliasing | Blending edge pixels with background to smooth jagged edges |
| Dithering | Mixing available colours spatially to simulate unavailable colours |
| Half-toning | Using variable-density dot patterns to simulate grey levels |
| Collinear Points | Points lying on the same straight line |
| Coplanar Points | Points lying on the same plane |
| Scalar | Quantity with magnitude only |
| Vector | Quantity with both magnitude and direction |
| Dot Product | Scalar result; measures alignment; = 0 means perpendicular |
| Cross Product | Vector result; perpendicular to both inputs; used for normals |
| Parametric Eq. | Express curve using independent parameter t; handles all slopes |
| Clipping | Removing parts of objects outside the visible window |
| Flood Fill | Fill connected same-colour region with new colour |
| Boundary Fill | Fill region enclosed by a specific boundary colour |
| Scan-Line Fill | Fill polygon row by row using edge intersection pairs |
| DDA | Line drawing using float increments |
| Bresenham's | Line drawing using integer arithmetic only |
| Midpoint Circle | Circle drawing using 8-fold symmetry and integer decision parameter |

