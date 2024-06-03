# another-draco-injector-script
the name is pretty self explanatory huh?

A simple bash script made with help of ChatGPT 4o. 

## Usage
1. Download injector for your arch.
2. Extract the archive.
3. Open up terminal in the extracted folder and do
   ```
   touch injector.sh | chmod +x injector.sh
   ```
4. Open up the newly made `injector.sh` file in notepad and paste the following and save.
5. Now, put original minecraft apk named `minecraft.apk` in the same folder and open up terminal and run
   ```
   sh injector.sh
   ```
6. It will do its job now.

```
#!/bin/bash

# Prompt the user for the app name and package ID (optional)
read -p "Enter the app name (optional): " appname
read -p "Enter the package ID (optional): " packageid

# Prompt the user for the output filename
while true; do
    read -p "Enter the output filename: " outputfilename

    # Check if the output filename is provided
    if [ -z "$outputfilename" ]; then
        echo "Error: Output filename is mandatory."
    else
        # Add ".apk" extension if not already present
        if [ ! "$(echo "$outputfilename" | grep -E '\.apk$')" ]; then
            outputfilename="$outputfilename.apk"
        fi
        break
    fi
done

# Start building the command
command="./injector minecraft.apk -o $outputfilename"

# Add appname if provided
if [ -n "$appname" ]; then
    command+=" -a $appname"
fi

# Add packageid if provided
if [ -n "$packageid" ]; then
    command+=" -p $packageid"
fi

# Output the command
echo
echo [!] EXECUTING $command
echo 

# Execute the command with automatic yes response
eval $command

```
