---
title: Record Sessions
weight: 4
---
# Record Sessions

You can record an ongoing session in the interactive terminal window. 

![img](/static/img/interactive.png)

Recorded sessions will be listed in the main window of WiTTY. You can click the {{<img src="/static/img/edit.svg" width="16px">}} button to rename a recorded session. By default, a recorded session is named based on its session ID and the current time, not very meaningful for human. Rename them to something easy to remember, such as `task1`, `task2`,...

![img](/static/img/rename.png)

WiTTY provides two sub-commands to merge and replay recorded sessions. 

   - ```witty merge -o <output_file> <record1> <record2> ...```
   - ```witty replay -w <wait_time> <recorded_session>```
   
Recorded sessions often have long delay between outputs. You can set `wait_time` of the `replay` command to limit the maximum wait time between outputs, to speed up the replay. 

The following screenshot shows how to use ```witty merge``` to merge three recorded sessions into `alltasks.scr`.

<img src="/static/img/merge.png" width="640px">

{{< hint info>}}
The intended use of this is to record a separate session for each individual task, rename and merge them into a final session for submission to a project.  
{{< /hint >}}

{{< hint info>}}
All the recorded sessions are located under the ```records``` directory.
{{< /hint >}}