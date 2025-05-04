# Following svpino's repository, setup Mac Mini M4 for Pytorch, Tensorflow and JAX
I just bought a Mac Mini M4 and I wanted to verify my Python setup for runing my AI work on the M4 chip.  I found [svpino's](https://github.com/svpino) repository [apple-silicon](https://github.com/svpino/apple-silicon).  First I watched the [youtube video](https://www.youtube.com/watch?v=cGEIEnekmRM&t=325s) then I decided to try this myself. 

# initial installations
## Clone svpino's repository, Setup conda for python-3.8
```
(base) jkozik@Jacks-Mac-mini projects % https://github.com/svpino/apple-silicon.git
zsh: no such file or directory: https://github.com/svpino/apple-silicon.git
(base) jkozik@Jacks-Mac-mini projects % git clone https://github.com/svpino/apple-silicon.git
Cloning into 'apple-silicon'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 15 (delta 6), reused 12 (delta 4), pack-reused 0 (from 0)
Receiving objects: 100% (15/15), 4.48 KiB | 4.48 MiB/s, done.
Resolving deltas: 100% (6/6), done.
(base) jkozik@Jacks-Mac-mini projects % cd apple-silicon
(base) jkozik@Jacks-Mac-mini apple-silicon % conda create --prefix ./env python=3.8
Retrieving notices: done
Channels:
 - conda-forge
Platform: osx-arm64
Collecting package metadata (repodata.json): done
Solving environment: done

## Package Plan ##

  environment location: /Users/jkozik/projects/apple-silicon/env

  added / updated specs:
    - python=3.8


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    openssl-3.5.0              |       h81ee809_1         2.9 MB  conda-forge
    ------------------------------------------------------------
                                           Total:         2.9 MB

The following NEW packages will be INSTALLED:

  bzip2              conda-forge/osx-arm64::bzip2-1.0.8-h99b78c6_7
  ca-certificates    conda-forge/noarch::ca-certificates-2025.4.26-hbd8a1cb_0
  libffi             conda-forge/osx-arm64::libffi-3.4.6-h1da3d7d_1
  liblzma            conda-forge/osx-arm64::liblzma-5.8.1-h39f12f2_0
  liblzma-devel      conda-forge/osx-arm64::liblzma-devel-5.8.1-h39f12f2_0
  libsqlite          conda-forge/osx-arm64::libsqlite-3.49.1-h3f77e49_2
  libzlib            conda-forge/osx-arm64::libzlib-1.3.1-h8359307_2
  ncurses            conda-forge/osx-arm64::ncurses-6.5-h5e97a16_3
  openssl            conda-forge/osx-arm64::openssl-3.5.0-h81ee809_1
  pip                conda-forge/noarch::pip-24.3.1-pyh8b19718_0
  python             conda-forge/osx-arm64::python-3.8.20-h7d35d02_2_cpython
  readline           conda-forge/osx-arm64::readline-8.2-h1d1bf99_2
  setuptools         conda-forge/noarch::setuptools-75.3.0-pyhd8ed1ab_0
  tk                 conda-forge/osx-arm64::tk-8.6.13-h5083fa2_1
  wheel              conda-forge/noarch::wheel-0.45.1-pyhd8ed1ab_0
  xz                 conda-forge/osx-arm64::xz-5.8.1-h9a6d368_0
  xz-gpl-tools       conda-forge/osx-arm64::xz-gpl-tools-5.8.1-h9a6d368_0
  xz-tools           conda-forge/osx-arm64::xz-tools-5.8.1-h39f12f2_0


Proceed ([y]/n)? y


Downloading and Extracting Packages:

Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate /Users/jkozik/projects/apple-silicon/env
#
# To deactivate an active environment, use
#
#     $ conda deactivate

(base) jkozik@Jacks-Mac-mini apple-silicon % conda activate /Users/jkozik/projects/apple-silicon/env
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon %
```
## Install Torch
```
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon % pip install torch torchvision torchaudio
Collecting torch
  Using cached torch-2.4.1-cp38-none-macosx_11_0_arm64.whl.metadata (26 kB)
Collecting torchvision
  Using cached torchvision-0.19.1-cp38-cp38-macosx_11_0_arm64.whl.metadata (6.0 kB)
Collecting torchaudio
  Using cached torchaudio-2.4.1-cp38-cp38-macosx_11_0_arm64.whl.metadata (6.4 kB)
Collecting filelock (from torch)
  Using cached filelock-3.16.1-py3-none-any.whl.metadata (2.9 kB)
Collecting typing-extensions>=4.8.0 (from torch)
  Using cached typing_extensions-4.13.2-py3-none-any.whl.metadata (3.0 kB)
Collecting sympy (from torch)
  Using cached sympy-1.13.3-py3-none-any.whl.metadata (12 kB)
Collecting networkx (from torch)
  Using cached networkx-3.1-py3-none-any.whl.metadata (5.3 kB)
Collecting jinja2 (from torch)
  Using cached jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Collecting fsspec (from torch)
  Using cached fsspec-2025.3.0-py3-none-any.whl.metadata (11 kB)
Collecting numpy (from torchvision)
  Using cached numpy-1.24.4-cp38-cp38-macosx_11_0_arm64.whl.metadata (5.6 kB)
Collecting pillow!=8.3.*,>=5.3.0 (from torchvision)
  Using cached pillow-10.4.0-cp38-cp38-macosx_11_0_arm64.whl.metadata (9.2 kB)
Collecting MarkupSafe>=2.0 (from jinja2->torch)
  Using cached MarkupSafe-2.1.5-cp38-cp38-macosx_10_9_universal2.whl.metadata (3.0 kB)
Collecting mpmath<1.4,>=1.1.0 (from sympy->torch)
  Using cached mpmath-1.3.0-py3-none-any.whl.metadata (8.6 kB)
Using cached torch-2.4.1-cp38-none-macosx_11_0_arm64.whl (62.1 MB)
Using cached torchvision-0.19.1-cp38-cp38-macosx_11_0_arm64.whl (1.7 MB)
Using cached torchaudio-2.4.1-cp38-cp38-macosx_11_0_arm64.whl (1.8 MB)
Using cached pillow-10.4.0-cp38-cp38-macosx_11_0_arm64.whl (3.4 MB)
Using cached typing_extensions-4.13.2-py3-none-any.whl (45 kB)
Using cached filelock-3.16.1-py3-none-any.whl (16 kB)
Using cached fsspec-2025.3.0-py3-none-any.whl (193 kB)
Using cached jinja2-3.1.6-py3-none-any.whl (134 kB)
Using cached networkx-3.1-py3-none-any.whl (2.1 MB)
Using cached numpy-1.24.4-cp38-cp38-macosx_11_0_arm64.whl (13.8 MB)
Using cached sympy-1.13.3-py3-none-any.whl (6.2 MB)
Using cached MarkupSafe-2.1.5-cp38-cp38-macosx_10_9_universal2.whl (18 kB)
Using cached mpmath-1.3.0-py3-none-any.whl (536 kB)
Installing collected packages: mpmath, typing-extensions, sympy, pillow, numpy, networkx, MarkupSafe, fsspec, filelock, jinja2, torch, torchvision, torchaudio
Successfully installed MarkupSafe-2.1.5 filelock-3.16.1 fsspec-2025.3.0 jinja2-3.1.6 mpmath-1.3.0 networkx-3.1 numpy-1.24.4 pillow-10.4.0 sympy-1.13.3 torch-2.4.1 torchaudio-2.4.1 torchvision-0.19.1 typing-extensions-4.13.2
```
## Install Tensorflow
```
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon %  pip install tensorflow tensorflow-macos tensorflow-metal
Collecting tensorflow
  Downloading tensorflow-2.13.1-cp38-cp38-macosx_12_0_arm64.whl.metadata (2.6 kB)
Collecting tensorflow-macos
  Downloading tensorflow_macos-2.13.0-cp38-cp38-macosx_12_0_arm64.whl.metadata (3.2 kB)
Collecting tensorflow-metal
  Downloading tensorflow_metal-1.0.1-cp38-cp38-macosx_12_0_arm64.whl.metadata (1.2 kB)
INFO: pip is looking at multiple versions of tensorflow to determine which version is compatible with other requirements. This could take a while.
Collecting tensorflow
  Downloading tensorflow-2.13.0-cp38-cp38-macosx_12_0_arm64.whl.metadata (2.6 kB)
Collecting absl-py>=1.0.0 (from tensorflow-macos)
  Downloading absl_py-2.2.2-py3-none-any.whl.metadata (2.6 kB)
Collecting astunparse>=1.6.0 (from tensorflow-macos)
  Downloading astunparse-1.6.3-py2.py3-none-any.whl.metadata (4.4 kB)
Collecting flatbuffers>=23.1.21 (from tensorflow-macos)
  Downloading flatbuffers-25.2.10-py2.py3-none-any.whl.metadata (875 bytes)
Collecting gast<=0.4.0,>=0.2.1 (from tensorflow-macos)
  Downloading gast-0.4.0-py3-none-any.whl.metadata (1.1 kB)
Collecting google-pasta>=0.1.1 (from tensorflow-macos)
  Downloading google_pasta-0.2.0-py3-none-any.whl.metadata (814 bytes)
Collecting h5py>=2.9.0 (from tensorflow-macos)
  Downloading h5py-3.11.0-cp38-cp38-macosx_11_0_arm64.whl.metadata (2.5 kB)
Collecting libclang>=13.0.0 (from tensorflow-macos)
  Downloading libclang-18.1.1-1-py2.py3-none-macosx_11_0_arm64.whl.metadata (5.2 kB)
Collecting numpy<=1.24.3,>=1.22 (from tensorflow-macos)
  Downloading numpy-1.24.3-cp38-cp38-macosx_11_0_arm64.whl.metadata (5.6 kB)
Collecting opt-einsum>=2.3.2 (from tensorflow-macos)
  Downloading opt_einsum-3.4.0-py3-none-any.whl.metadata (6.3 kB)
Collecting packaging (from tensorflow-macos)
  Downloading packaging-25.0-py3-none-any.whl.metadata (3.3 kB)
Collecting protobuf!=4.21.0,!=4.21.1,!=4.21.2,!=4.21.3,!=4.21.4,!=4.21.5,<5.0.0dev,>=3.20.3 (from tensorflow-macos)
  Downloading protobuf-4.25.7-cp37-abi3-macosx_10_9_universal2.whl.metadata (541 bytes)
Requirement already satisfied: setuptools in ./env/lib/python3.8/site-packages (from tensorflow-macos) (75.3.0)
Collecting six>=1.12.0 (from tensorflow-macos)
  Downloading six-1.17.0-py2.py3-none-any.whl.metadata (1.7 kB)
Collecting termcolor>=1.1.0 (from tensorflow-macos)
  Downloading termcolor-2.4.0-py3-none-any.whl.metadata (6.1 kB)
Collecting typing-extensions<4.6.0,>=3.6.6 (from tensorflow-macos)
  Downloading typing_extensions-4.5.0-py3-none-any.whl.metadata (8.5 kB)
Collecting wrapt>=1.11.0 (from tensorflow-macos)
  Downloading wrapt-1.17.2-cp38-cp38-macosx_11_0_arm64.whl.metadata (6.4 kB)
Collecting grpcio<2.0,>=1.24.3 (from tensorflow-macos)
  Downloading grpcio-1.70.0-cp38-cp38-macosx_10_14_universal2.whl.metadata (3.9 kB)
Collecting tensorboard<2.14,>=2.13 (from tensorflow-macos)
  Downloading tensorboard-2.13.0-py3-none-any.whl.metadata (1.8 kB)
Collecting tensorflow-estimator<2.14,>=2.13.0 (from tensorflow-macos)
  Downloading tensorflow_estimator-2.13.0-py2.py3-none-any.whl.metadata (1.3 kB)
Collecting keras<2.14,>=2.13.1 (from tensorflow-macos)
  Downloading keras-2.13.1-py3-none-any.whl.metadata (2.4 kB)
Requirement already satisfied: wheel~=0.35 in ./env/lib/python3.8/site-packages (from tensorflow-metal) (0.45.1)
Collecting google-auth<3,>=1.6.3 (from tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading google_auth-2.39.0-py2.py3-none-any.whl.metadata (6.2 kB)
Collecting google-auth-oauthlib<1.1,>=0.5 (from tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading google_auth_oauthlib-1.0.0-py2.py3-none-any.whl.metadata (2.7 kB)
Collecting markdown>=2.6.8 (from tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading Markdown-3.7-py3-none-any.whl.metadata (7.0 kB)
Collecting requests<3,>=2.21.0 (from tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading requests-2.32.3-py3-none-any.whl.metadata (4.6 kB)
Collecting tensorboard-data-server<0.8.0,>=0.7.0 (from tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading tensorboard_data_server-0.7.2-py3-none-any.whl.metadata (1.1 kB)
Collecting werkzeug>=1.0.1 (from tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading werkzeug-3.0.6-py3-none-any.whl.metadata (3.7 kB)
Collecting cachetools<6.0,>=2.0.0 (from google-auth<3,>=1.6.3->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading cachetools-5.5.2-py3-none-any.whl.metadata (5.4 kB)
Collecting pyasn1-modules>=0.2.1 (from google-auth<3,>=1.6.3->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading pyasn1_modules-0.4.2-py3-none-any.whl.metadata (3.5 kB)
Collecting rsa<5,>=3.1.4 (from google-auth<3,>=1.6.3->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading rsa-4.9.1-py3-none-any.whl.metadata (5.6 kB)
Collecting requests-oauthlib>=0.7.0 (from google-auth-oauthlib<1.1,>=0.5->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading requests_oauthlib-2.0.0-py2.py3-none-any.whl.metadata (11 kB)
Collecting importlib-metadata>=4.4 (from markdown>=2.6.8->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading importlib_metadata-8.5.0-py3-none-any.whl.metadata (4.8 kB)
Collecting charset-normalizer<4,>=2 (from requests<3,>=2.21.0->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading charset_normalizer-3.4.2-cp38-cp38-macosx_10_9_universal2.whl.metadata (35 kB)
Collecting idna<4,>=2.5 (from requests<3,>=2.21.0->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading idna-3.10-py3-none-any.whl.metadata (10 kB)
Collecting urllib3<3,>=1.21.1 (from requests<3,>=2.21.0->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading urllib3-2.2.3-py3-none-any.whl.metadata (6.5 kB)
Collecting certifi>=2017.4.17 (from requests<3,>=2.21.0->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading certifi-2025.4.26-py3-none-any.whl.metadata (2.5 kB)
Requirement already satisfied: MarkupSafe>=2.1.1 in ./env/lib/python3.8/site-packages (from werkzeug>=1.0.1->tensorboard<2.14,>=2.13->tensorflow-macos) (2.1.5)
Collecting zipp>=3.20 (from importlib-metadata>=4.4->markdown>=2.6.8->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading zipp-3.20.2-py3-none-any.whl.metadata (3.7 kB)
Collecting pyasn1<0.7.0,>=0.6.1 (from pyasn1-modules>=0.2.1->google-auth<3,>=1.6.3->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading pyasn1-0.6.1-py3-none-any.whl.metadata (8.4 kB)
Collecting oauthlib>=3.0.0 (from requests-oauthlib>=0.7.0->google-auth-oauthlib<1.1,>=0.5->tensorboard<2.14,>=2.13->tensorflow-macos)
  Downloading oauthlib-3.2.2-py3-none-any.whl.metadata (7.5 kB)
Downloading tensorflow-2.13.0-cp38-cp38-macosx_12_0_arm64.whl (1.9 kB)
Downloading tensorflow_macos-2.13.0-cp38-cp38-macosx_12_0_arm64.whl (189.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 189.3/189.3 MB 21.4 MB/s eta 0:00:00
Downloading tensorflow_metal-1.0.1-cp38-cp38-macosx_12_0_arm64.whl (1.4 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.4/1.4 MB 13.6 MB/s eta 0:00:00
Downloading absl_py-2.2.2-py3-none-any.whl (135 kB)
Downloading astunparse-1.6.3-py2.py3-none-any.whl (12 kB)
Downloading flatbuffers-25.2.10-py2.py3-none-any.whl (30 kB)
Downloading gast-0.4.0-py3-none-any.whl (9.8 kB)
Downloading google_pasta-0.2.0-py3-none-any.whl (57 kB)
Downloading grpcio-1.70.0-cp38-cp38-macosx_10_14_universal2.whl (11.4 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 11.4/11.4 MB 21.4 MB/s eta 0:00:00
Downloading h5py-3.11.0-cp38-cp38-macosx_11_0_arm64.whl (2.9 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.9/2.9 MB 18.1 MB/s eta 0:00:00
Downloading keras-2.13.1-py3-none-any.whl (1.7 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.7/1.7 MB 19.7 MB/s eta 0:00:00
Downloading libclang-18.1.1-1-py2.py3-none-macosx_11_0_arm64.whl (25.8 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 25.8/25.8 MB 21.7 MB/s eta 0:00:00
Downloading numpy-1.24.3-cp38-cp38-macosx_11_0_arm64.whl (13.8 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 13.8/13.8 MB 21.1 MB/s eta 0:00:00
Downloading opt_einsum-3.4.0-py3-none-any.whl (71 kB)
Downloading protobuf-4.25.7-cp37-abi3-macosx_10_9_universal2.whl (394 kB)
Downloading six-1.17.0-py2.py3-none-any.whl (11 kB)
Downloading tensorboard-2.13.0-py3-none-any.whl (5.6 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 5.6/5.6 MB 21.5 MB/s eta 0:00:00
Downloading tensorflow_estimator-2.13.0-py2.py3-none-any.whl (440 kB)
Downloading termcolor-2.4.0-py3-none-any.whl (7.7 kB)
Downloading typing_extensions-4.5.0-py3-none-any.whl (27 kB)
Downloading wrapt-1.17.2-cp38-cp38-macosx_11_0_arm64.whl (38 kB)
Downloading packaging-25.0-py3-none-any.whl (66 kB)
Downloading google_auth-2.39.0-py2.py3-none-any.whl (212 kB)
Downloading google_auth_oauthlib-1.0.0-py2.py3-none-any.whl (18 kB)
Downloading Markdown-3.7-py3-none-any.whl (106 kB)
Downloading requests-2.32.3-py3-none-any.whl (64 kB)
Downloading tensorboard_data_server-0.7.2-py3-none-any.whl (2.4 kB)
Downloading werkzeug-3.0.6-py3-none-any.whl (227 kB)
Downloading cachetools-5.5.2-py3-none-any.whl (10 kB)
Downloading certifi-2025.4.26-py3-none-any.whl (159 kB)
Downloading charset_normalizer-3.4.2-cp38-cp38-macosx_10_9_universal2.whl (198 kB)
Downloading idna-3.10-py3-none-any.whl (70 kB)
Downloading importlib_metadata-8.5.0-py3-none-any.whl (26 kB)
Downloading pyasn1_modules-0.4.2-py3-none-any.whl (181 kB)
Downloading requests_oauthlib-2.0.0-py2.py3-none-any.whl (24 kB)
Downloading rsa-4.9.1-py3-none-any.whl (34 kB)
Downloading urllib3-2.2.3-py3-none-any.whl (126 kB)
Downloading oauthlib-3.2.2-py3-none-any.whl (151 kB)
Downloading pyasn1-0.6.1-py3-none-any.whl (83 kB)
Downloading zipp-3.20.2-py3-none-any.whl (9.2 kB)
Installing collected packages: libclang, flatbuffers, zipp, wrapt, werkzeug, urllib3, typing-extensions, termcolor, tensorflow-estimator, tensorboard-data-server, six, pyasn1, protobuf, packaging, opt-einsum, oauthlib, numpy, keras, idna, grpcio, gast, charset-normalizer, certifi, cachetools, absl-py, tensorflow-metal, rsa, requests, pyasn1-modules, importlib-metadata, h5py, google-pasta, astunparse, requests-oauthlib, markdown, google-auth, google-auth-oauthlib, tensorboard, tensorflow-macos, tensorflow
  Attempting uninstall: typing-extensions
    Found existing installation: typing_extensions 4.13.2
    Uninstalling typing_extensions-4.13.2:
      Successfully uninstalled typing_extensions-4.13.2
  Attempting uninstall: numpy
    Found existing installation: numpy 1.24.4
    Uninstalling numpy-1.24.4:
      Successfully uninstalled numpy-1.24.4
ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
torch 2.4.1 requires typing-extensions>=4.8.0, but you have typing-extensions 4.5.0 which is incompatible.
Successfully installed absl-py-2.2.2 astunparse-1.6.3 cachetools-5.5.2 certifi-2025.4.26 charset-normalizer-3.4.2 flatbuffers-25.2.10 gast-0.4.0 google-auth-2.39.0 google-auth-oauthlib-1.0.0 google-pasta-0.2.0 grpcio-1.70.0 h5py-3.11.0 idna-3.10 importlib-metadata-8.5.0 keras-2.13.1 libclang-18.1.1 markdown-3.7 numpy-1.24.3 oauthlib-3.2.2 opt-einsum-3.4.0 packaging-25.0 protobuf-4.25.7 pyasn1-0.6.1 pyasn1-modules-0.4.2 requests-2.32.3 requests-oauthlib-2.0.0 rsa-4.9.1 six-1.17.0 tensorboard-2.13.0 tensorboard-data-server-0.7.2 tensorflow-2.13.0 tensorflow-estimator-2.13.0 tensorflow-macos-2.13.0 tensorflow-metal-1.0.1 termcolor-2.4.0 typing-extensions-4.5.0 urllib3-2.2.3 werkzeug-3.0.6 wrapt-1.17.2 zipp-3.20.2
```
## Install JAX
```
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon %  pip install jax-metal ml_dtypes==0.2.0
Collecting jax-metal
  Using cached jax_metal-0.1.1-py3-none-macosx_13_0_arm64.whl.metadata (2.7 kB)
Collecting ml_dtypes==0.2.0
  Using cached ml_dtypes-0.2.0-cp38-cp38-macosx_10_9_universal2.whl.metadata (20 kB)
Requirement already satisfied: numpy>1.20 in ./env/lib/python3.8/site-packages (from ml_dtypes==0.2.0) (1.24.3)
Requirement already satisfied: wheel~=0.35 in ./env/lib/python3.8/site-packages (from jax-metal) (0.45.1)
Requirement already satisfied: six>=1.15.0 in ./env/lib/python3.8/site-packages (from jax-metal) (1.17.0)
INFO: pip is looking at multiple versions of jax-metal to determine which version is compatible with other requirements. This could take a while.
Collecting jax-metal
  Downloading jax_metal-0.1.0-py3-none-macosx_11_0_arm64.whl.metadata (2.5 kB)
  Downloading jax_metal-0.0.7-py3-none-macosx_13_0_arm64.whl.metadata (2.1 kB)
  Downloading jax_metal-0.0.6-py3-none-macosx_13_0_arm64.whl.metadata (2.0 kB)
  Downloading jax_metal-0.0.5-py3-none-macosx_11_0_arm64.whl.metadata (1.4 kB)
  Downloading jax_metal-0.0.4-py3-none-macosx_11_0_arm64.whl.metadata (1.1 kB)
Collecting jax==0.4.11 (from jax-metal)
  Downloading jax-0.4.11.tar.gz (1.3 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.3/1.3 MB 15.0 MB/s eta 0:00:00
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Collecting jaxlib==0.4.11 (from jax-metal)
  Downloading jaxlib-0.4.11-cp38-cp38-macosx_11_0_arm64.whl.metadata (2.1 kB)
Requirement already satisfied: opt-einsum in ./env/lib/python3.8/site-packages (from jax==0.4.11->jax-metal) (3.4.0)
Collecting scipy>=1.7 (from jax==0.4.11->jax-metal)
  Downloading scipy-1.10.1-cp38-cp38-macosx_12_0_arm64.whl.metadata (53 kB)
Requirement already satisfied: importlib-metadata>=4.6 in ./env/lib/python3.8/site-packages (from jax==0.4.11->jax-metal) (8.5.0)
Requirement already satisfied: zipp>=3.20 in ./env/lib/python3.8/site-packages (from importlib-metadata>=4.6->jax==0.4.11->jax-metal) (3.20.2)
Downloading ml_dtypes-0.2.0-cp38-cp38-macosx_10_9_universal2.whl (1.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.2/1.2 MB 13.4 MB/s eta 0:00:00
Downloading jax_metal-0.0.4-py3-none-macosx_11_0_arm64.whl (38.7 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 38.7/38.7 MB 16.8 MB/s eta 0:00:00
Downloading jaxlib-0.4.11-cp38-cp38-macosx_11_0_arm64.whl (60.4 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 60.4/60.4 MB 9.8 MB/s eta 0:00:00
Downloading scipy-1.10.1-cp38-cp38-macosx_12_0_arm64.whl (28.8 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 28.8/28.8 MB 21.1 MB/s eta 0:00:00
Building wheels for collected packages: jax
  Building wheel for jax (pyproject.toml) ... done
  Created wheel for jax: filename=jax-0.4.11-py3-none-any.whl size=1487873 sha256=3e4f97d3707937b9d5bce6f750993fc2e6dd54cd272e8bc81df631ed8cb787bc
  Stored in directory: /Users/jkozik/Library/Caches/pip/wheels/65/e8/48/e882a3b1894ac6faa056112773675b7fee52390b219207334f
Successfully built jax
Installing collected packages: scipy, ml_dtypes, jaxlib, jax, jax-metal
Successfully installed jax-0.4.11 jax-metal-0.0.4 jaxlib-0.4.11 ml_dtypes-0.2.0 scipy-1.10.1
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon %
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon %
(/Users/jkozik/projects/apple-silicon/env) jkozik@Jacks-Mac-mini apple-silicon %   
```
# Run test.ipynb
svpino setup a test file that creates two large matrices and multipies them together with and without GPU for each of the packages Pytorch, TensorFlow and JAX.  Please look at the saved notebook to see the output.  

This repository helped me verify that my basic python setup for data science was correctly setup for my Mac Mini's M4 Silicon.  Thank you !


# References
 - [How to run PyTorch, TensorFlow, and JAX on your Mac](https://www.youtube.com/watch?v=cGEIEnekmRM&t=325s) by [Underfitted](https://www.youtube.com/@underfitted)
 - [apple-silicon](https://github.com/svpino/apple-silicon) by [svpino](https://github.com/svpino)
