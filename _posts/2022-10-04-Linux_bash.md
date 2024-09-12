---
title: Linux Bash Lab
commentable: true
Edit: 2022-10-04
mathjax: true
mermaid: true
tags: Linux
categories: Lab
description: Linux bash exercise
---

Linux bash练习

```bash
#!/bin/bash

# This checks if the number of arguments is correct
# If the number of arguments is incorrect ( $# != 2) print error message and exit
if [[ $# != 2 ]]
then
  echo "Usage: backup.sh target_directory_name destination_directory_name"
  exit
fi

# This checks if argument 1 and argument 2 are valid directory paths
if [[ ! -d $1 ]] || [[ ! -d $2 ]]
then
  echo "Invalid directory path provided"
  exit
fi

# [TASK 1] Assign the first and second arguments to respective variables
targetDirectory=$1
destinationDirectory=$2

# [TASK 2] Print the target and destination directories
echo "Target Directory: $targetDirectory"
echo "Destination Directory: $destinationDirectory"

# [TASK 3] Get the current timestamp in the format YYYYMMDDHHMMSS
currentTS=$(date +"%Y%m%d%H%M%S")

# [TASK 4] Create the backup file name with the timestamp
backupFileName="backup-$currentTS.tar.gz"

# We're going to:
  # 1: Go into the target directory
  # 2: Create the backup file
  # 3: Move the backup file to the destination directory

# To make things easier, we will define some useful variables...

# [TASK 5] Get the absolute path of the target directory
origAbsPath=$(cd "$targetDirectory"; pwd)

# [TASK 6] Change to the target directory
cd "$targetDirectory" || exit

# Get the absolute path of the destination directory
destDirAbsPath=$(cd "$destinationDirectory"; pwd)

# [TASK 7] Change back to the initial directory (probably the script's working directory)
cd -

# [TASK 8] Get yesterday's timestamp in the format YYYYMMDD
yesterdayTS=$(date -d "yesterday" +"%Y%m%d")

# Create an array of files that have been modified since yesterday
declare -a toBackup

# [TASK 9] Loop over files in the target directory that were modified since yesterday
for file in $(find "$origAbsPath" -type f -newermt "$yesterdayTS")
do
  # [TASK 10] Check if the file is readable
  if [[ -r $file ]]
  then
    # [TASK 11] Add the file to the list of files to back up
    toBackup+=("$file")
  fi
done

# [TASK 12] Create the backup file by archiving the collected files
tar -czf "$backupFileName" "${toBackup[@]}"

# [TASK 13] Move the backup file to the destination directory
mv "$backupFileName" "$destDirAbsPath"

echo "Backup completed successfully! File saved to: $destDirAbsPath/$backupFileName"

```