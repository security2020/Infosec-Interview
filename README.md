# Information Security Interview Questions
collection of interview questions for Information Security domain

## Table of Contents
* [Application Security](#application-security)
* [Encryption](#encryption)
* [Forensics](#forensics)

## Application Security

**Q. If you needed to encrypt and compress data for transmission, which would you do first and why?**

Compress then encrypt. Because encryption takes up resources and can be cumbersome to perform. (If you encrypt first, then compress, then your compression will be useless. Compression doesn't work on random data.) [resource](https://blog.appcanary.com/2016/encrypt-or-compress.html)

## Encryption 

**Q. What’s the difference between encoding, encryption, hashing and Obfuscation ?**

**Encoding** - The purpose of encoding is to transform data so that it can be properly (and safely) consumed by a different type of system, e.g. binary data being sent over email, or viewing special characters on a web page. The goal is not to keep information secret, but rather to ensure that it’s able to be properly consumed.
Encoding transforms data into another format using a scheme that is publicly available so that it can easily be reversed. It does not require a key as the only thing required to decode it is the algorithm that was used to encode it.

**Encryption** - The purpose of encryption is to transform data in order to keep it secret from others, e.g. sending someone a secret letter that only they should be able to read, or securely sending a password over the Internet. Rather than focusing on usability, the goal is to ensure the data cannot be consumed by anyone other than the intended recipient(s).
Encryption transforms data into another format in such a way that only specific individual(s) can reverse the transformation. It uses a key, which is kept secret, in conjunction with the plaintext and the algorithm, in order to perform the encryption operation. As such, the cipher text, algorithm, and key are all required to return to the plaintext.

**Hashing** - Hashing serves the purpose of ensuring integrity, i.e. making it so that if something is changed you can know that it’s changed. Technically, hashing takes arbitrary input and produce a fixed-length string that has the following attributes:

* The same input will always produce the same output.
* Multiple disparate inputs should not produce the same output.
* It should not be possible to go from the output to the input.
* Any modification of a given input should result in drastic change to the hash.

Hashing is used in conjunction with authentication to produce strong evidence that a given message has not been modified. This is accomplished by taking a given input, hashing it, and then signing the hash with the sender’s private key.

When the recipient opens the message, they can then validate the signature of the hash with the sender’s public key and then hash the message themselves and compare it to the hash that was signed by the sender. If they match it is an unmodified message, sent by the correct person.

**Obfuscation** - The purpose of obfuscation is to make something harder to understand, usually for the purposes of making it more difficult to attack or to copy.
One common use is the the obfuscation of source code so that it’s harder to replicate a given product if it is reverse engineered.

It’s important to note that obfuscation is not a strong control (like properly employed encryption) but rather an obstacle. It, like encoding, can often be reversed by using the same technique that obfuscated it. Other times it is simply a manual process that takes time to work through.

Another key thing to realize about obfuscation is that there is a limitation to how obscure the code can become, depending on the content being obscured. If you are obscuring computer code, for example, the limitation is that the result must still be consumable by the computer or else the application will cease to function.

## Forensics
**Q. What is Chain of custody?**

For legal cases the data/device (evidence) needs to be integrated, hence any access needs to be documented – who, what when and why. Compromise in this process can cause legal issues for the parties involved.

**Q. Define steps of forensic process**

Identification > Collection > preservation > Examination > Analysis > Presentation

**Q. difference in raw/dd image and E01 image**

RAW or DD images just contain the data from the original source, and nothing else. Any hash data etc is usually stored in a separate log file that is generally stored with the image file.

EnCase image format includes a separate hash for each segment, and the hash file and certain information about the image - including information entered by the examiner - is stored inside the image files themselves. Hence an E01 is more than just the image, it also contains metadata relating to the image file.

**Q. Difference in Data recovery and Data carving**

Deleted files are recoverable by using some forensic programs if the deleted file’s space is not overwritten by another file.(file flag has been removed by the os. This kind of file are easier to locate)
 
Data carving is different than data recovery in that data carving searches through raw data on a hard drive without using a file system. Data carving is essential for computer forensics investigators to find data when a hard drive’s data is corrupted. (basically it’s a program that can reconstruct file based on fragments.)

**Q. Types of file carving**

1. Header-footer or header-maximum file size carving, 2. File structure based carving (metadata in the file as well), 3. Content based carving (semantics etc.)[Link](https://users.du.se/~hjo/cs/dt2016/presentation/extra_carving_w4.pdf)

**Q. A user reports that they received a suspicious looking email. How do you proceed?**

Collect the original mail from user or collect the mailbox dump, identify the suspicious mail extract them in eml/msg format (to preserve metadata) extract email header from all the files. And based on email headers (usually taken bottom to top approach process) we can identify original sender (X-originating-IP) and mail server (message-id).
 
important fields are
From, to, Subject, date (time zone difference can be issue) CC, BCC, In-reply-to ID, X-Originating-IP, Received and SMTP server hop details. (Link)

**Q: Explain the difference between a logical, file system and physical extraction of a mobile phone.**
**Q: You are given a phone and asked for all location data relating to Los Angeles Airport. Explain how you would conduct your analysis.**



## Credits

[Daniel Miessler](https://danielmiessler.com/study/infosec_interview_questions/),[Peter Benjamin](https://github.com/petermbenjamin), [Jordan Potti](https://jordanpotti.com/2016/12/28/what-to-know-for-your-first-infosec-interview/), [Teckk2](https://teckk2.github.io/misc/2018/01/03/Infosec-Interview_Questions_Part-1.html)
