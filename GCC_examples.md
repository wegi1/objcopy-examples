---
# -----------------
# GCC toolchain command line examples of use
# -----------------
---

---
# -----------------
# objcopy.exe examples of use
# -----------------
---

# extract from elf file:

objcopy.exe -O ihex elf_file.elf hexfile.hex

objcopy.exe -O binary elf_file.elf binfile.bin

---

# convert ihex file to binary:

objcopy.exe -I ihex -O binary hexfile.hex binfile.bin

objcopy.exe --input-target=ihex --output-target=binary hexfile.hex binfile.bin

---

# convert from binary file to ihex:

objcopy.exe -I binary -O ihex test.bin test.hex

objcopy.exe --input-target=binary --output-target=ihex test.bin test.hex

---
# -----------------
# objdump.exe examples of use
# -----------------
---

# disassembly bin file as arm code at 0x08000000 and save disassembly to text file

arm-none-eabi-objdump.exe -b binary -marm --adjust-vma=0x08000000 NUCLEO_103_ASM.BIN -Mforce-thumb -D  > deas.txt

---

# dump info data about program in ELF file

arm-none-eabi-objdump.exe program.elf -d --source > deas.txt

---

# disassembly the program included in a the ELF file

arm-none-eabi-objdump -h -S TIMERS_TRY.elf  > "TIMERS_TRY.list"

---
# -----------------
# as.exe examples of use
# -----------------
---

# compile assembler file "functions.s" to object file

arm-none-eabi-as.exe  functions.s -o functions.o 

---
# -----------------
# gcc.exe examples of use
# -----------------
---

# compile C file to object file

arm-none-eabi-gcc.exe  -mcpu=cortex-m3 -g3 -DDEBUG -c main.c -o main.o 

---

# compile C to object file and store ASM output file from conversion C file to assembler

arm-none-eabi-gcc.exe -mcpu=cortex-m3  -DDEBUG  -c main.c -S 

---

# compile main.c file to main.o with the 2nd optimizations level

arm-none-eabi-gcc.exe -O2 -c main.c -o main.o

---

# convert main.c file to ASM file with the 2nd optimizations level

arm-none-eabi-gcc.exe -O2 -c main.c -S

---
# -----------------
# linker ld.exe examples of use
# -----------------
---

# linking 2 obj files into the output elf program file

arm-none-eabi-ld.exe main.o functions.o -o program.elf

---

# use variables at absolute address:

__attribute__ ((section(".rxBuffer"), used))  uint8_t RxBuffer[16];

__attribute__ ((section(".txBuffer"), used))  uint8_t TxBuffer[10];

---
for this is needed add section in ld linker script:

---

//============================

.rxBuf(NOLOAD) :

{

  . = ALIGN(4)
  
  . = ABSOLUTE (0x20000000)
  
  *(.rxBuffer)
  

  . = ABSOLUTE (0x20000010)
  
  *(.txBuffer)
  
} >RAM

//=============================


---
# -----------------
# mixing gcc toolchain examples of use
# -----------------
---

# compile and mixing C with assembler from hand command line:
# ... and show the result in assembler output file ...

---

arm-none-eabi-gcc.exe  -mcpu=cortex-m3 -g3 -DDEBUG -c main.c -o main.o 

arm-none-eabi-as.exe  functions.s -o functions.o 

arm-none-eabi-ld.exe main.o functions.o -o program.elf

---

arm-none-eabi-objdump.exe program.elf -d --source > deas.txt

arm-none-eabi-objdump.exe main.o -d --source > deas2.txt

arm-none-eabi-gcc.exe -mcpu=cortex-m3  -DDEBUG  -c main.c -S 

---
