include ../tools.mk

all:
	/bin/echo || exit 0 # This test requires /bin/echo to exist
	$(RUSTC) the_backend.rs --crate-name the_backend --crate-type dylib \
		-o $(TMPDIR)/the_backend.dylib
	$(RUSTC) some_crate.rs --crate-name some_crate --crate-type bin -o $(TMPDIR)/some_crate \
		-Z codegen-backend=$(TMPDIR)/the_backend.dylib -Z unstable-options
	grep -x "This has been \"compiled\" succesfully." $(TMPDIR)/some_crate
