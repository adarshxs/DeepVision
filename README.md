## Running Inference:
**Minimum requirements to run Inference is an A100 40GB GPU.**

- Clone our fork of the Bunny by BAAI repository here: https://github.com/adarshxs/DeepVision
- Create a conda virtual environment
  ```bash
  conda create -n capx python=3.10
  conda activate capx
  ```
- Install the following
  ```bash
  pip install --upgrade pip  # enable PEP 660 support
  pip install transformers
  pip install torch torchvision xformers --index-url https://download.pytorch.org/whl/cu118

  # Installing APEX
  pip install ninja
  git clone https://github.com/NVIDIA/apex
  cd apex
  pip install -v --disable-pip-version-check --no-cache-dir --no-build-isolation --global-option="--cpp_ext" --global-option="--cuda_ext" ./
  cd ..

  # Installing Flash Attn
  pip install packaging
  pip install flash-attn --no-build-isolation
  
  # Clone the inference Repo
  git clone https://github.com/adarshxs/DeepVision-Deepfake
  cd DeepVision-Deepfake
  pip install -e .
  ```
- Run cli server:
  ```bash
  python -m bunny.serve.cli \
	--model-path adarshxs/DeepVision-Deepfake \
	--model-type llama3.1-8b \
	--image-file /path/to/image \
	--conv-mode llama
  ```


  We thank the amazing team at BAAI, for their Bunny project, upon which this was built.
