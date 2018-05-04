# fasta_parser
A python (v 2.7) library that implements a fasta / multi-fasta parser with some useful features.

## **Contacts**
Michele Berselli, <berselli.michele@gmail.com>

## **Importing the library**
To use the library simply `import fasta_parser` into your code.

## **Usage**
The library implements the objects *FastaHandler* and *FastaSequence*.

### **FastaHandler**
The FastaHandler is an object that stores the fasta sequences as FastaSequence objects. 

#### Initialize the object
Initialize the object with `handler = fasta_parser.FastaHandler()`.

#### Parse input fasta file
Different methods can be used to parse the fasta file:

 - **parse(** *inputfile* **)** method parses inputfile and saves the fasta sequences as string of characters. 
  
	`handler.parse('inputfile.fas')`
 
 - **parse_binary(** *inputfile* **)** method parses inputfile and saves the fasta sequences with a binary encoding to reduce memory usage (two bits per base). Requires sequences containing only canonical bases A, C, G, T.
  
	`handler.parse_binary('inputfile.fas')`
 
 - **parse_generator(** *inputfile* **)** method parses inpufile and creates a generator of the sequences, each iteration returns a tuple in the form (header, sequence).
  
	`IT = handler.parse_generator('inputfile.fas')`

#### Access sequences stored in the object
To access the stored sequences differrent methods can be used:

 - **iter_sequences( )** method creates a generator of the stored sequences, each iteration returns a FastaSequence object.
	
	`IT = handler.iter_sequences()`

 - **get_sequences( )** method returns the list of the stored sequences as a list of FastaSequence objects.
	
	`handler.get_sequences()`

 - **write_sequences(** *fo, max_char_per_line* **)** method writes the sequences in fasta format to buffer (*fo*) using a maximum (*max_char_per_line number*) of characters per line.

	`handler.write_sequences(fo, [max])`

### **FastaSequence**
The FastaSequence is an object that stores the information for a fasta sequences. Contains the header of the sequence and the sequence itself. The sequence can be stored as a string of charachters or as a bitarray that represents the binary encoding for the sequence (two bits per character).

#### Initialize the object
Initialize the object with `sequence = fasta_parser.FastaSequence(header, sequence)`.

#### Access information stored in the object

 - **get_header( )** method returns the header for the sequence (without >).
	
	`sequence.get_header()`

 - **get_sequence( )** method returns the sequence as a string of characters.

	`sequence.get_sequence()`

 - **get_bitarray( )** metod returns the sequence as binary encoded in a bitarray object. Requires that the sequence is stored as a bitarray.

	`sequence.get_bitarray()`

 - **write_sequence(** *fo, max_char_per_line* **)** method writes the sequence in fasta format to buffer (*fo*) using a maximum (*max_char_per_line number*) of characters per line.

	`sequence.write_sequence(fo, [max])`

## **Libraries** 
*bitarray* library is required

