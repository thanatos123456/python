## Codec for MIF Approach

This program contains both encoder and decoder for the proposed multi-frame in-loop filter (MIF). 

Usage: first, run a Python program for predicting the enhanced frames, and then run the modified HM encoder or decoder. 

Note: the existing executable files were complied on Ubuntu 18.04 (64-bit). If encounter with trouble or need to run on Windows, please rebuild the program.

Steps:

1. Install TensorFlow. Versions $\ge$ 1.8.0 are recommended.

2. Edit <font color="#0040c0">*cfg.dat*</font>. Fill the file with "LDP [end]", "LDB [end]" or "RA [end]", to specific the configuration for a    bit-stream file (\*.bin).

3. Ensure there exists no any signal file, <font color="#0040c0">*pred_start.sig*</font> or <font color="#0040c0">*pred_end.sig*</font>, because these files will be generated later, for communication between the HM encoder and the Python program during their running.

4. Run <font color="#0040c0">*enhance_one_frame.py*</font> with Python 3.5 or higher, wait for about 1~10s, until "Python: Tensorflow initialized" is shown.

(Encoder)

5. Configure the input raw YUV file in <font color="#0040c0">*encoder_yuv_source.cfg*</font> and QP value in <font color="#0040c0">*encoder_randomaccess_main.cfg*</font>.

6. Run <font color="#0040c0">*TAppEncoderStatic*</font>.

   Example: <font color="#0040c0">*RUN_ENC_RA.sh*</font>

(Decoder)

5. Choose the bit-stream file to be decoded, and copy the corresponding log file to this folder. Then, rename the log file as <font color="#0040c0">*log.txt*</font>, which will be read by the decoder.

6. Run <font color="#0040c0">*TAppDecoderStatic*</font>.


​       Example: <font color="#0040c0">*RUN_DEC.sh*</font>

After encoding and decoding, <font color="#0040c0">*rec.yuv*</font> is the output file for the proposed MIF approach. Other YUV files, such as <font color="#0040c0">*rec_nof.yuv*</font>, <font color="#0040c0">*rec_enhanced.yuv*</font> and <font color="#0040c0">*rec_enhanced_total.yuv*</font>, are intermediate files and can be safely deleted.
