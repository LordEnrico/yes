README-D6.0A.txt  18 January 2012

Copyright © 2011 and 2012 by the Regents of the University of Michigan acting as agent for the MTS Consortium and licensed under the Creative Commons Attribution 3.0 Unported License (CC BY 3.0). See the file COPYRIGHT.txt for details.


          Description of the MTS d6.0A.zip distribution archive 
          -----------------------------------------------------         

Corrections, questions, comments, and suggestions are all welcome.  Post them to the H390-MTS e-mail list or send them to mts-comments@umich.edu.

The D6.0A version of MTS allows interested persons to run the D6.0 version of MTS under the Hercules S/370 Emulator without the need to restore the D6.0 system from simulated tapes. Working directly with the MTS D6.0 distribution materials it was and remains possible to create an IPLable version of MTS. The D6.0A system makes this easier by providing a IPLable version of MTS on Hercules simulated disks. The D6.0A system includes several updates and fixes to resolve problems with the D6.0 system and to allow MTS to operate more easily under Hercules.

The D6.0A distribution archive is available for download from the MTS Archive (http://archive.michigan-terminal-system.org/mts-d60A). In the future we hope to make the D6.0A archive available from the Software Archive at Bitsavers.org as well as from U-M's Deep Blue Digital Archive.

Distribution D6.0 supports the IBM S/370 and the IBM S/370-XA architectures. Distribution D6.0A has been configured to use the IBM S/370-XA architecture which Hercules supports as EAS/390. This is machine architecture code "MP" in the MTS D6.0 Installation Instructions for New Installations (D6.0-NEWSYS.txt).

In addition to the d6.0A.zip archive, it is recommended that the d6.0.tar.gz archive be downloaded as well since it contains the full set of D6.0 *FS distribution tapes and a number of documentation files that will be useful when using D6.0A. The d6.0A.tar.gz archive may be downloaded from http://bitsavers.org/bits/univOfMichigan/mts/d6.0.tar.gz.

d6.0A.zip archive contents
--------------------------

Included as part of D6.0A you will find:

README-D6.0A.txt  This file.
COPYRIGHT.txt     The copyright, license, and limitation of liability 
                  statement for the MTS distribution materials.
README.txt        An updated version of the file that describes the 
                  entire collection of MTS distribution materials.
hercules.cnf      A template configuration file for use by Hercules.
Disks             A directory that contains simulated disk files.
  mts600.dsk and  A compressed simulated 3380-1 disk image and
  mts600_1.dsk    an associated shadow file for use with Hercules.
Units             A directory that contains three unit record files
  PCH1.txt        The file for card punch, PCH1
  PTR2.txt        The file for printer, PTR2
  RDR1.txt        The file for card reader, RDR1. It contains three 
                  "card" images.
Tapes             A directory that contains files for the simulated AWS tapes
  cmd001.aws      A simulated tape for use by the CMDSTAT pickup program, *DWB
  d6.0tn.aws      The simulated tapes for the six *FS tapes from D6.0.
mtsDistDoc/d6.0   Directories that hold D6.0 documentation
  OperatorsManual-MTSD6.0-1988.pdf  The MTS D6.0 Operator's Manual
  HASPManual-MTSD6.0-1988.pdf       The MTS D6.0 HASP Manual

MTS was restored from the D6.0 distribution tapes to create the disk image. The restored disk was updated to become version D6.0A and includes several bug fixes to resolve problems with the D6.0 version and to allow the system to operate more smoothly under the Hercules Emulator. 

The base mts600.dsk file contains the D6.0 system as it was restored from tape. The first shadow file, mts600_1.dsk, contains the updates that were made to create the D6.0A system. As distributed these two files are read-only and so when they are used by Hercules a third shadow file, mts600_2.dsk, will be created to contain the changes from your use of the system. It is possible to revert to previous versions of the disk contents by removing one or both of the shadow files using the Hercules -sf command.

Additional documentation
------------------------

Information about the Hercules System/370 Emulator is available:

  * from the Hercules website (http://www.hercules-390.org/).
  
Additional MTS documentation is available:

  * in the "Michigan Terminal System" Wikipedia article 
    (http://en.wikipedia.org/wiki/Michigan_Terminal_System),
  * in the PDF archive at Bitsavers.org 
    (http://www.bitsavers.org/pdf/univOfMichigan/mts/), 
  * in the "Computing Center" collection within 
    "Archival Collections -- Bentley Library" in the Deep Blue archive 
    at the University of Michigan 
    (http://deepblue.lib.umich.edu/handle/2027.42/79570), 
  * in the "Michigan Terminal System (MTS)" public collection of the 
    Hathi Trust Digital Library 
    (http://babel.hathitrust.org/cgi/mb?a=listis;c=937729558), and
  * on the simulated MTS distribution tapes included in the MTS 
    distribution archive (http://www.bitsavers.org/bits/univOfMichigan/mts/), 
    and
  * from the MTS Archive (http://archive.Michigan-Terminal-System.org/).

Steps to run the D6.0A version of MTS under Hercules
----------------------------------------------------

There are several screen shots available that show many of these steps, see: http://MTS-Hercules.BlogSpot.com/. 

1.    Edit the hercules.cnf template to tailor it to your environment.
2.    Place the d6.0A folder from the d6.0A.zip archive in an 
      appropriate place. 
3.    Add the ten aws files from the d6.0.tar.gz archive to 
      the Tapes directory or comment out those device definitions in the hercules.cnf file.
4.    From a terminal or command window make the D6.0A folder your current
      directory (cd d6.0A). 
5.    From the terminal or command window start Hercules. 
5a.   There will be a good deal of output to the Hercules console.
5b.   An error message of the form
        HHCTT001W Timer thread set priority -20 failed: Permission denied
      is expected and can be ignored.
5c.   The content of the messages displayed will make it clear that 
      the hercules.cnf file is being used.
6.    List the files in the Disks subdirectory to confirm that the second
      shadow disk file, mts600_2.dsk, has been created. If it hasn't 
      been created, you might want to use the Hercules sf+ command 
      before proceeding. 
7.    Open a tn3270 connection to port 3270 on "localhost" to act as the 
      MTS Operator's console. 
8.    Read Q27 and Q28 from the FAQ section of this file below to learn 
      a little bit about the MTS 3270 Operator's Console.
9.    Type "ipl 260" on the Hercules console. 
      The D6.0A system should now be running from disk.
      (later, when you are finished running MTS you must
       shutdown properly -- see step #17 and Q30 below)
      The IPLReader will use address 001 as its console.
      This address will be passed to the supervisor initialization routine, 
      CONFIG, which will use the same console.
      When the Operator job starts it will use the first operational
      device from the list of CON2 (01F), DS01 (001), and DS21 (101) and
      so by good fortune or good planning DS01 (001) will remain the MTS 
      console device.
      Messages should appear on the MTS console (address 001, device DS01).
      The Hercules console will act as the MTS console log printer (address 
      009, device CON1).
      If you forget to start the tn3270 session or the session isn't associated 
      with address 001, the 1052-C console/printer at address 009 will be used 
      by the MTS backup console support. The backup console support is a pain 
      to use and so is to be avoided.
10.   Answer "yes" to the question "Do you want to run the current system" 
      on the MTS Operator's console.
11.   MTS will display the local time and may ask if it is OK. If asked, 
      always reply "ok" since it isn't possible to set the TOD clock in 
      the Hercules environment. You will be using the default timezone 
      and timezone offset built into TABLES, initially 
      Eastern Standard Time (EST) which is GMT minus 5 hours. 
      If this isn't you timezone, this isn't ideal and can be fixed by 
      patching TABLES as described in question Q18 below.
11a.  You may be prompted:
        MTS   Current time of hh:mm day mmm dd is more than 12 hours later than                                
        MTS   last recorded signoff time of hh:mm day mmm yy.                                                 
        MTS   If you are sure the time is set correctly, enter "OK" to proceed                             
        MTS   with IPL; otherwise re-IPL now.
      Respond to this prompt as you think best.
12.   Respond to the prompts:
        Enter initials and reason for reloading: 
          [enter a line of text]
        ** *CHK: Routine check for offline devices.                                                    
        ** Just cancel after you have checked the offline devices.
          [remember that PA2 is "cancel", it is normal for a few
           devices that aren't configured in the .cnf file to be offline]
13.   You'll see a number of status messages, including:
                      ** UMMPS/XA ** assembled 04/19/88                                                                
             CONFIG  CPU 0000 online                                                                                   
               INIT  Time and date have been set to  hh:mm:ss on mm-dd-yy.                                             
           OPERATOR    Started at mm:mm:hh on mm-dd-yy  Model 3090 Serial 000611                                       
           OPERATOR    Using display DS01 & printer CON1 (1052)
        PDP  MTS600 on D400 (*PAG001         )
        MTS   Contents of IPL file "*IPL.0":
        MTS   Filesave directory update completed
        MTS   *CMD: The CMDSTAT pickup program has been started.
        MTS   THE ACCOUNTING FILE IS AVAILABLE
        MTS   0*** Post-IPL system successfully loaded.
        MTS  *NAL complete                                                                                  
        MTS  PEEK initialization begins                                                                     
        MTS  PEEK initialization complete 
14.   Open additional tn3270 sessions to port 3270 on "localhost" to use 
      as MTS 3270 terminals.
15.   Once you see the message "MTS PEEK initialization complete" system 
      initialization is complete and you can:
          start HASP: type "HASP" followed by "MTS *HSP" (see Q19 below)
          "let out the lines" (line adaptor start): type "MTS *LAS" 
          start individual MTS jobs on 3270 displays: type MTS DSnn 
          and pretty much anything else you want to do.
15a.  Before you start HASP, see questions Q19, Q20, Q21, Q25, and Q26 below.
15b.  If you start HASP, you'll see the following messages:
            HASP  HASP initialization -- phase 2                                                                    
        HASPLING  $*Enter HASP requests                                                                             
15c.  When you start *HSP, you'll see the following messages:                                                                                         
        HASPLING  $*OK                                                                                              
        HASPLING  $*OK                                                                                              
             MTS  HASP START (17 January 2012) 
15d.  You can release batch execution with the HASP command 
        $RELEASE EX 
      and you will see:  
        HASPLING  $*OK 
15e.  When you start *LAS, you will see:                                                                                
        MTS  Line configuration (17 January 2012)                                                                 
        MTS  Jobs on: DS02-DS05                                                                                
        MTS    Other: *CLK, *TPR, *MGR, *TCM, *FTPSERV                                                         
        MTS  The Messagefile Manager has started up successfully                                               
        MTS   There are no available Telnet (TLNT) connections.
      The very last message above about no available Telnet connections Is
      expected and has to do with the lack of a Host Interface machine
      or HIM under Hercules.   
16.   Continue with steps 12, 13, and 14 as described in the 
      D6.0-NEWSYS.txt writeup. Proceed with the start-up procedures 
      described in the MTS Operator's Manual.       
13-B. This step is optional, you may or may not need to change *LAS.
13-C. This step is optional.
13-D. This step isn't possible since ASMH is a licensed program product and 
         not included as part of D6.0.
13-E. This step isn't possible without ASMH, but see question Q18 below. 
13-F. This step is optional. One disk will probably be enough for many people.
13-G. This step isn't possible without ASMH.
14.   It is a good idea to read over this step.
14-I. This step is optional and most people don't need or want to 
      install real rates.
17.   See question Q30 below for information about shutting MTS down.
18.   Optionally exit from Hercules.
19.   To restart MTS: If you exited from Hercules, go back to step #5 above. 
      If Hercules is still running, go to step #7 above.


Changes made to the D6.0A version of MTS
----------------------------------------

The hercules.cnf template Hercules configuration file was created to serve as a starting point for configuring Hercules to run the D6.0A system.

PDF versions of the D6.0 MTS Operator's Manual and the D6.0 HASP Manual were created to make it easier to access this information.

The simulated 3380 disk and its associated shadow files were created by restoring MTS from the D6.0 dump/restore tapes. The base disk represents the D6.0 system as it was restored from the simulated tapes. The first shadow file includes the updates and fixes made to the base system to create the D6.0A system. It is recommended that shadow files two and above be used to hold the changes that you make to the D6.0A system.

The following updates and fixes were applied to create the D6.0A system from the D6.0 system:

 1. Permitted the files etc:tape? correctly to allow the use of the generic cataloged tape names MTS:TAPE, MTS:TAPEn (where n is a number from 0 to 9) by non-privileged users with the $Mount command avoiding the need to use *TAPESUBMIT to register tapes before they are used.
 2. Created a new versions of the internal system module RSF (Really Shared Files) and persub (permit subroutine) to resolve a date and time rollover problem that occurs on or after 9 November 1989.
 3. Patched tables to rearrange OPERDEVS so that CON2, DS01, and DS21 are operator consoles and CON1 is an console log printer. 
 4. Patched TABLES to change the device type of CON1 (0009) from 3270 to 1052. Then if address 0009 is defined as a 1052-c device in the hercules.cnf file the MTS operator's console log appears in the Hercules log.  
 5. Patched the default time zone name and offset in TABLES to EST and GMT minus 5 hours. The patch in REP cards can serve as an example for others who wish to change the default time zone name and offset. See Q18 below.
 6. Enabled a RAMROD log file and changed the IPLVOL option in RAMROD from MTS001 to MTS600.
 7. Created a new resident system in Ramrod and saved it to *IPL.0 so that it will be used by default when the system is IPLed.
 8. Increased the amount of disk space that is available to HASP and did a HASP FORMAT COLD start to initialize HASP for regular use.
 9. Fixed the HASP log (*HLG) and UNSP:HASPLOG.
10. Fixed *CMD and *DWB to work properly and provided a simulated AWS tape for use when the Command Statistics Pickup process (*DWB) asks to mount a tape from time to time. The tape is associated with T90A (018A).
11. Fixed a problem that caused errors when accessing 3420 tape drives. D6.0A should work with 3420s regardless of what version of Hercules is being used (3.07 or later at least) and 3480 tape drives should not be configured for use with D6.0A.
12. *CLK (Clock Watcher) has been fixed so that it no longer loops creating  huge log files that it tries to print using *PRINT*.
13. The *-file jobs *LAS (Line Adapter Start) and *HSP (HASP Start) were
    modified to match the device configuration in the hercules.cnf file.


Frequently Asked Questions (FAQ)
--------------------------------

The following are questions that arose on the Hercules-390 and H390-MTS e-mail groups in the first several weeks after the MTS distributions became available on Bitsavers.org on 22 December 2011. Some questions are omitted because they apply to D6.0, but not to D6.0A.

Q1 Where is MTS available?

A1: The MTS distributions starting with D1.0 (1968) through D6.0 (1988) are available in several tar.gz archives on the Bitsavers Software Archive, see:  http://bitsavers.org/bits/univOfMichigan/mts.

Q2: What are the terms under which MTS is being made available?

A2: MTS is copyright © by the Regents of the University of Michigan acting as agent for the MTS Consortium and is being made freely available under a Creative Commons Attribution 3.0 license (CC BY 3.0, http://creativecommons.org/licenses/by/3.0/). The license allows one to use, copy, adapt, share, distribute, and transmit the work provided that one attributes the work by including the copyright statement and the name of the work, version number, volume reference, or date of publication that identifies the work in the copies or adaptations made. For additional information, see:  http://archive.michigan-terminal-system.org/documentation/mts-distributions#TOC-COPYRIGHT.txt-14-November-2011 or the COPYRIGHT.txt file included with the MTS distribution materials on the Bitsavers.org Software Archive.

Q3: What is included in the MTS distributions?

A3: The distributions include source code, object code, and documentation. There is a README.txt file available in the Bitsavers Software Archive that describes what is available in detail.  The README file is also available as a Web page, see: 
     http://archive.michigan-terminal-system.org/documentation/mts-distributions.

Q4: Do the MTS distributions include everything that was part of MTS?

A4: No, the distributions only include the materials that the MTS Consortium was able to distribute free of copyright or license restrictions. This means that various program products are not included.  None of the excluded materials are required to use MTS, but the absence of the MTS version of ASMH is a sometimes painful shortcoming since various MTS programs and configuration files can't be reassembled because they depend on the MTS version of ASMH. The MTS version of ASMH was based on the IBM Assembler H Program Product and included SLAC and MTS specific enhancements.

Q5: Does MTS run under Hercules?

A5: Yes, several people have gotten the D6.0 version of MTS running under Hercules. The D6.0A version was developed and tested using Hercules. For information about Hercules, see: 
        http://www.hercules-390.org/.

Q6: Is a runnable version of MTS available?

A6: Yes. With a bit of work one can create a runnable version of an MTS starter system based on the D6.0 distribution from 1988. Several people with little or no knowledge of MTS have been successful doing this. Version D6.0A is an IPLable disk based version of D6.0 MTS.  It allows someone to run MTS under Hercules more or less directly without the need to restore the system from "tape".  D6.0A also fixes some of the problems that people have encountered when using the D6.0 version of MTS under Hercules.

Q7: Is D6.0 the latest or final version of MTS?

A7: No.  D6.0 is the last formal distribution of MTS. It was sent out in 1988.  MTS continued to be developed and used at the University of Michigan (U-M) until 1996 and at RPI until 1999. While there is no distribution for later versions of MTS, work is being done now to create an IPLable version of MTS based on the system that was running at U-M in 1996 shortly before MTS was shutdown for the last time. While we don't know exactly when that version of MTS will be available, there is hope that it will be sometime in the first half of 2012.

Q8: What are the differences between the D6.0 and the 1996 versions of MTS?

A8: There isn't a complete list of the differences, but here is a partial list.

The 1996 version:

    fixes several bugs that were present in the D6.0 system;
    includes support for cartridge tapes;
    uses the Resource Manager (RM) rather than HASP as its spooling system;
    has support for user programs that use 31-bit addressing;
    has new versions of the CMDSTAT programs, CMDPIKUP (*CMD) and 
        CMDTAPE (*DWB) written in PLUS; and
    several utility job programs, broadcast, init, signonm, and stop, 
        were rewritten in PLUS. 

Q9: Should someone wait for the 1996 IPLable version or start working with the D6.0 or D6.0A versions now?

A9: This will depend on how much time you have, how much effort you want to put into getting a version of MTS running, and how soon you want to be able to run MTS.  Getting MTS working from scratch using D6.0 will take much more effort than working with the D6.0A or the D1996.0 IPLable system when it becomes available. For many people installing the D6.0 starter system from "tape" is likely to be a frustrating experience. There are certainly bugs in the D6.0 version that were fixed after D6.0 was released in 1988. The D6.0A IPLable version should be available sometime during January 2012. It isn't yet clear exactly how long it will take to make the D1996.0 IPLable version of MTS available, but it is likely to take several months and possibly longer. Some people will want the experience of making a version of MTS available from "scratch" and so will be happy to start working with D6.0 now. Others will want to skip that work and will use the D6.0A version or the D1996.0 IPLable version when it is available.

Q10: Is there an e-mail list or group where issues related to running MTS under Hercules are discussed?

A10: Yes.  Such discussions started out on the main Hercules-390 Yahoo group e-mail list, but moved to the new H390-MTS Yahoo group at the start of 2012. You need to join the groups to receive messages from and post messages to both of these lists. 
    For H390-MTS go to: 
       http://tech.groups.yahoo.com/group/H390-MTS/. 
    For Hercules-390 go to: 
       http://tech.groups.yahoo.com/group/hercules-390/.

Q11: If someone wants to try running the D6.0A version of MTS using Hercules, how do they get started?

A11: Start by reading the following documents that are available in the MTS Software Archive at Bitsavers.org:

    README.txt;
    COPYRIGHT.txt;
    D6.0-NOTES.txt; and
    D6.0-NEWSYS.txt.
    
    Next read the rest of this FAQ.

The documents listed above plus several others are also available as Web pages or PDF files at: 
 http://archive.michigan-terminal-system.org/documentation#TOC-MTS-Distributions.

If you don't know much about MTS, you'll want to look at some of the MTS Volumes. MTS Volume 1 is a good place to start. MTS Volume 2 documents the public files that are available under MTS. MTS Volume 4 contains information on terminal support in MTS including the 3270 display. Some versions of MTS Volume 4 did not include the 3270 description, but the PDF files available at Bitsavers.org and in Deep Blue do. A list of MTS Documentation is available on the MTS Archive Web site: http://archive.michigan-terminal-system.org/documentation. Some of the documentation listed postdates D6.0 (1988). Tutorial and other documents are available online from the Hathi Trust Digital Library, see: http://babel.hathitrust.org/cgi/mb?a=listis;c=1889583521.

If you don't know much about Hercules, you'll want to look at some of the documentation available at http://www.hercules-390.org/ and you will need a version of a 3270 terminal emulator to use as an MTS Operator's console and as an MTS terminal. See: 
 http://archive.michigan-terminal-system.org/discussions/mts-today/3270terminalemulators for more information.

When you are ready, follow the instructions in the NEWSYS.txt writeup. A summary of the necessary steps is provided at the end of this FAQ.

Q12: What does a Hercules configuration file to run MTS look like?

A12: A sample Hercules configuration file is available at http://archive.michigan-terminal-system.org/documentation/documents/MTSD6.0A.cnf. A listing of this file is included near the end of this FAQ.

Q13: Omitted

Q14: When I try to use the $Mount command to mount a simulated magnetic tape, an error occurs. What do I need to do differently?

A14: When mounting tapes use the generic tape name "MTS:TAPEn" on the $Mount command where "n" is a digit from 0 to 9.

For example:
   $Mount MTS:TAPE1 9TP *T* lbltype=VLO vol=volumelabel
   $Run *FS 0=*T*
   list (n)    [n is the number of the file on the *FS tape 
                that you want to restore]
   restore (n)
    . . .
   stop
   $Release *T*

where:
	*  MTS:TAPEn is a generic tape name on the D6.0 starter system that
		allows non-privileged users to mount tapes that haven't been submitted
		using *TAPESUBMIT;
	 *  volumelabel is the tape's volume label; and
	 *  lbltype=VLO should only be used for Volume Label Only tapes, which the D6.0 *FS tapes are.

Third, see also Q29 below.

Q15: Is everything from the *FS distribution tapes also available on the disk based starter MTS system, once it has been created?

A15: No, only some of the items from the *FS tapes are included on the disk based starter system. You can tell which files are on the disk based starter system by looking at the Disk Name field toward the end of a component's entry in the distribution driver file listing (D6.0-LIST.txt). If the Disk Name is blank or if it ends with the suffix @UM, the file is not on the starter system and will need to be restored from the *FS tape, if it is needed/desired.

Q16: How does one get items off of the *FS tapes that are used to distribute MTS components?

A16: Once you have a running version of MTS, you can $Mount the tapes and run the *FS program. See MTS Volume 1 for a description of the $Mount command and MTS Volume 2 for a description of the *FS program. MTS Volume 19 has the most detailed information on using magnetic tapes in MTS. You can also extract items from AWS format simulated tapes including *FS format tapes without running MTS by using the lbltp program that is available in the MTS Software Archive at Bitsavers.org. The README.txt file has more information about the lbltp program, the distribution process, and the distribution driver file.

The distribution driver file listing (D6.0-LIST.txt) is probably the best source of information on how all of the parts of MTS fit together. The listing contains comments about most components and many sub-components, is a directory to other information sources contained in the distribution materials, and shows the tape name and file number for components on the *FS tapes as well as the file names for components included on the starter system disk.  The distribution index file (D6.0-INDEX.txt) can be helpful in finding specific items in the distribution driver file listing, but the index does not contain nearly as much useful information as the driver file listing itself.

Q17: Where do I go to find the D6.0 MTS Operator's Manual?

A17: The D6.0 MTS Operator's Manual and the HASP Manual are available on the D6.0 *FS tapes. See the D6.0 distribution driver file listing for details (http://archive.michigan-terminal-system.org/documentation/documents/MTSD6DriverFileListing-April1988.pdf). Text versions of both manuals are also available at http://tech.groups.yahoo.com/group/H390-MTS/files/, but you need to be a member of the H390-MTS Yahoo Group to access them. In addition these files are freely available from the MTS Archive web site, see:  
  http://archive.michigan-terminal-system.org/documentation#TOC-MTS-Distributions
  
    and copies of the PDFs are included in the d6.0A.zip archive

Q18: I can't set the time or timezone and the timezone and timezone offset used by default are EST (Eastern Standar5 Time) and GMT minus 4 hours. This isn't right for my location. How do you change it?

A18: The default values for timezone and timezone offset are configured into the TABLES assembly which is part of the resident system. Normally one would update the TABLES source and reassemble it using *ASMH. However, *ASMH is based on the IBM Assembler H Program Product and so was not included in MTS distributions due to license restrictions. The alternative is to patch TABLES. In this case you don't want to patch the running system, but rather add a REP card to the TABLES object deck using the program MTS:RAMROD. There are instructions on "Patching the System Object Deck" on pages 17 and 18 in the D6.0-NOTES.txt file.  The external symbol TIMEZONE in TABLES is a halfword integer offset in minutes followed by an 8 byte time zone name.

Q18a: I've read the instructions on "Patching the System Object Deck" in the General Notes (D6.0-NOTES.txt), but am having trouble using MTS:RAMROD. Can I have some hints?

A18a: Sure. The RAMROD writeup is available in the file RMRD:RAMROD*PF.  RAMROD has a HELP command. RAMROD works on systems. Systems are made up of an ordered collection of object decks. You can get a list of systems using the RAMROD command LIST.  LIST CURRENT will show you the current system. The RAMROD command CURRENT will make a system the current system, but you don't want to do that until you've created a new system and added your patches. You'll want to create a new system from an existing system (create newsys from existingsys) and make your changes to the new system. The RAMROD PATCH command lets you add one or more REP cards to one of the object decks in a system. You need to know the ESID (usually 1) and the offset within the object deck you wish to patch.  You can figure this out  from the file SEG2:S2MAP. The MTS commands $PEEK and $INFO can also be used to figure out the offset. When you've finished your modifications, use RAMROD's ANNOTATE command to add any additional comments, rename newsys bettersys (some better more meaningful name), and make the better more meaningful named system current.

You've found the instructions on patching the system in the General Notes (D6.0-NOTES.txt), but the following comments from the D6.0 driver file (D6.0-LIST.txt) for component 468/007 (RESIDENT SYSTEM UM RAMROD) might be helpful as well:

The following procedures are used in maintaining this file. Whenever
           a new system is installed i.e., made "current", three things are done:
           
             1.   The name of the system installed is changed to the "model
                  number" of the date it is installed, e.g. "AY108" for May 10,
                  1978. [2nd and 3rd letters of the month name, two digit day
                   of the month and one digit year.]
           
             2.   The system installed is made the current system.
           
             3.   The oldest system is deleted so that there are about five
                  systems, the current one and the four preceding.
           
           When someone wishes to change a component, but not install a new
           system, a new system called "NEWSYS" is created from the current
           system (if it doesn't already exist) and the desired changes made and
           noted using the ANNOTATE command. Then when the NEWSYS system is
           actually to be installed as the running system, the procedure
           above is followed.
           
           A test system can be created at any time with any name, but when the
           new components are ready to be installed, they should be put in
           "NEWSYS" and the test system destroyed.

Q19: I cannot use *PRINT* or *BATCH*. What needs to be done to make them available?

A19: Start HASP using HASP WARM or just HASP from the MTS Operator's Console. Once HASP has started, enter "MTS *HSP" followed by the HASP command $RELEASE EX at the MTS Operator's Console. You may wish to tailor *HSP to your local configuration as outlined in step 13(A) in the D6.0-NEWSYS.txt instructions.  Use "MTS *HPS" to display HASP status.

Q20: Does HASP support 3287 printers? What printers can be used as the MTS console log printer?

A20: No, HASP does not support 3287 printers. A 1403, 3211, 1052, or 3287 printer may be used as the MTS Operator's Console log printer.  In order for a 3287 printer to work, it must be associated with a tn3287 session. Some tn3270 software includes tn3287 emulation.  Issue the %PTR name device command from the request area at the bottom of the MTS Operator's Console to start or switch to a different console log printer, where name is the MTS device name for the printer to be used. Use the %PTR NONE device command to terminate console logging and release the printer.

Q21: I get an error when trying to print to a 1403 printer (HASPLING PTRn: Unrecoverable error - Printer status: 0100 0E00 01:80). How do I work around this?

A21: This is a command reject (x'80') caused when the printer tried to skip to an undefined carriage control channel. To avoid the problem, an MTS carriage control tape needs to be defined for the printer. Unfortunately, this is only possible using relatively newer versions of Hercules. As of early January 2012 the new versions were not available without building Hercules from the source in the SVN repository. And newer Windows snapshots may be available at http://www.ivansoftware.com/snapshots/. If you can get access to a newer version (versions 7000 and later have been reported to work, but bugs related to this support have been reported in those versions too), the Hercules configuration command to use to define the carriage control tape is: 

   addr type filename lpp=66 fcb=1:11,4:1,5:5,8:10,14:6,19:4,24:7,34:2,44:6,49:4,54:7,63:8,66:3 optprint

An alternative that may work with somewhat older versions of Hercules is to include the "nofcbcheck" option. For example: 

  addr type filename nofcbcheck

If the version of Hercules being used does not support either the fcb= or nofcbcheck option, then you will not be able to print using HASP or *PRINT*. You may be able to print directly to a printer when signed on to MTS using a privileged userid (an id that can $Set prot=off), if you avoid the more unusual MTS carriage control options.  Here is an example:

    $Get >PTR2
    $Copy somefile  *AFD*
    $Run someprogram SPRINT=*AFD*
    $Release *AFD*

Adding the @nocc I/O modifier to an FDname will suppress logical carriage control processing and so might help avoid problematic carriage control at the expense of some formatting on the pages printed. For example:

    $Get >PTR2
    $Copy somefile *AFD*@nocc
    $Run someprogram SPRINT=*AFD*@nocc
    $Release *AFD*

Q22: Does MTS include a link editor?

A22: Yes, but the use of a link editor is optional. The MTS loader is a dynamic linking loader that will load output from compilers and assemblers directly. You can use the MTS programs *LINKEDIT and *OBJUTIL to optimize object modules so that they load somewhat faster, but that is the only advantage to using the programs. The programs are described in MTS Volume 2 and MTS Volume 5 contains additional information about the programs, the MTS loader, and MTS object modules.

Q23: The message "*DWB: IS ANOTHER COPY OF *DWB RUNNING?" appears on the MTS Operator's console followed by an input request. What is the message about and how should I respond?

A23: This message should not appear for the D6.0A system. If it does the MTS *-file job *DWB is trying to copy the contents of CMDSTAT (Command Statistics) log files to tape. *DWB is started by *CMD when one of the log file fills up. But a previous version of *DWB appears to still be running. There is some additional information about CMDSTAT in the file D6.0-NEWSYS.txt step 13(C) and more information in the D6.0 MTS Operator's Manual.

Q24: My 3270 terminal session gets signed off from time to time for reasons that are unclear. What is happening?

A24: The 3270 Device Support Routine (DSR) will sign you off after a period of inactivity. You can prevent this by issuing the %timeout device command. You can issue that command every time you sign on by placing the command $Control *MSOURCE* timeout=off into a file and establishing the file as your sign on file or sigfile ($Set sigfile=filename).

Q25: If your HASP spool space fills up, what can you do?

A25: You can increase the amount of disk space available to HASP by:

     1) Optionally creating one or more new files named *SPOOL2, *SPOOL3, …, *SPOOLn using the command: 
              $Create *SPOOLn size=32767P  [where n is a number]
     2) Shutdown and re-IPL and do a HASP cold start and format
              HASP COLD FORMAT
         which will clear any queued jobs and get HASP to use the new larger spool files.

Q26: I'm trying to submit a batch job to HASP from a card reader, but I see that I need an S-8 card. What is an S-8 card and how do I make some?

A26: An S-8 card is the first card in a batch job submitted to MTS or to HASP from a card reader. It has a 0-2-8 over punch in column 1 and also contains a six digit receipt number that identifies the job.  S-8 cards were handed out at the input window, used when the card deck was run through the card reader, and then returned to the user with the rest of their cards to serve as a receipt for the job and any printed or punched output it produces. The S-8 card comes immediately before the MTS $Signon command (don't be confused by the Signon card that is used to sign on a remote RJE station, which is something different entirely).

The MTS *-file job *RCP can be used to punch S-8 cards. *RCP is described on page 269 of the D6.0 MTS Operator's Manual.

S-8 cards are only used for batch job input through a card reader, they are not needed for batch jobs submitted using *BATCH*.

If you read from the card reader directly rather than using HASP, you don't need an S-8 card. You can only do this from a privileged userid (an id that can $Set prot=off):

       $Get >RDR1   [or whatever the device name of the card reader is, and
                     if you were using HASP, you need to get HASP to release 
                     the device first]
       $Create somenewfile
       $Copy *AFD* somenewfile
        . . .
       $Release *AFD*

Q27: What do the various PA, PF, and other keys on the MTS 3270 Operator's console do?

A27: PA1          stops system status output (output from a /xxx command)
     PA2 or CNCL  is "Cancel"
     TEST-REQ     is "Pause"
     ENTER        sends an input line to the system
     CLEAR        refreshes or rewrites the screen
     PF keys      are shortcuts that enter predefined character strings
                  that may or may not be sent to the system as input,
                  if the lines are not sent automatically, they can be
                  sent by pressing the ENTER key. Use the %PF?
                  command to display a list of PF key assignments.

Q28: How is the MTS Operator's Console used?

A28: The screen has five areas: (1) the top two lines display system status load information; (2) the third line displays a list of status alerts and may be empty; (3) a message area in the middle displays messages and input requests from running jobs; (4) a request area near the bottom is used to: (i) start new jobs by entering the job name followed by zero or more parameters, (ii) enter HASP commands which start with a dollar sign ($), (iii) enter system status commands which start with a slash (/), and (iv) enter device commands which start with a percent sign (%); and (5) the last line where the "host" name, machine type, time, and date are displayed.  See pages 325 to 335 in the D6.0 MTS Operator's Manual for more detailed information.

    See Q20 above for information on starting a console log printer.
    
    Use the %WRAP ON device command to cause lines on the screen to wrap rather than be truncated on the right. The console log printer will display longer lines without the need to use the %WRAP command. %WRAP OFF will disable long line wrapping at the console.

Q28a: What does the information on the two lines at the top of the MTS Operator's Console mean?

A28a: This is the system status load information. There is a description on pages 462 and 463 in the D6.0 MTS Operator's Manual. There is also a description of the load line as part of the description of the $Systemstatus command in MTS Volume 1.

	DT   = Delta Time [time in seconds covered by the sample displayed]
	EXQ  = Execution Queue [number of batch jobs waiting to execute]
	PRT  = Print Queue [number of jobs waiting to print]
	PCH  = Punch queue [number of jobs waiting to punch]
	BP   = Batch Preferred [the number of batch jobs the system would 
	                        "like" to be running]
	AB   = Actual Batch [the number of batch jobs actually running]
	BHP  = Batch per Hour [average number of batch jobs completed per hour]
	AL   = Active lines [MTS terminal sessions]
	VP   = Virtual Pages
	RP   = Real Pages
	DPA  = Drum Pages Available [pages available on the high speed 
	                             paging devices, rather than disk]
	PA   = Paging Activity [paging I/O operations per second]
	DA   = Disk Activity [disk I/O operations per second]
	CA   = Channel Activity [channel I/O operations per second, 
	                         includes DA and a portion of PA as well as 
	                         other I/O operations]
	%PI  = Percent Processor Idle
	Q    = Global CPU Queue [jobs waiting for the CPU]
	TQ   = Tape Queue [MTS jobs waiting for one or more tapes 
	                   drives to become available]

If a plus (+) sign appears following some of these values, it indicates that that operation is overloaded. An asterisk (*) appears after BP if any of the other items is overloaded (has a plus sign).

Q29: I'm having problems mounting and using simulated magnetic tapes. What is the problem and what can I do to work around it?

A29: This was a problem in D6.0 that should be fixed in D6.0A. In D6.0A only 3420 tape drives should be configured and used. MTS D6.0 and D6.0A do not include support for 3480 tape drives and they should not be used with D6.0A.

    See also Q14 above.

Q30: Is it important to shut MTS down before exiting from Hercules?  How does one shut MTS down?

A30: Yes, it is important to shut MTS down gracefully before you stop the Hercules processor(s) on which it is running and before you exit from Hercules. If this is not done, there is a fairly small risk that portions of the MTS file system may be left in an inconsistent/corrupted state.

The procedures to shut MTS down are described on pages 52 and 53 in the MTS Operator's Manual. Basically, you should enter the following commands from the MTS Operator's console:

		$HOLD EX
		$DRAIN SYSTEM
		SHUTDOWN ALL

Wait for the message "Shutdown All complete", then issue the system status command:

		/t m

Check the output to see if there are any MTS jobs that did not stop, if there are, $RERUN any batch jobs and try to stop non-batch jobs one by one using the STOP job, once all of the jobs are stopped or it is clear that they won't stop, go ahead and stop the Hercules processors (stopall Hercules command) and exit from Hercules or re-IPL.

Q31: How does one create new userids?

A31: You use the program ACC:ACCMAINT, one of the more arcane programs in MTS.

The *Format source for a writeup is available in component 104/172 (file 547 on d6.0t1). You can produce a formatted version with the command: $Run *Format scards=ACCMAINT*WF sprint=-print. Then $Copy -print to look at the output, or $Copy -print >PTRn to "print" the output, or $Copy -print *Print*, if you have HASP working.

From the userid ACC. $Run ACCMAINT and use a CREATE command to create a new userid (RAF.), with a University account number of 0, with a disk space limit of 10,000 pages, in a new project (WRAF), with several system privileges that might look something like this:

	CRE RAF.,0,,,,,10000,,,,WRAF,LIBRARY=ON,PRIV=ON,PROTECT=ON,PASSWORD=xxxxxxx

The positional parameters in order are: User ID, University account number, IDR number, Unit code, Expiration time, Max charge dollars, Max disk pages, Max terminal minutes, Max plotting minutes, Project owner's name, and Project number, optionally followed by keyword parameters. All of the keyword parameters set system privileges and IDs with these privileges set must be part of a project whose name starts with the letter W (WRAF in the above example). If you want to create regular user ids rather than system user ids, then the project name shouldn't start with the letter W.

A PDF of the "Accounting in MTS" writeup from 1991 is available in the Internal Documentation sub-section of the Documents page on the MTS Archive. Not sure what, if anything, changed between D6.0 in 1988 and 1991. See: 
      http://archive.michigan-terminal-system.org/documentation#TOC-Internal-documentation.

Q32: How does one change the password for an existing userid?

A32: You can reset a password by signing on to the userid WPSW and running the program Program1. If you give it a userid, it will assign a new random password to that id.


A sample Hercules configuration file for use with MTS D6.0A
-----------------------------------------------------------

	#########################################
	# Hercules emulator configuration file  #
	#    Version AN182 (18 January 2012)    #
	#   A template for use with MTS D6.0A   #
	#########################################
	
	# Adjust this template for use in your own environment
	
	# You'll need to put the D6 files in the right places.
	
	# For D6.0, but not for D6.0A you need to create a 
	# 3380 disk image before you start using something 
	# similar to:
	#    dasdinit -z -a MTS600.dsk 3380-1 MTS600
	
	# In general the Hercules device configuration needs to
	# match or at least be a subset of the D6.0 version
	# of TABLES as described in the following list from
	# the D6.0-NEWSYS.txt writeup:
	#
	#    Device Type     Address            Device name
	#    -----------     ---------          -----------
	#
	#    3287            0000               PTR1  
	#    3270            0001-0007          DS01-DS07
	#    3270 (in D5.0)  0009               CON1 (in D6.0)
	#    1052 (in D6.0A) 0009               CON1 (in D6.0A)
	#
	#    2540R           000C               RDR1
	#    2540P           000D               PCH1
	#    1403            000E               PTR2
	#
	#    3270            001F               CON2
	#
	#    3287            0100               PTR3  
	#    3270            0101-011F          DS21-DS3F
	#    3420            0180-018F          T900-T90F
	#
	#    3330            0200-020F          D100-D10F
	#    3350            0220-022F          D200-D20F
	#    3370            0240-024F          D300-D30F
	#    3380            0260-026F          D400-D40F
	#
	#    3420            0C70               T920
	#
	#    9335            0D00-0D03          D500-D503
	#    9335            0E00-0E03          D600-D603
	
	ARCHMODE  ESA/390  # includes 370-XA (MTS architecture code "MP")
	CODEPAGE  437/037
	
	CPUSERIAL 000611
	CPUMODEL  3090
	CPUVERID  FF       # the value FF here causes MTS to bypass
					   # its reguests to set the TOD clock
	MAINSIZE  128
	
	# Adjust the following two values for your local configuration
	# MTS does support operation on multi-CPU configurations with
	# (in theory) up to 32 processors, although 6 processors is likely
	# the maximum number ever used in "real life".
	
	NUMCPU   1 
	MAXCPU   1
	
	XPNDSIZE 0  # D6.0 of MTS will use expanded storage as a write through
				# disk cache, if expanded storage is present
	
	SYSEPOCH 1900
	TZOFFSET -0000  # MTS uses GMT for its TOD clock
	
	# YROFFSET is not needed for the D6.0A or D1996.0 versions of MTS.
	# For D6.0 uncomment the following parameter. 
	
	# YROFFSET -23  # For D6.0, but not D6.0A set the year back to 
					# avoid time/date rollover issues.
					# For D6.0, needs to give dates after D6.0 was 
					# released in 1988, but before November 1989.
	
	CNSLPORT 3270   # the port that tn3270 sessions will use to connect
	OSTAILOR QUIET
	
	###### Device definitions #####
	
	# Display and console devices
	
	# The definition for address 0009 below doesn't match the D6.0 
	# definition in TABLES, but in D6.0A TABLES is patched to make 
	# address 0009 a 1052 console/printer and CON1 will be used as 
	# the MTS Operator's Console log printer with its output directed 
	# to the Hercules console.
	
	0000   3287    # PTR1, a 3270 data stream printer
	0001.7 3270    # DS01 through DS07
	0009   1052-C  # CON1, comment this line out and
	# 0009 3270    # CON1, uncomment this line if you want the
				   #       definition to match the definition
				   #       in the D6.0 version of TABLES 
	001F   3270    # CON2
	0100   3287    # PTR3, a 3270 data stream printer
	0101.7 3270    # DS21 through DS27
	
	# Unit record devices
	
	000C   3505   Units/RDR1.txt ascii eof   # RDR1
	000D   3525   Units/PCH1.txt ascii       # PCH1
	
	# Diferent versions of Hercules support different printer options.
	# Uncomment one of the following three device definitions for addr 000E.
	# The three definitions are listed in order from newest to oldest
	# and from best to worst in terms of functionality. 
	# The fcb= option defines the MTS printer carriage control tape.
	# The nofcbcheck option supresses errors (command reject) when
	# a skip to an undefined printer carriage tape channel is used.
	# If the third (last) option is used, errors will result when 
	# HASP tries to print its head and tail sheets on the printer,
	# effectively making HASP printing unusable.
	
	# 000E 1403   Units/PTR2.txt lpp=66 fcb=1:11,4:1,5:5,8:10,14:6,19:4,24:7,34:2,44:6,49:4,54:7,63:8,66:3 optprint # PTR2
	# 000E 1403   Units/PTR2.txt nofcbcheck  # PTR2
	000E   1403   Units/PTR2.txt             # PTR2
	
	# Tapes
	
	# These ten tape definitions are not required for D6.0A
	# and may be commented out.
	
	0180   3420   Tapes/d6.0util.aws ro  # T900, D6.0 utilities tape
	0181   3420   Tapes/d6.0dr1.aws  ro  # T901, D6.0 IPLable dump/restore tape #1
	0182   3420   Tapes/d6.0dr2.aws  ro  # T902, D6.0 dump/restore tape #2
	0183   3420   Tapes/d6.0dr3.aws  ro  # T903, D6.0 dump/restore tape #3
	0184   3420   Tapes/d6.0t1.aws   ro  # T904, *FS D6.0 distribution tapes #1
	0185   3420   Tapes/d6.0t2.aws   ro  # T905,  " #2
	0186   3420   Tapes/d6.0t3.aws   ro  # T906,  " #3
	0187   3420   Tapes/d6.0t4.aws   ro  # T907,  " #4
	0188   3420   Tapes/d6.0t5.aws   ro  # T908,  " #5
	0189   3420   Tapes/d6.0t6.aws   ro  # T909,  " #6
	
	018A 3420 Tapes/cmd001.aws       # T90A, a CMDSTAT tape for use by *DWB
	
	# Devices 018B through 018F and 0C70 (T90B to T90F and T920) are defined
	# as 9TP (3420) tape drives in TABLES and so could be defined here
	
	# Disk(s)
	
	# Shadow files (sf=) won't be used until the Hercules command "sf+" 
	# is issued, unless the shadow file already exists or the base and 
	# shadow files are read-only in which case a new shadow file will 
	# be created.
	
	0260   3380   Disks/MTS600.dsk sf=Disks/MTS600_*.dsk # D400
	
	# D6.0 and D6.0A of MTS support single density (3380-1), but not 
	# double density (3380-2) or triple density (3380-3), 3380 disks.
	
	# New 3380 disks need to be initialized using dasdinit's -a option 
	# so that the alternate tracks are included. For example:
	#    dasdinit -z -a MTS600.dsk 3380-1 MTS600
	
	# Devices 0200-020F (D100-D10F), 0220-022F (D200-D20F),
	# 0240-024F (D300-D30F) and 0261-026F (D401-D40F) are 
	# defined as 3330, 3350, 3370, and 3380 disks and so
	# copuld be defined here.
	
	# Devices 0D00-0D03 (D500-D503) and 0E00-0E03 (D600-D603) are defined
	# as 9335 disks in the D6.0 and D6.0A TABLES, but there are bugs in
	# the D6.0 and D6.0A 9335 support, so these devices can't be used.
	
	# END

		Mike Alexander     Jeff Ogden             Gavin Eadie
		mta@umich.edu      jeff.ogden@umich.edu   Gavin.Eadie@umich.edu
	
									or
	
						 mts-comments@umich.edu
	
	END