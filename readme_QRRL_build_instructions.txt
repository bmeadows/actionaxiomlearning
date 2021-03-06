OVERVIEW:

Requires SWI-Prolog (version 6 or higher) to run.

The core components of the architecture are contained in the main file 'qRRL.pl'. Several more files must be present in the same directory:
- 'parameters.pl'
- 'meta.pl'
- 'rrl_domain.pl'
- 'data_collector.pl'


BUILD INSTRUCTIONS:

It is recommended to first become familiar with the content of the file 'parameters.pl' which specifies parameters controlling the behaviour of each part of the system.
Before running, ensure these are set to appropriate values. The file provided has certain default parameters set.

Create or modify the file 'rrl_domain.pl' describing the domain the architecture will operate over. The file provided contains an example of the format required.
The provided version of the file is configured to learn failure cases for one target action in a simple simulated robot domain.


RUN INSTRUCTIONS:

To run the program, consult the main file with SWI-Prolog (swipl.exe). For example, open the terminal in the directory containing 'qRRL.pl' and enter
  ?- consult(qRRL).
or open the file 'qRRL.pl' itself in SWI-Prolog.

To begin learning, enter run(Filename), specifying the file to send final output axioms to, for example:
  ?- run('learned.txt').

A batch processing interface is available that operates analogously by entering runbatch(CounterFilename, ErrorFilename, TimeFilename). For example:
  ?- runbatch('counter.txt', 'error.txt', 'time.txt').
This command can be run multiple times. Each time it is run, it completes a session of the learning architecture, and then updates the run data that is stored in the output files.
An example of this for Windows operating systems is given in the file 'scriptrrl.bat'.
Batch processing uses the batch_collect_data function in the supporting file 'data_collector.pl' to analyse the information on true positives, false positives, and CPU time, that was generated over multiple trials.
The collated results are printed to the file 'post_analysis.txt'.
