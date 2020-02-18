---
path: samba
date: 2020-02-17T15:52:00.000Z
title: Ubuntu 19.10 Samba server, MacOS Catalina (10.15) Finder / SMB performance
description: Optimizing my SMB server for macOS
---

# Version numbers
Macbook Pro 15" 2017 running 10.15.3

Desktop running ubuntu 19.10

Samba 4.10.7


# Benchmarking speeds with Blackmagic Disk Speed Test
Free app in macapp store

## 1TB Internal Hard Drive

## 1TB External Hard Drive
.6 - .9 MB/s

1 MB/s



# Using macOS VFS objects
smb.conf (ubuntu):
```
vfs objects = recycle catia fruit streams_xattr
fruit:aapl = yes
fruit:encoding = native
fruit:locking = none
fruit:metadata = stream
fruit:resource = file
```

macOS stats:
```
kevins-mbp:~ kevinchau$ smbutil statshares -a

==================================================================================================
SHARE                         ATTRIBUTE TYPE                VALUE
==================================================================================================
MyPassport                    
                              SERVER_NAME                   192.168.86.35
                              USER_ID                       501
                              SMB_NEGOTIATE                 SMBV_NEG_SMB1_ENABLED
                              SMB_NEGOTIATE                 SMBV_NEG_SMB2_ENABLED
                              SMB_NEGOTIATE                 SMBV_NEG_SMB3_ENABLED
                              SMB_VERSION                   SMB_3.02
                              SMB_SHARE_TYPE                DISK
                              SIGNING_SUPPORTED             TRUE
                              EXTENDED_SECURITY_SUPPORTED   TRUE
                              UNIX_SUPPORT                  TRUE
                              LARGE_FILE_SUPPORTED          TRUE
                              OS_X_SERVER                   TRUE
                              DFS_SUPPORTED                 TRUE
                              FILE_LEASING_SUPPORTED        TRUE
                              MULTI_CREDIT_SUPPORTED        TRUE
                              ENCRYPTION_SUPPORTED          TRUE

--------------------------------------------------------------------------------------------------
```

This however seems to disable writing to the share

stats without changes to smb.conf:
```
kevins-mbp:~ kevinchau$ smbutil statshares -a

==================================================================================================
SHARE                         ATTRIBUTE TYPE                VALUE
==================================================================================================
MyPassport                    
                              SERVER_NAME                   192.168.86.35
                              USER_ID                       501
                              SMB_NEGOTIATE                 SMBV_NEG_SMB1_ENABLED
                              SMB_NEGOTIATE                 SMBV_NEG_SMB2_ENABLED
                              SMB_NEGOTIATE                 SMBV_NEG_SMB3_ENABLED
                              SMB_VERSION                   SMB_3.02
                              SMB_SHARE_TYPE                DISK
                              SIGNING_SUPPORTED             TRUE
                              EXTENDED_SECURITY_SUPPORTED   TRUE
                              LARGE_FILE_SUPPORTED          TRUE
                              FILE_IDS_SUPPORTED            TRUE
                              DFS_SUPPORTED                 TRUE
                              FILE_LEASING_SUPPORTED        TRUE
                              MULTI_CREDIT_SUPPORTED        TRUE
                              ENCRYPTION_SUPPORTED          TRUE

--------------------------------------------------------------------------------------------------
```

## only VFS objects line:
smb.conf (ubuntu):
```
vfs objects = recycle catia fruit streams_xattr
```
Same results as above. Importnat thing to note is SMB is version 3.02

## only fruit and streams_xattr
```
vfs objects = fruit streams_xattr
```
same results

## only fruit
```
vfs objects = fruit
```

smbutil shows OS_X_SERVER is true, and I can write to the disk! 
Doesn't seem much faster

Time for a speed test:
1.0 - 1.3 MB/s speed. Maybe a little faster...

I think streams_xattr was causing the write issue

## only fruit and recycle with other fruit config
```
vfs objects = recycle fruit
fruit:aapl = yes
fruit:encoding = native
fruit:locking = none
fruit:metadata = stream
fruit:resource = file
```

Same speed test results, ~1.0 MB/s

## Disabling client signing:
mac terminal:
```
printf "[default]\nsigning_required=no\n" | sudo tee /etc/nsmb.conf >/dev/null
```

Pretty much same speeds

# Ignore .DS_Store files over SMB, should speed up browsing / display:
https://support.studionetworksolutions.com/hc/en-us/articles/360000938163-Folder-contents-slow-to-display-Mac-SMB-

defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool TRUE

didn't seem to increase browing speed. Let me try a full logout like the guide suggests


# Downgrading mac to SMB2
/etc/nsmb.conf:
```
[default]
protocol_vers_map=2
```

Then smbutil shows SMB version 2.1

Same speed

# External vs Ubuntu (Internal Drive)
Pretty much the same speed, ~1MB/s

## Speed test on ubuntu
8-10 Mbps

# I think the bottle neck is WiFi
Seems pretty typical for wifi speeds


# Looking for non-samba solutions
Doesn't seem like there are any OS native solutions, samba might be the best thing


For files under 10MB, over wifi is only not bad / more convenient than looking for wires / usb media. Only takes about 5-10 seconds

# Another moral of this story.
Basically all this extra configuration didn't do anything

## Recycle module doesn't seem to add any recycling feature for macOS


