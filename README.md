# Cheetah: Lean and Fast Secure Two-Party Deep Neural Network Inference
This repo contains a reproduce for the [Cheetah paper](https://eprint.iacr.org/2022/207).
The codes are just used for the Cybersecurity Frontier.

### Cheetah -> Secure Processing Unit
Most of the Cheetah protocols has been re-written in the [SecretFlow](https://github.com/secretflow) project. Check the code [here](https://github.com/secretflow/spu/tree/main/libspu/mpc/cheetah).

### Requirements

* openssl 
* c++ compiler (>= 8.0 for the better performance on AVX512)
* cmake >= 3.13
* git
* make
* OpenMP (optional, only needed by CryptFlow2 for multi-threading)

### Building Dependencies
* Run `bash scripts/build-deps.sh` which will build the following dependencies
	* [emp-tool](https://github.com/emp-toolkit/emp-tool) We follow the implementation in SCI that using emp-tool for network io and pseudo random generator.
	* [emp-ot](https://github.com/emp-toolkit/emp-ot) We use Ferret in emp-ot as our VOLE-style OT.
	* [Eigen](https://github.com/libigl/eigen) We use Eigen for tensor operations.
	* [SEAL](https://github.com/microsoft/SEAL) We use SEAL's implementation for the BFV homomorphic encryption scheme.
	* [zstd](https://github.com/facebook/zstd) We use zstd for compressing the ciphertext in SEAL which can be replaced by any other compression library.
	* [hexl](https://github.com/intel/hexl/tree/1.2.2) We need hexl's AVX512 acceleration for achieving the reported numbers in our paper.

* The generated objects are placed in the `build/deps/` folder.
* Build has passed on the following setting
  * MacOS 11.6 with clang 13.0.0, Intel Core i5, cmake 3.22.1
  * Red Hat 7.2.0 with gcc 7.2.1, Intel(R) Xeon(R), cmake 3.12.0
  * Ubuntu 18.04 with gcc 7.5.0 Intel(R) Xeon(R),  cmake 3.13
  * Ubuntu 20.04 with gcc 9.4.0 Intel(R) Xeon(R),  cmake 3.16.3
  
### Building Cheetah and SCI-HE Demo

* Run `bash scripts/build.sh` which will build 6 executables in the `build/bin` folder
	* `resnet50-cheetah` 
	* `sqnet-cheetah`
	* `densenet121-cheetah`
	* `resnet50-SCI_HE`
	* `sqnet-SCI_HE`
	* `densenet121-SCI_HE`


