foo | tee output.file
For example, if you only care about stdout:

ls -a | tee output.file
If you want to include stderr, do:

program [arguments...] 2>&1 | tee outfile
2>&1 redirects channel 2 (stderr/standard error) into channel 1 (stdout/standard output), such that both is written as stdout. It is also directed to the given output file as of the tee command.

Furthermore, if you want to append to the log file, use tee -a as:

program [arguments...] 2>&1 | tee -a outfile
