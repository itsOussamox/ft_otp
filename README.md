# ft_otp Bonus QR Mode

This bonus script adds QR seed generation to the original OTP workflow.

Usage

```bash
./ft_otp_qr -g key.hex
./ft_otp_qr -k ft_otp.key
./ft_otp_qr -q
```

What `-q` does

 - Generates a fresh 64-hex-character seed.
 - Saves the encrypted seed in `ft_otp.key`.
 - Creates `ft_otp_qr.png` containing an `otpauth://` QR code.
 - Prints the raw seed so it can also be entered manually if needed.

Install dependency

```bash
pip install -r requirements.txt
```
