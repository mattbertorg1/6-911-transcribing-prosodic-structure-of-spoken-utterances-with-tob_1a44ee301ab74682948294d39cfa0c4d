---
course_id: 6-911-transcribing-prosodic-structure-of-spoken-utterances-with-tobi-january-iap-2006
layout: course_section
parent_title: Lecture Notes
title: 'Appendix 2: Praat Script to Load Multiple Files'
type: course
uid: 23af36f911eba169a7ec9008b53165b7

---

Chapters: [1.0]({{< baseurl >}}/sections/lecture-notes/chapter1_0) | [2.0]({{< baseurl >}}/sections/lecture-notes/chapter2_0) | [2.1]({{< baseurl >}}/sections/lecture-notes/chapter2_1) | [2.2]({{< baseurl >}}/sections/lecture-notes/chapter2_2) | [2.3]({{< baseurl >}}/sections/lecture-notes/chapter2_3) | [2.4]({{< baseurl >}}/sections/lecture-notes/chapter2_4) | [2.5]({{< baseurl >}}/sections/lecture-notes/chapter2_5) | [2.6]({{< baseurl >}}/sections/lecture-notes/chapter2_6) | [2.7]({{< baseurl >}}/sections/lecture-notes/chapter2_7) | [2.8]({{< baseurl >}}/sections/lecture-notes/chapter2_8) | [2.9]({{< baseurl >}}/sections/lecture-notes/chapter2_9) | [2.10]({{< baseurl >}}/sections/lecture-notes/chapter2_10) | [2.11]({{< baseurl >}}/sections/lecture-notes/chapter2_11) | [2.12]({{< baseurl >}}/sections/lecture-notes/chapter2_12) | [Appendix 1]({{< baseurl >}}/sections/lecture-notes/appendix1) | Appendix 2

#OpenToBI

\# This script prompts for a list of file name, and opens each .wav  
\# file corresponding .TextGrid files from a specified directory.

tobidir$ = "."  
examples$ = "tobi\_examples"

clearinfo

form Open .wav and text grid  
text file\_list  
endform

while length(file\_list$) > 0  
list\_length = length(file\_list$)  
firstspace = index(file\_list$, " ")  
if firstspace = 0  
file\_name$ = file\_list$  
file\_list$ = ""  
else  
file\_name$ = left$(file\_list$,firstspace-1)  
file\_list$ = mid$(file\_list$,firstspace+1,list\_length-firstspace)  
endif

sound\_file$ = tobidir$+"/"+examples$+"/"+file\_name$+".wav"  
if fileReadable(sound\_file$)  
Read from file... 'sound\_file$'  
else  
printline 'sound\_file$' is not readable  
endif

text\_file$ = tobidir$+"/"+examples$+"/"+file\_name$+".TextGrid"  
if fileReadable(text\_file$)  
Read from file... 'text\_file$'  
else  
printline 'text\_file$' is not readable  
endif  
endwhile