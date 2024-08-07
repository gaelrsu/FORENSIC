# Disk Forensics

File Structure Insight: Being able to navigate and see the disk's file hierarchy is crucial. Top-tier forensic tools should display this structure, allowing quick access to specific files, especially in known locations on a suspect system.

Hex Viewer: For those moments when you need to get up close and personal with your data, viewing files in hexadecimal is essential. This capability is especially handy when dealing with threats like tailored malware or unique exploits.

Web Artifacts Analysis: With so much user data tied to web activities, a forensic tool must efficiently sift through and present this data. It's a game-changer when you're piecing together events leading up to a user landing on a malicious website.

Email Carving: Sometimes, the trail leads to internal threats. Maybe it's a rogue employee or just someone who slipped up. In such cases, emails often hold the key. A tool that can extract and present this data streamlines the process, making it easier to connect the dots.

Image Viewer: At times, the images stored on systems can tell a story of their own. Whether it's for policy checks or deeper dives, having a built-in viewer is a boon.

Metadata Analysis: Details like file creation timestamps, hashes, and disk location can be invaluable. Consider a scenario where you're trying to match the launch time of an app with a malware alert. Such correlations can be the linchpin in your investigation.

## Tool 

[FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) 
Create an image of a disk. \
Select File -> Create Disk Image -> select the media source -> Choose the destination -> select the image type -> start

[Arsenal Image Mounter](https://arsenalrecon.com/downloads) 
 mount a disk image \
 
[AFF4 Imager](https://github.com/Velocidex/c-aff4) 
Create and duplicate a forensic disk image. extract files based on their creation time, segment volumes, and reduce the time taken for imaging through compression.

[Active@ Disk Editor](https://www.disk-editor.org/index.html) 
viewing and modifying of raw disk data, including the Master File Table of an NTFS system.

[Autopsy](https://www.autopsy.com/)

















