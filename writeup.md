# R STANDS ALONE

**Flag:** `nite{7h3_Latt1c3_kn0ws_Ur_Pr1m3s_very_vvery_v3Ry_w3LLL}`

---



### SOLUTION

First,
Observed the code and got to know that this is very very similar to rsa encryption.
I remember searching online on how to solve similar problems and often came across python code that solved this

So I analyzed that code and knew I needed to:
1. Find the modular inverse of the public exponent to get the private key exponent
2. Use this private key to decrypt the given message



---

Next,
I just followed these steps I learnt earlier from reference code to solve the problem

1. **Mod Inverse:**
   I used the `mod_inverse` function from `sympy` module (unlike the Crypto.Util.number like mentioned in reference code, because i had used this earlier) to calculate this.

2. **Decrypting the Message:** 
   Once I had `e_inv`,(which is the private key) I could use it to decrypt the message using modular exponentiation, which actually reverses the encryption
![image](https://github.com/user-attachments/assets/c0fe44c8-d7b3-4311-a7da-e176b39359c1)

### CODE:

```python
from sympy import mod_inverse

r = 170897208475225321861009044953729547960865234393434011901235722431299057534746780948450698789024859359839031510037922598851007198165422566469211147823588506546694221540562810861243141061590539954106792039>
e = 65537
c = 583923134770560329725969597854974954817875793223201855918544947864454662723867635785399659016709076642873878052382188776671557362982072671970362761186980877612369359390225243415378728776179883524>

phi = r - 1
e_inv = mod_inverse(e, phi)

x = pow(c, e_inv, r)

print("x",x)
```



---

Finally, 
```
Just used long_to_bytes() to get the byte expression of that number and there it was!
```
![image](https://github.com/user-attachments/assets/dad4a318-ca34-4239-9b2a-d92338876888)

### CODE:
```python
from Crypto.Util.number import long_to_bytes

num = 1224543274432953164098494823673082544474888158727042278518055942472603042171050926269717319080882631327061394998314354487201417153661
flag = long_to_bytes(num)

print(flag)
```


---


References (goat 🙏)

- https://b0mk35h.medium.com/unlocking-secrets-a-beginners-guide-to-rsa-decryption-in-python-89a71ccda295
