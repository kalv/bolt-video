# Bolt Video

Goal: Getting a video of 1080p rendering in 30 fps but at about 90% the size of an MP4. Using a compression approach that I've been calling Weave.

# Goal is video
[90% sure it's a fail] Perhaps start with a video file de-compression into PNGs or images that could be analyzed into a data blob.

! Then the composition of the rendering would be the challenge.
What if it's an avif image files, bundle and then displayed in 30fps over Canvas?

!? Could canvas be used to display an AVIF, the de-compression speed of an AVIF could be the challenge.

Blog post can then describe the limitations of the prototype to just show the potential of the video approach and having the steps outlined in a Github Repo as v10 of the approach to get something working.
The output of the video might be smaller and enough to show progress daily.

Obviously the limitations of this approach is that avif compression of each frame is slow and it's not ideal to work on existing video but shows the size of the video being the size that it could be if AV1 would be used for the image frames.

Taking this tate mcrae music video output 4500 frames in PNG of lossless image quality of X? Then compressing it into AVIF created ?

To use blob splitting of a binary data bundle could add "You can certainly append the byte values representing SOI (0xFF, 0xD8) and EOI (0xFF, 0xD9) to the beginning and end of an AVIF file's binary data." to split up AVIf files if going to bundle them together.

To speed up compressing of PNG files into AVIF, could test out using SWIFT to see if the Apple Accelerate cores to speed up compression.
! Nope, AVFileType on AVKit doesn't support the avif file format. GOOD EXAMPLE OF HOW Gemini would just output some code that is not supported by Mac OS SDKs

AVIF experiment - shows that potentially the bundle will probably be the same size of MP4 but it would be lossless...? Or not really cause AV1 seems to still be a compression based library.

[ ] Back to the drawing board of using the pixel re-use method. Blacks in Tate McRae video for example. 1 frame would be 1 pixel of 8 bytes for one colour. 

v10
Testing out whether images compressed to AVIF would work

v11
Testing out whether images 

v12
Design
- Bundle of pixels from each frame, would need to analyze and add to data bundle file that has the ability to be looked up - can then be delivered in binary blob to the HTML page.
- WebGPU could then draw out those pixels, might be fast enough
! Build - simple hook up of specific styles of computer science functions into WebGPU for this test.

# Recap on Weave Algorithm
Being able to store pixels in a map of lookup table.
IO stream, pointer based byte stream. So that it's buffered into a file. Piped almost.

Then a signature file that defined the draw from 1024 width in a 1,1024 way. Just like a BBC turtle.

# Challenges
- The size of the signature to lookup and draw the rows of pixels. Returning to old scanline drawing.
- Which language to built it in such that it is inter-operable or even demonstratable on kalv.life
    - Originally considered doing this in C, and compiling the algorithm in WASM such that it can run really fast and not be reliant on 
    - Swift applications can then embed this as a C extension for when video needs to be demonstrated. For a better than F1 video services. Netlix, music applications, etc. APPLE all the way.

# History
Started originally working on this in London in 2010.
Back then I got it working in Java Swing thing. with B&W shades only
Then returned to the project in Puerto Escondido in 2022 when leaving Shopify. And have been working on the designs, different implementations such as C on just images first and then have taken some different approaches to use different image compression techniques to see if the image frame would be small enough to achieve the goal.

Shield: [![CC BY-NC-ND 4.0][cc-by-nc-nd-shield]][cc-by-nc-nd]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-NoDerivs 4.0 International License][cc-by-nc-nd].

[![CC BY-NC-ND 4.0][cc-by-nc-nd-image]][cc-by-nc-nd]

[cc-by-nc-nd]: http://creativecommons.org/licenses/by-nc-nd/4.0/
[cc-by-nc-nd-image]: https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png
[cc-by-nc-nd-shield]: https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg
