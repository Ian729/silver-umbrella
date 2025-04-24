---
toc: false
layout: post
comments: true
description: Generate 2SV Code Using oathtool
categories: [markdown, tech, tools, security]
title: Generate 2SV Code Using oathtool
---
In modern cybersecurity, two-step verification (2SV) has become an essential method to protect accounts. This article introduces how to use `oathtool` to generate Time-based One-Time Passwords (TOTP) for use with 2SV-enabled services.

## What is oathtool?

`oathtool` is a command-line utility for generating and validating OATH-based One-Time Passwords (OTP). It supports various algorithms and modes, including time-based TOTP.

## Generating TOTP with oathtool

Here is an example command to generate a TOTP using `oathtool`:

```bash
oathtool -b --totp=SHA256 "<your_secret_key>"
```

### Parameter Explanation

- `-b`: Displays the generated password in Base32 encoding.
- `--totp=SHA256`: Specifies the use of the SHA256 algorithm to generate the time-based one-time password.
- `"<your_secret_key>""`: This is your secret key (usually provided by the service).

### Example Output

After running the above command, you will see an output similar to the following:

```plaintext
123456
```

This number is your current TOTP, which can be entered into 2SV-enabled services to complete verification.

## Important Notes

1. Keep your secret key secure and do not share it with others.
2. If you are using a different algorithm (e.g., SHA1 or SHA512), you can specify it by changing the `--totp` parameter.
3. Time synchronization is crucial. Ensure your device's time matches the server's time.

## Conclusion

With `oathtool`, you can easily generate time-based one-time passwords to add an extra layer of security to your accounts. I hope this article helps you!
