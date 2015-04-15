#Use Pin + Simpoint to find Critical Regions in benchmarks

You need to have the pin tool and Simpoint installed. Installation instructions at the end of document.

**To run Simpoint analysis locally with Pin:** Navigate to $PIN/source/tools/PinPoint. type make to compile it. Then make the following modifications in runpinpoints.template.sh:

- SLICE_SIZE: Change this to the number of instructions per region.
- MAXK: The number of critical regions you want to identify.
- CUTOFF: I like to switch this to one.
- PINHOME: The path to the PinPoints directory.
- Find the lines that call pin and replace it with the entire path to the pin executable.
- Somewhere in the beginning of the file add the simpoints executable in your PATH variable as such (replace simpoint_folder as needed):
```bash
export PATH=<simpoint_folder>/bin:$PATH
```

Modify the file named Step2.sh as such:
- Find the lines saying "read TMP &> /dev/null" and comment out the redirection to /dev/null
- Find the line starting with ppgen.3 and get rid of the output redirection as well.
- Get rid of the for loop at the end of the file. It handles alternative simpoints so we don't need it.

These are the modifications needed to make sure the tool is running to completion. Now for each benchmark you want to analyze, the following modifications need to be made:
- PROGRAM: Just the name of the program to run. Could be anything.
- INPUT: Can be anything. Probably "ref" for SPEC benchmarks.
- WORKDIR: The path to the executable you want to analyze.
- COMMAND: The full command (with arguments) to run the executable.

After the modifications, all you need to do is run the runpinpoints.template.sh script. You probably don't need the controller tool running at the end of the script so you can save a few minutes by removing it.

Pin Installation: TODO
Simpoints installation: TODO
