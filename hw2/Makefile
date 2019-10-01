# All variables/Sources

MEM = mem.txt 
RESULTS = out.txt
SOURCE = DynamicArrays.c TestDarray_hw.c 
PROG = DynamicA


#Compiler and Directives
CC = gcc
CFLAGS  = -Wall -std=c99 -O1 -pedantic -g


# builds a binary from provied c file. 
.PHONY: all
all:	$(PROG)

# Execute DynamicArray.c & TestDarray_hw.c
.PHONY: PROG 
$(PROG):DynamicArrays.c TestDarray_hw.c
	$(CC) $(CFLAGS)  -o DynamicA DynamicArrays.c TestDarray_hw.c


# runs the identified test
.PHONY:	test
test:	$(PROG)
	@echo "Testing TestDarray_hw.c"
	./$(PROG) us-eng-short.txt > $(RESULTS)
	@cat $(RESULTS) 

# runs the standard valgrind memory commands for memory leaks
.PHONY: mem1
mem1:	$(PROG)	
	@echo "Runs the standard valgrind memory command : "
	valgrind --tool=memcheck --leak-check=yes ./$(PROG) us-eng-short.txt &> $(MEM)
	@cat $(MEM)


# All the key makefile targets
.PHONY: help
help: 
	@echo "make options: all, test,mem1, clean, help"


#Removes all temporary and intermediate file
.PHONY: clean
clean: 
	@echo "unwanted file cleanup"
	-rm -f $(PROG)
	-rm -f $(RESULTS)
	-rm -f $(MEM) 
