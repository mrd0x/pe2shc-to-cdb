# pe2shc-to-cdb
Convert shellcode generated using <a target="_blank" href="https://github.com/hasherezade/pe_to_shellcode">pe_to_shellcode</a> to cdb format.

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