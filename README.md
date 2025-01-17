# AI Painter by OneFlow

![image](https://user-images.githubusercontent.com/76760002/208841976-2b7e1e88-5404-4113-a1e3-02a38e727a9c.png)
A browser interface for [OneFlow Diffusers](https://github.com/Oneflow-Inc/diffusers) inspired by [Stable Diffusion Web UI](https://github.com/AUTOMATIC1111/stable-diffusion-webui),the functions of txt2img and img2img are realized


## How to Run

### With Docker

```bash
docker run -it --rm \
  --gpus all --ipc=host -p 7860:7860 --ulimit memlock=-1 --ulimit stack=67108864 \
  -v ${PWD}:/workspace \
  -v ${PWD}/.cache:/root/.cache \
  -w /workspace \
  oneflowinc/ai-painter:cu112 \
  python3 launch.py --ip 0.0.0.0 --port 7860
```

### Without Docker

Install depencies:

```bash
sh setup_env.sh
```

Launch the server:

```bash
python3 launch.py
```
If this fails, try the following two commands to install the latest oneflow
```bash
pip uninstall oneflow
python3 -m pip install -f https://staging.oneflow.info/branch/master/cu112 --pre oneflow
```
Then rerun the script.


### Launch Options

There are other options besides `ip` and `port` mentioned above.

- `--ui-debug-mode`: launch without loading model
- `--graph-mode`: use OneFlow graph mode which will accelerate the inference (but limited by fixed tensor shape)
- `--device`: Target a specific device, eg: `cuda:0` means the first GPU and `cuda:1` means the second GPU


