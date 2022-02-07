---
title: Introduction
type: docs
---

# Introduction


[WiTTY](https://github.com/syssecfsu/witty) is a cross-platform, open-source, web-based terminal emulator. It exports the terminal interface on the server (i.e., where WiTTY runs) to the browser. Simply run WiTTY on a computer and give it the command to execute when users connect via the browser. WiTTY has the following features that distinguish itself from other similar tools:

1. WiTTY allows users to **easily record, replay, and share console sessions** with just a few clicks. 

   {{< hint info >}}  
   WiTTY was designed to help teach courses that use UNIX-like command-line interface, such as the software and system security parts of [the SEED labs](https://seedsecuritylabs.org/Labs_20.04/). The biggest challenge in teaching a large such course in the era of pandemic is how to answer students' questions **in the first try**, avoiding long exchange of emails and screenshots. WiTTY makes it a breeze to answer such questions. It is much easier to spot problems with the full history of  console sessions. 
   {{< /hint >}}

   {{< hint info >}}
   Instructors can also record their demos in WiTTY and send them to students. Students can replay these demons however they want. This would help them better understand the knowledge. 
   {{< /hint >}}

2. It allows others to **view ongoing interactive sessions**. This is useful for providing live remote help. 

   {{< hint info >}} 
   An envisioned use of this feature is to allow students to view live sessions of demos by the instructors. It can also allow live, remote help to students. 

   A challenge of this use case is that our home networks are almost always behind NAT, making it difficult to run WiTTY as a publicly accessible server. Security is also potentially a concern.
   {{< /hint >}}

3. Great attention has been paid to ensure the cleanses of the code. This, hopefully, provides a useful counter-example of **Do as I say, but not as I do**. 