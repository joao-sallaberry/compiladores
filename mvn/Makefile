MAIN_FILE = ex.mvn
LIBS = libatoi.mvn libconst.mvn libitoa.mvn libpop.mvn libprint.mvn libpush.mvn libscan.mvn libstrlen.mvn libstrrev.mvn libsubtracao.mvn
#OBJ = test.mvn libprint.mvn libconst.mvn
FINAL = final.mvn
LINKED = linked.mvn
SIZE = $(shell tail -1 ex.mvn | cut -c1-4 | tr '[:lower:]' '[:upper:]')
SIZE2 = $(shell echo 'obase=16;ibase=16;$(SIZE) + 2' | bc)

%.mvn: %.asm
	java -cp MLR.jar montador.MvnAsm $<

$(FINAL): $(LINKED)
	java -cp MLR.jar relocator.MvnRelocator $< $@ $(SIZE2) 000

$(LINKED): $(MAIN_FILE) $(LIBS)
	java -cp MLR.jar linker.MvnLinker $^ -s $@

run:
	@java -jar mvn.jar

clean:
	rm -f *.lst *.mvn *.run
