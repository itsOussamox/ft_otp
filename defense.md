Goal

This program stores a secret key and later generates a 6-digit one-time password from it.
The time-based part is the important idea: the code changes every 30 seconds, so the password is temporary.
What your program does

In ft_otp, the -g mode reads a file containing a hexadecimal secret key.
It validates that the key is long enough and really hexadecimal.
It saves the key into ft_otp.key in a non-plain-text form and sets restrictive file permissions when possible.
The -k mode reads ft_otp.key, reconstructs the secret, and prints a 6-digit OTP.
The algorithm

Explain that the OTP is based on HOTP from RFC 4226.
To make it time-based, you convert the current Unix time into a counter by dividing by 30.
Then you compute HMAC-SHA1 with the secret key and that counter.
Dynamic truncation picks part of the hash.
The result is reduced modulo 1,000,000 to force exactly 6 digits.
Why the output changes

The time counter changes every 30 seconds.
That is why two calls 60 seconds apart produce different OTPs.
If you run it twice inside the same 30-second window, you should usually get the same OTP.
What you should show to the corrector:

Show key.hex with a valid 64-character hexadecimal key.
Run the save step and show that ft_otp.key gets created.
Run the generate step and show a 6-digit result.
Run it again after waiting about 30 seconds to prove the value changes.
Also show at least one invalid input case, such as a non-hex file or a too-short key, so they see your validation works.
If they ask about your design choices, say this clearly:

I did not use any TOTP library.
I used standard Python libraries only for file I/O, hashing, HMAC, and time.
I followed the required HOTP logic and used the current time as the moving factor.
I kept the output format fixed at exactly 6 digits.