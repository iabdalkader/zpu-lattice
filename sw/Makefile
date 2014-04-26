hello: hello.c crt_io.c
	gcc zpuromgen.c -o zpuromgen
	zpu-elf-gcc -Os -phi `pwd`/hello.c `pwd`/crt_io.c -o hello.elf -Wl,--relax -Wl,--gc-sections -g
	zpu-elf-objcopy -O binary hello.elf hello.bin
	zpu-elf-objdump --disassemble-all >hello.dis hello.elf
	./zpuromgen hello.bin > hello.bram

clean:
	rm -f *.elf *.bin *.dis *.bram *.o zpuromgen
