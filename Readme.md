# extract from elf file:
objcopy.exe -O ihex elf_file.elf hexfile.hex

objcopy.exe -O binary elf_file.elf binfile.bin

# convert ihex file to binary:
objcopy.exe -I ihex -O binary hexfile.hex binfile.bin

objcopy.exe --input-target=ihex --output-target=binary hexfile.hex binfile.bin

# convert from binary file to ihex:
objcopy.exe -I binary -O ihex test.bin test.hex

objcopy.exe --input-target=binary --output-target=ihex test.bin test.hex

# // HELP OUTLINE 
objcopy.exe --help


Usage: objcopy.exe [option(s)] in-file [out-file]
 Copies a binary file, possibly transforming it in the process
 
 The options are:
 
  -I --input-target <bfdname>      Assume input file is in format <bfdname>
  
  -O --output-target <bfdname>     Create an output file in format <bfdname>
  
  -B --binary-architecture <arch>  Set output arch, when input is arch-less
  
  -F --target <bfdname>            Set both input and output format to <bfdname>
     --debugging                   Convert debugging information, if possible
     
  -p --preserve-dates              Copy modified/access timestamps to the output
  
  -D --enable-deterministic-archives
                                   Produce deterministic output when stripping archives
                                   
  -U --disable-deterministic-archives
  
                                   Disable -D behavior (default)
                                   
  -j --only-section <name>         Only copy section <name> into the output
  
     --add-gnu-debuglink=<file>    Add section .gnu_debuglink linking to <file>
     
  -R --remove-section <name>       Remove section <name> from the output
  
  -S --strip-all                   Remove all symbol and relocation information
  
  -g --strip-debug                 Remove all debugging symbols & sections
  
     --strip-dwo                   Remove all DWO sections
     
     --strip-unneeded              Remove all symbols not needed by relocations
     
  -N --strip-symbol <name>         Do not copy symbol <name>
  
     --strip-unneeded-symbol <name>
     
                                   Do not copy symbol <name> unless needed by
                                   
                                     relocations
                                     
     --only-keep-debug             Strip everything but the debug information
     
     --extract-dwo                 Copy only DWO sections
     
     --extract-symbol              Remove section contents but keep symbols
     
  -K --keep-symbol <name>          Do not strip symbol <name>
  
     --keep-file-symbols           Do not strip file symbol(s)
     --localize-hidden             Turn all ELF hidden symbols into locals
     
  -L --localize-symbol <name>      Force symbol <name> to be marked as a local
  
     --globalize-symbol <name>     Force symbol <name> to be marked as a global
  -G --keep-global-symbol <name>   Localize all symbols except <name>
  
  -W --weaken-symbol <name>        Force symbol <name> to be marked as a weak
  
     --weaken                      Force all global symbols to be marked as weak
  -w --wildcard                    Permit wildcard in symbol comparison
  
  -x --discard-all                 Remove all non-global symbols
  
  -X --discard-locals              Remove any compiler-generated symbols
  
  -i --interleave[=<number>]       Only copy N out of every <number> bytes
  
     --interleave-width <number>   Set N for --interleave
     
  -b --byte <num>                  Select byte <num> in every interleaved block
  
     --gap-fill <val>              Fill gaps between sections with <val>
     --pad-to <addr>               Pad the last section up to address <addr>
     --set-start <addr>            Set the start address to <addr>
    {--change-start|--adjust-start} <incr>
                                   Add <incr> to the start address
    {--change-addresses|--adjust-vma} <incr>
                                   Add <incr> to LMA, VMA and start addresses
    {--change-section-address|--adjust-section-vma} <name>{=|+|-}<val>
                                   Change LMA and VMA of section <name> by <val>
     --change-section-lma <name>{=|+|-}<val>
                                   Change the LMA of section <name> by <val>
     --change-section-vma <name>{=|+|-}<val>
                                   Change the VMA of section <name> by <val>
    {--[no-]change-warnings|--[no-]adjust-warnings}
                                   Warn if a named section does not exist
     --set-section-flags <name>=<flags>
                                   Set section <name>'s properties to <flags>
     --add-section <name>=<file>   Add section <name> found in <file> to output
     --update-section <name>=<file>
                                   Update contents of section <name> with
                                   contents found in <file>
     --dump-section <name>=<file>  Dump the contents of section <name> into <file>
     --rename-section <old>=<new>[,<flags>] Rename section <old> to <new>
     --long-section-names {enable|disable|keep}
                                   Handle long section names in Coff objects.
     --change-leading-char         Force output format's leading character style
     --remove-leading-char         Remove leading character from global symbols
     --reverse-bytes=<num>         Reverse <num> bytes at a time, in output sections with content
     --redefine-sym <old>=<new>    Redefine symbol name <old> to <new>
     --redefine-syms <file>        --redefine-sym for all symbol pairs 
                                     listed in <file>
     --srec-len <number>           Restrict the length of generated Srecords
     --srec-forceS3                Restrict the type of generated Srecords to S3
     --strip-symbols <file>        -N for all symbols listed in <file>
     --strip-unneeded-symbols <file>
                                   --strip-unneeded-symbol for all symbols listed
                                     in <file>
     --keep-symbols <file>         -K for all symbols listed in <file>
     --localize-symbols <file>     -L for all symbols listed in <file>
     --globalize-symbols <file>    --globalize-symbol for all in <file>
     --keep-global-symbols <file>  -G for all symbols listed in <file>
     --weaken-symbols <file>       -W for all symbols listed in <file>
     --add-symbol <name>=[<section>:]<value>[,<flags>]  Add a symbol
     --alt-machine-code <index>    Use the target's <index>'th alternative machine
     --writable-text               Mark the output text as writable
     --readonly-text               Make the output text write protected
     --pure                        Mark the output file as demand paged
     --impure                      Mark the output file as impure
     --prefix-symbols <prefix>     Add <prefix> to start of every symbol name
     --prefix-sections <prefix>    Add <prefix> to start of every section name
     --prefix-alloc-sections <prefix>
                                   Add <prefix> to start of every allocatable
                                     section name
     --file-alignment <num>        Set PE file alignment to <num>
     --heap <reserve>[,<commit>]   Set PE reserve/commit heap to <reserve>/
                                   <commit>
     --image-base <address>        Set PE image base to <address>
     --section-alignment <num>     Set PE section alignment to <num>
     --stack <reserve>[,<commit>]  Set PE reserve/commit stack to <reserve>/
                                   <commit>
     --subsystem <name>[:<version>]
                                   Set PE subsystem to <name> [& <version>]
     --compress-debug-sections[={none|zlib|zlib-gnu|zlib-gabi}]
                                   Compress DWARF debug sections using zlib
     --decompress-debug-sections   Decompress DWARF debug sections using zlib
     
  -v --verbose                     List all object files modified
  
  @<file>                          Read options from <file>
  
  -V --version                     Display this program's version number
  
  -h --help                        Display this output
  
     --info                        List object formats & architectures supported
     
objcopy.exe: 
 supported targets:
 
    elf32-littlearm 
    elf32-bigarm 
    elf32-little 
    elf32-big 
    plugin 
    srec 
    symbolsrec 
    verilog 
    tekhex 
    binary 
    ihex



//===================================

// == objcopy.exe --info

//===================================

BFD header file version (GNU Tools for ARM Embedded Processors) 2.26.0.20160310

elf32-littlearm

 (header little endian, data little endian)
 
  arm
  
elf32-bigarm

 (header big endian, data big endian)
 
  arm
  
elf32-little

 (header little endian, data little endian)
 
  plugin
  
  arm
  
elf32-big

 (header big endian, data big endian)
 
  plugin
  
  arm
  
plugin

 (header little endian, data little endian)
 
srec

 (header endianness unknown, data endianness unknown)
 
  plugin
  
  arm
  
symbolsrec

 (header endianness unknown, data endianness unknown)
 
  plugin
  
  arm
  
verilog

 (header endianness unknown, data endianness unknown)
 
  plugin
  
  arm
  
tekhex

 (header endianness unknown, data endianness unknown)
 
  plugin
  
  arm
  
binary

 (header endianness unknown, data endianness unknown)
 
  plugin
  
  arm
  
ihex

 (header endianness unknown, data endianness unknown)
 
  plugin
  
  arm

               elf32-littlearm elf32-bigarm elf32-little elf32-big plugin srec 
        plugin --------------- ------------ elf32-little elf32-big ------ srec 
           arm elf32-littlearm elf32-bigarm elf32-little elf32-big ------ srec 

               symbolsrec verilog tekhex binary ihex 
        plugin symbolsrec verilog tekhex binary ihex 
           arm symbolsrec verilog tekhex binary ihex 
