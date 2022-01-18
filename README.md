# pe2shc-to-cdb
This tool will convert shellcode generated using <a target="_blank" href="https://github.com/hasherezade/pe_to_shellcode">pe_to_shellcode</a> to cdb format. Cdb.exe is a LOLBIN which can help evade detection & application whitelisting. More information can be found about it in my <a target="_blank" href="https://mrd0x.com/the-power-of-cdb-debugging-tool/">blog post</a>.

# Requirements

* pe_to_shellcode
* xxd

# Usage

## Step 1
	
	# Generates executable.shc.exe
	pe2shc.exe <executable>

## Step 2

	xxd -i executable.shc.exe > temp.out

## Step 3

	# Generates out.wds
	python cdb.py -f temp.out

## Step 4

	cdb.exe -pd -cf out.wds -o notepad.exe

# Example

The test.exe binary launches calc.exe.

![Example](https://github.com/mrd0x/pe2shc-to-cdb/blob/main/example.gif)

# Limitations

* I had some issues making it work on some executables. Be aware of this in case you face problems.
* Each executable will have a different number of breakpoints. Append 'g' to out.wds as many times as necessary to automatically continue when a breakpoint is hit.