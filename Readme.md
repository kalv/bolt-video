# Bolt Video

Goal: Getting a video of 1080p rendering in 30 fps but at about 90% the size of an MP4. Using a compression approach that I've been calling Weave.

# Previous iterations

## Blue Sky test
24th May 2024
Working on a 1024x1024 resolution image of a specific blue.
To see if the theory checks.
57kb image of just a shade of blue.
Hexdump shows that it's a bit stream of one pixel as a raw image. In any programming language, even after JPG decoding or PNG opening.

If weave, 1 object of one colour of 4kb and 1 signature stating the configuration of the draw will be 2kb. Therefore image would be 6kb for a lossles render of the image. 10% of the original size. A reduction of 90%! Got really excited at this opportunity to develop at a company or with funding.

## Signature thinking
I was able to compute the unique pixels out of images with a C library created. But the challenge become the size of being able to plot the x,y of the frame. As having to have 2 pointers to a pixl reference vs in PNG which would just stream them row after row.

## Image signature extraction
I started to work on an `eat(1,1)` function that would better determine the pixels related to the next left X and the top Y and bottom Y to better understand where the pixels would need to be drawn.

Ideas to optimize this would be to use:
- GPU or faster analysis of a frame to better compute unique pixels per frame, as I want to use this for video eventually.
- Using multiple cores to fire recursive growing technique of being able to slowly reduce the the image to nothing and recording the positioning of the pixels and then optimizing that data blob post into an optimized size of signature of rendering.
- Using the recursive lookup function based on the cores and parallel processing of the functions, made me investigate the best language that would allow parallel processing as much as possible.

## Languages and platform testing
- I tested in Ruby/ImageMagick for prototyping and was obviously slow but allowed me to test out the algorithm
- SQLite3 DB wasm storage but found that this is more for dynamic web based content and not something low level as this
- Swift and the potential of using the neural cores which are the same in all machines including the cheapest macbook air m2 that I was using.
- Raw C is where I ended up constructing more of what I wanted to do. Code I no longer I have.

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

# Things to look up later
https://github.com/vapoursynth/vapoursynth
https://github.com/master-of-zen/Av1an?tab=readme-ov-file

# Current conclusion
I've decided to work on another project until I can get some others to work with me on this but really I have been surprised at the quality of existing video streams and the bandwidth we have. So knowing that in 2025 the video we have is good enough. The BBC iplayer is the best I've seen so far.

Shield: [![CC BY-NC-ND 4.0][cc-by-nc-nd-shield]][cc-by-nc-nd]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-NoDerivs 4.0 International License][cc-by-nc-nd].

[![CC BY-NC-ND 4.0][cc-by-nc-nd-image]][cc-by-nc-nd]

[cc-by-nc-nd]: http://creativecommons.org/licenses/by-nc-nd/4.0/
[cc-by-nc-nd-image]: https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png
[cc-by-nc-nd-shield]: https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg
