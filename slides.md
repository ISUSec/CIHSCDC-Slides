# How to win CIHSCDC

---

## What's going to happen?

  * You will have a small network containing:

    * Windows boxes of different vintages and varieties (XP/7/8, Server/Home)

    * Linux boxes of different vintages and varieties (Probably Ubuntu [Server])

    * A firewall (Probably pfsense)

    * ???

----

  * You will have to both defend against attackers and perform jobs called
    "injects"

----

  * You'll have a brief setup period and then red team is going to try to break
    all your things

---

## How do we win?

  * Don't get hacked

    * When you do get hacked, fill out incident report forms

  * Do the injects

---

## How is this hard?

  * You will get hacked

    * You'll be going up against professionals with very little time

  * You won't have time to do all the injects

  * Fear, uncertainty, and doubt will plague your team

  * ~~A plague of locusts o'er the land~~

---

## What goes wrong?

(In rough order of commonness)

----

  1. Default passwords (there are more of these than you think)

----

  2. Non-updated computers (old Windows XP security is not your friend)

----

  3. Social Engineering (they literally ask nicely and you listen)

----

  4. People get scared and panicky and fall into a black hole of failure

----

  5. Red team has backdoored your stuff in advance and you didn't notice

    * Red team _has_ backdoored your stuff

    * They also have a box on your network

----

  6. Everything else

---

### Example 1

  * Blue team forgets to change the default password on their Windows server with
    remote desktop enabled

  * Red team knows the default password and logs in

----

### Example 2

  * Blue team forgets to update their Ubuntu server from a vulnerable version

  * Red team googles the version they see running, finds a CVE, and owns the box

----

### Example 3

  * Red team sends an email from wh1teteam@gmail.com with a fake inject telling
    blue team to configure their servers insecurely

  * Blue team listens to them

  * Red team takes advantage of their insecure configuration

----

### Example 4

  * Red team owns a box as above

  * Blue team brings it back online after a reset

  * Red team owns it again in less than 10 seconds because they have a script

---

## How do we make things not go wrong?

  * Work with failure

    * You will fail a lot so this is important

    * Panic is bad

----

  * Have designated roles and plans (more on this later)

----

  * Git gud (at googling)

    * There are a lot of things to know. No one actually knows all of them.
      Pretty much all of them are on stackoverflow somewhere

----

  * Have plans written down

    * You can write down passwords too

----

  * Fix machines before bringing them back up

    * If red team owns you once, they can do it again in <10 seconds

    * Just take the downtime and patch with the system 100% offline

---

## Roles

---

### Team Captain

  * MAKE SURE EVERYTHING IS UPDATED

  * MAKE SURE ALL PASSWORDS ARE CHANGED

  * Have a big picture

  * Be a gopher

----

  * Direct effort

    * Put the buckets on the biggest fires near the most flammable materials

  * Talk to white team

  * (Probably) do incident response forms

  * Don't boss people around

    * This is more keeping things organized than being in charge

---

### Firewall Admin

  * UPDATE

  * CHANGE PASSWORDS

  * Run the firewall

  * Look at outbound connections

----

  * Look at boxes on your network

    * One of these is probably red team

  * If red team owns your firewall, they can kill your whole net

    * This is probably a bad thing

---

### Linux Admin

  * UPDATE

  * CHANGE PASSWORDS

  * Get rid of extra users/processes

    * There are lots of users you can't see. `/etc/passwd` knows all about them

  * `.bash_history` probably has all of red team's stuff in it

  * `chattr +i $FILE` makes a file immutable. `chattr -i $FILE` fixes it.

----

  * Run Enigmail. Otherwise you will get social engineered to death

  * Get rid of setuids

  * IPTSTATE is cool

  * ufw is cool

  * fail2ban is cool

----

  * Monitor

    * `/tmp/`

    * `crontabs`

    * `~/.ssh/` (root also has one of these)

    * `/etc/` _especially_

      * `/etc/passwd`

      * `/etc/shadow`

      * `/etc/sudoers`

---

### Windows Admin

  * UPDATE

  * CHANGE PASSWORDS

  * Get rid of extra users/processes

  * Event viewer is cool

----

  * Autoruns are scary

  * Process explorer is cool

  * TCPView is cool

  * Use your firewall

  * Active Directory is cool

----

  * Windows Group Policy is worth looking at

    * Audit policy especially
