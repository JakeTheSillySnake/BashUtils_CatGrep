SHELL := /bin/bash
FLAGS = -Wall -Wextra -Werror
FILE = cat.c

all: s21_cat tests

s21_cat: clean
	gcc $(FLAGS) cat.c -o s21_cat

tests:
	-diff <(./s21_cat $(FILE)) <(cat $(FILE))
	-diff <(./s21_cat -e $(FILE)) <(cat -e $(FILE))  
	-diff <(./s21_cat -n $(FILE)) <(cat -n $(FILE))  
	-diff <(./s21_cat -t $(FILE)) <(cat -t $(FILE))  
	-diff <(./s21_cat -b $(FILE)) <(cat -b $(FILE))
	-diff <(./s21_cat -s $(FILE)) <(cat -s $(FILE))
	-diff <(./s21_cat --number-nonblank $(FILE)) <(cat -b $(FILE))  
	-diff <(./s21_cat --number $(FILE)) <(cat -n $(FILE))  
	-diff <(./s21_cat --squeeze-blank $(FILE)) <(cat -s $(FILE))
	-diff <(./s21_cat $(FILE) hi.txt) <(cat $(FILE) hi.txt)      

clean:
	rm -rf s21_cat

check:
	cppcheck --enable=all --suppress=missingIncludeSystem *.c
	clang-format -i *.c  