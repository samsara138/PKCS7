# Usage

```
import PKCS7
padded_data = PKCS7.pad(data, 1024)
is_added, padded_length = is_padded(data)
data = PKCS7.remove_padding(padded_data, 1024)
```
  

# PKCS7 padding scheme improved
For the secure socket, an improved version of PKCS7 padding is implemented, where it doesn't have a maximum block size

PKCS7 is chosen as it has a low chance where data is mistaken as padding

To learn more about PKCS7: [Wiki](https://en.wikipedia.org/wiki/Padding_(cryptography)#PKCS#5_and_PKCS#7)

## PKCS7 Improvment
An improved version of PKCS7 is implemented to allow an unlimited maximum block size instead of the 255 block size limit. To archive this, the new scheme added blocks of 255 * 0xff padding at the end of the block until less than 255 bytes are needed to be padded. In which, it will fall back to the default PKCS7 padding scheme.
```
while padding_length > 255:
        paddings += 0xff * 255
        padding_len -= 255
PKCS7()
```
