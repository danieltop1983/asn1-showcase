ASN1SCC="/home/daniel/Downloads/asn1scc/asn1.exe"
OUT="output"
ASN_SRCS=sample.asn
ACN_SRCS=sample.acn
DEP_ASN_SRCS+=$(wildcard $(1)/asn1/*.asn1) 
DEP_ACN_SRCS+=$(wildcard $(1)/asn1/*.acn)

per:
	@echo "Generating source code and runtime libs using uPER"
	$(ASN1SCC) -c $(ASN_SRCS) -uPER -o $(OUT)

acn:
	@echo "Generating source code and runtime libs using ACN"
	$(ASN1SCC) -c $(ASN_SRCS) -ACN $(ACN_SRCS) -atc -o $(OUT)

ada:
	@echo "Generating source code and runtime libs using ACN"
	$(ASN1SCC) -Ada $(ASN_SRCS) -ACN $(ACN_SRCS) -atc -equal -o $(OUT)

lib:
	cd $(OUT); gcc -c -I . *.c
	
allacn: clean acn lib

allper: per lib

all1: allacn allper

all: allacn

clean:
	cd $(OUT); rm -rf *

.PHONY: per acn lib allacn allper all1 all clean
