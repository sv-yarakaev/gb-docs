---
description: 'Разбор опций(getopt, getoptlong)'
---

# Глава 1. Парсинг опций

## Описание

 Функция **getopt\(\)** разбирает аргументы командной строки. Ее аргументы argc и argv являются счетчиком и массивом аргументов, которые передаются функции **main\(\)** при запуске программы. Элемент argv, начинающийся с "-" \(и не являющийся "-" или "--"\), считается опцией. Символы этого элемента \(не считая начального "-"\) являются символами опций. При каждом повторном вызове **getopt\(\)** возвращаются символы следующей опции.

Если **getopt\(\)** находит символ опции, она возвращает этот символ, обновляя внешнюю переменную optind и статическую переменную nextchar, так что следующий вызов **getopt\(\)** может продолжить проверку со следующего символа опции или элемента argv.

```c
#include <unistd.h>

int getopt(int argc, char * const argv[],
           const char *optstring);

extern char *optarg;
extern int optind, opterr, optopt;

#define _GNU_SOURCE


#include <getopt.h>

int getopt_long(int argc, char * const argv[],
           const char *optstring,
           const struct option *longopts, int *longindex);

int getopt_long_only(int argc, char * const argv[],
           const char *optstring,
           const struct option *longopts, int *longindex);

```



