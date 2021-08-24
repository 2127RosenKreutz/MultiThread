CFILES  = client_handler.c connection.c list.c main.c msg_store.c server.c
HFILES  = client_handler.h connection.h fail.h list.h msg_store.h server.h
OFILES  = $(CFILES:.c=.o)
PROGRAM = chat_server

# -----------------------------------------------------------------------------

CFLAGS  = -std=gnu99 -O2 -g -Wall -Wextra -Werror -Wfatal-errors -Wno-unused-parameter
CC      = gcc
LD      = gcc

# explicit -pthread option not needed on MacOS (a.k.a. "Darwin")
# (and results in warnings on some older MacOS versions)
ifneq ($(shell uname),Darwin)
  LDFLAGS += -pthread
endif

# -----------------------------------------------------------------------------

.PHONY: all clean
.INTERMEDIATE: $(OFILES)

all: $(PROGRAM)

clean:
	$(RM) $(OFILES) $(PROGRAM)

$(OFILES): $(HFILES)
#	$(CC) $(CFLAGS) -c -o $@

$(PROGRAM): $(OFILES)
	$(LD) $(OFILES) $(LDFLAGS) -o $@
