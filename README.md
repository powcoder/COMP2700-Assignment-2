# COMP2700 Assignment 2

Bad-AES
In this challenge, we consider a modifed version of AES, called Bad-AES, which is the same as AES, but with a modified round function. In this variant, every pair of ShiftRows/MixColumns transformations has been replaced with a PermuteStateMatrix transformation. The ShiftColumns transformation is defined as follows: given a 16 byte. input b_0, b_1,..., b_15, arranged in the AES state matrix: [b_0] [b_4] [b_8][b_12] [b_1][b_5][b_9][b_13] [b_2][b_6][b_10][b_14] [b_3][b_7][b_11][b_15], the result of applying the ShiftColumns transformation produces the following matrix: [b_1][b_12][b_11][b_5] [b_8][b_0][b_7][b_10] [b_3][b_15][b_2][b_6] [b_13][b_14][b_9][b_4]. The Inverse PermuteStateMatrix transformation, as the name suggests, is the inverse of PermuteStateMatrix.
You are given a compressed file badaes.tar.gz (linked below), containing the following files: - sample.txt: This is a sample plaintext. - sample.enc: This is a sample ciphertext, encrypted from sample.txt using Bad-AES with an unknown key, in ECB mode. The last block of the plaintext is padded, using PKCS#7 padding scheme before it was encrypted. - badaes.py: This is a python script implementing Bad AES. It is provided here for you to experiment with the algorithm, to help you with your analysis. - flag.enc: This is a file containing an encrypted flag. The original flag was encrypted using Bad-AES with the same key that was used to encrypt sample.txt.
Your task is to decrypt flag.enc to obtain the original unencrypted flag.
Hint: Use the badeas.py script to experiment with the encryption and the decryption processes, to figure out the relationship between a given plaintext and its corresponding ciphertext. Recall that the key ideas in the construction of a secure block cipher are the concepts of confusion and diffusion. Try to devise some tests to see whether Bad-AES adheres to the concepts of confusion and diffusion, and use what you learn to craft your exploit.
Provide the flag in the answer box below. The flag has the form flag{<some-text>} where <some-text> consists of two or more English words separated by -, for example, flag{hello-world}. Note that you need to include the tag flag{} in your answer, so if the flag you obtained is flag(hello-world} then enter exactly flag(hello-world} in the answer box.
Challenge file: badaes.tar.gz

CBC-MAC
In this challenge, we consider a modified version of the CBC-MAC algorithm, constructed using the AES block cipher, similar to what we have seen in the labs. However, the modified algorithm can take an input of any length, and if the input length is not a multiple of AES block size, then padding bytes are added according to the PKCS#7 padding scheme.
Here you are given a compressed file cbcmac.tar.gz (linked below) containing the following files: - cbcmac.py: This is an implementation of the CBC-MAC algorithm described above. - fst.bin: This is a binary input file, that serves as a sample file for which the MAC (see below) is provided. - mac1.txt: This contains the 16-byte (in HEX string) MAC of fst.bin, computed using a secret key that is not provided. - cbcmac_oracle: This is a 64-bit linux executable file that takes two arguments: a file and a MAC (16 bytes HEX string), and checks whether the given MAC is valid for the file. If you provide as input the file fst.bin above, it will refuse to verify the MAC. The idea is that you should construct a file distinct from fst.bin and its corresponding valid MAC, without knowing the secret key.
Your task is to devise a MAC forgery attack on the cbcmac algorithm described above, by creating a file that is distinct from fst.bin; let's call it snd.bin, and a MAC value for snd.bin, without knowing the MAC key k. You then use cbcmac_oracle to check whether the MAC you constructed is valid for the file snd.bin you created, and if so, the flag will be printed. For example, if your constructed MAC is 0000000001010101020202020303030, run the following command to verify (and get the flag if your MAC is correct for the file snd.bin): $./cbcmac_oracle snd.bin 0000000001010101020202020303030.
Note that cbcmac_oracle restricts the input length of snd.bin to at most 512 bytes for practical reasons, as the solution for this challenge does not require input longer than 512 bytes.
Provide the flag in the answer box below. The flag has the form flag{<some-text>} where <some-text> consists of two or more English words separated by -, for example, flag{hello-world}. Note that you need to include the tag flag{} in your answer, so if the flag you obtained is flag{hello-world} then enter exactly flag{hello-world} in the answer box.
Challenge file: cbcmac.tar.gz


MMO-CTR
In this challenge, we consider a (flawed) variant of Matyas-Meyer-Oseas hash function. The hash function, which we call mmoctr, takes an input of arbitrary length and produces a 16-byte digest.
The mmoctr algorithm works as follows. Given an input m, we first pad m using the PKCS#7 padding, with block size 16 bytes, to obtain m_1. Suppose m_1 has n-blocks: X_1,..., I_n. We fixed an initial value H_0, and compute the values of H_i following a similar recursive scheme to the original MMO. For each input block T_i, we produce an intermediate value H_i as follows: $H_{i}=e_{H_{i - 1}}\left(x_{i}\right) \oplus i$.
The hash value for m is then H_n.
The difference between mmoctr and the original MMO is in the term to the right of ⊕; instead of using x_i like in the original MMO, we use the counter i.
You are given a compressed file mmoctr.tar.gz (linked below) containing the following files: - mmoctr.py: This is an implementation of the mmoctr algorithm described above. - fst.bin: This is a binary input file, that you will use to construct a second-preimage (we will come back to this below). - mmoctr_oracle: This is a 64-bit linux executable file that will verify whether your second-preimage is a correct one, and if so, a flag will be shown.
Your task is to create a second-preimage of the file fst.bin; let's call it snd.bin. The file snd.bin must be distinct from fst.bin but both fst.bin and snd.bin must map to the same hash value according to the mmoctr algorithm above. Once you have constructed snd.bin, verify it using mmoctr_oracle: $./mmoctr_oracle snd.bin.
If your snd.bin is a valid second-preimage to fst.bin, the flag will be shown.
Note that mmoctr_oracle restricts the input length of snd.bin to at most 512 bytes for practical reasons, as the solution for this challenge does not require an input longer than 512 bytes.
Provide the flag in the answer box below. The flag has the form flag{<some-text>} where <some-text> consists of two or more English words separated by -, for example, flag{hello-world}. Note that you need to include the tag flag{} in your answer, so if the flag you obtained is flag{hello-world} then enter exactly flag{hello-world} in the answer box.
Challenge file: mmoctr.tar.gz

# COMP2700 Assignment 2
# 加微信 powcoder

# QQ 1823890830

# Programming Help Add Wechat powcoder

# Email: powcoder@163.com

