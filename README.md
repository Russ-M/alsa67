# alsa67
Linux AES67 driver for ALSA

No open-source implementation of AES67 yet exists that does not require ffmpeg/libavconv or gstreamer. This repo aims to fix that and provide a basis for further development by others. During development these excellent utilities (ffmpeg, libavconv & gstreamer) may be employed for testing but the end goal is a standalone loadable kernel module.

alsa67 will expose ALSA pcm's to incoming and outgoing AES67 multicast flows, defined by SDP via SAP through a suitable Ethernet adaptor.

MILESTONES ::

1) The driver accepting incoming multicast streams from Dante Controller, after scanning the multicast address range 239.69.0.0 - 239.69.255.255/16 for suitable SDP's and automatically making them available as an ALSA capture PCM. A default configuration can be applied by /etc/alsa67.conf which includes masking or selection of unsuitable/suitable streams/SDP's according to name, ID, sanmplerate, source, etc. A command line utility could scan and list details of suitable sessions from found SDP's.

2) The driver correctly driving interrupts for alsa-lib to process PLAYBACK buffers, after sync'ing its word clock to PTP. Thus, alsa67 becomes clocked to external devices and is therefore applicable in a professional environment.

3) The driver correctly spawning multicast or unicast streams and transmitting the appropriate SDP via SAP such that Dante Controller may discover the audio streams for patching to a Dante receiver.

4) The driver correctly responding to interrupts from alsa-lib to process RECORD buffers, after sync'ing its word clock to PTP. Thus, alsa67 becomes clocked to external devices and is therefore applicable in a professional environment.

No claims to alsa67 participating in PTP clock master delegation are envisaged at this stage - although that may come later. alsa67 shall be a clock slave for the time being.






