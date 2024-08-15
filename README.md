# THM-Forensics-Case-B4DM755
This is a semi-writeup for TryHackMe\'s Digital Forensics Case B4DM755.
I don't list every question's answers here, acting as a tutorial, but
rather show what I worked on. I gain practical experience using FTK
Imager to create and analyze a disk image for artifacts that would be
presented as evidence. A Write-Blocker would be used to mount the drive
in order to prevent any accidental tampering that would ruin the
evidence.

## Taking an Image and Checking for Encryption

A leftover flash drive was found at the scene of a crime. It's mounted
to a write-blocker and is sent to the Forensics Lab. The drive is
checked for encryption, then an image is taken to create a copy.

![image3](https://github.com/user-attachments/assets/ab9e634d-f228-4304-8246-b4cfd4f929dc)


![image1](https://github.com/user-attachments/assets/f9fc473f-bc50-404d-a1c1-ab378c730254)


![image4](https://github.com/user-attachments/assets/21e96a51-ffeb-47fe-abc1-ce90ab09562a)


The image's integrity is verified by checking the hashes of the physical
drive and the disk image. Once verified, the physical flash drive is no
longer needed and is sent back.

![image8](https://github.com/user-attachments/assets/7f4fc58f-6b3d-45f8-87ea-1d9041858ff7)


![image12](https://github.com/user-attachments/assets/3ee66ede-72c3-4691-be4c-ec29778efe64)


## Analyzing the Image for Evidence

Now I can look through the contents of the drive and see if there is
anything suspicious or noteworthy

![image10](https://github.com/user-attachments/assets/69bd7075-c7e9-43dc-8066-c70a97d8482c)


I can see corrupted files with 0 kb size and files that were deleted,
labeled with a red X on the icon. I can also click on files to view the
header and see if it matches what the file type is listed as. I can also
export all the files to my desktop to preserve it, with deleted and
corrupted files included but nonfunctional of course.

Some deleted files have a file size to them, hideout.pdf warehouse.pdf
and operations.xlsx, however I can't open them up as I get prompted with
an error. I also notice that "Exif" is in the header of these files, so
I will use exiftool to verify the file type and see if it was obfuscated
by the suspect to hide evidence.

![image9](https://github.com/user-attachments/assets/2a34ae68-c8d0-4057-b3b7-3d34628100d2)

![image11](https://github.com/user-attachments/assets/df074b1f-db08-427c-b996-f96052797e00)


It looks like hideout.pdf and warehouse.pdf are images and
operations.xlsx is a zip file. I can see additional details regarding
the images, including timestamps and even the model of the camera/phone
used to take it.

![image13](https://github.com/user-attachments/assets/6b08f072-4120-495c-a6da-3ba73441e625)


![image6](https://github.com/user-attachments/assets/2eedad5f-5e82-41ac-93c6-202523c307a8)

Changing the file extensions of the images to .jpg and opening them up
displays pictures, of course, of the warehouse and hideout. Changing the
file extension of the .xlsx to .zip shows additional files within it.

![image5](https://github.com/user-attachments/assets/f46f973c-fe0c-4dce-b97a-a94ae48a5e80)


I can find the password to pandorasbox.zip within the notes.txt file
(along with details of transactions involving hundreds of millions of
dollars, along with geo coordinates) and then I extract all of the files
out of the .zip. From there, I can open the unsuspecting file titled
"DONOTOPEN" and find a hidden flag.

![image7](https://github.com/user-attachments/assets/2815518d-6306-4b42-8aa7-e68a2d155633)


I can also find other files related to trading algorithms with important
information

![image2](https://github.com/user-attachments/assets/2b8b575e-3172-4156-9d0a-955667ac60a4)


All the evidence I listed here, along with other existing documents I
haven't mentioned containing other suspects' names, can be used to
prosecute in a court of law.
