# SPDX-License-Identifier: (GPL-2.0)
CC := gcc

all: common_params.o common_user_bpf_xdp.o common_libbpf.o bishi.o json.o

CFLAGS := -g -Wall

LIBBPF_DIR = ../libbpf/src/
CFLAGS += -I$(LIBBPF_DIR)/build/usr/include/  -I../headers
# TODO: Do we need to make libbpf from this make file too?

common_params.o: common_params.c common_params.h
	$(CC) $(CFLAGS) -c -o $@ $<

common_user_bpf_xdp.o: common_user_bpf_xdp.c common_user_bpf_xdp.h
	$(CC) $(CFLAGS) -c -o $@ $<

common_libbpf.o: common_libbpf.c common_libbpf.h
	$(CC) $(CFLAGS) -c -o $@ $<
	
bishi.o: bishi.c bishi.h
	$(CC) $(CFLAGS) -lssl -lcrypto -lcurl -c -o $@ $<
	
json.o: json.c json.h
	$(CC) $(CFLAGS) -lm -c -o $@ $<

.PHONY: clean

clean:
	rm -f *.o
