
## Deploy to your own github account

Just fork this repo to your own accout. Modify the repo name to `<username>.github.io`, and then you can access it at:

`https://<username>.github.io`

It's quite easy!


## Build your own jupyterlite

1. Install miniconda 3

  ```bash
   mkdir -p ~/miniconda3 && \
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh 2>&1 | \
      awk 'BEGIN{t=0;l=""}systime()-t>1{print $0;t=systime()}/.+/{l=$0}END{print l}' && \
    bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3 && \
    rm ~/miniconda3/miniconda.sh
  ```

2. create xeus-lite-wasm env

   ```bash
   ~/miniconda3/bin/conda env create -f /environment.yml
   ```
   The `environment.yml` is in this repo. You can add your own dependencies in it.

3. build jupyterlite static files:

   ```bash
   source ~/miniconda3/bin/activate xeus-lite-wasm && \
    jupyter lite build --XeusAddon.environment_file=/environment.yml
   ```
   the build target is in `/_output` by default. Just copy the files into your web app directories. Serve it using `nginx`, `caddy`, `node` or `python`, whatever you like.

