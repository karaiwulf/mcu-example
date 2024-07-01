# Building

Make sure the `thumbv6m-none-eabi` toolchain is installed.  If using rustup, that would look like:

```
rustup target add thumbv6m-none-eabi
```

Then run:

```
cargo build --release
```

This should produce a binary that is 14800 bytes in size (at least on my system).  This binary has been optimized.  For further information on that check the Cargo.toml.  With default release profile options, the binary produced is 54K in size.

# Why

This repository was used as a test for the `unicode_names2` crate.  That did not fit within the required size limitations of the ATSAMD21G18 on the Feather M0, as it is entirely runtime, with lookup tables over 500K, much larger than the 256K available for program memory.  However, the `unicode_names2_macros` crate does all that, entirely at the compile step, negating the need for using additional program memory entirely.
