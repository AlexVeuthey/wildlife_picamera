# Wildlife camera using a Raspberry Pi

The need for this project arose when we lost our cat during an afternoon "walk". 
She was not used to the surroundings, 
and we wanted to track the outside activity before setting humane
traps around the building (and potentially keeping other animals enclosed until the next morning).

I had on hand a Raspberry Pi (model 3B) with a NOIR V2 camera that fitted the needs!

## Goals

Capturing videos would not be practical in this use case, as the power and disk space
available on the Pi are both limited (shooting outside removed access to internet connectivity 
and power supply). Everything had to be handled on-site.

The chosen approach was to write a general purpose script for taking pictures with `picamera`,
and run it periodically with a simple cron job. The frequency of the snapshots was set
to 4 per minute.

After the camera is setup and powered up on location, the cron job will continuously call 
the script to take pictures until either (a) the power supply runs dry or (b) the free disk
space runs out. In case (b), the cron job keeps calling the script, but captures fail due to
lack of free space.

## Hardware setup

My Pi enclosure had mounting points for the camera modules, so that the Pi and camera
assembly was just one tight package. Since we needed to capture images outside, 
the power was provided by a standard USB power bank (5000mAh).

The SD card mounted in the Pi was 16GB only, with around 7GB of free space
for images at the time.

I was very surprised when we observed that this setup was capable of capturing images
for almost **12 hours** before running out of power! The disk space was not full, and it
would therefore have been possible to capture more images per minute.

## Results

Very fortunately, we found our cat holed up in a tree a couple of hours after setting
the camera setup for the first time. We still kept it going for the night, in order to
see how long the battery would hold, but we took the assembly home and did not capture
any interesting snapshots in the short period it was outside.