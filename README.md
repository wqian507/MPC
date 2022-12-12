# Securing Multi-party Computation in Machine Learning

Create an environment using Anaconda and install the required libraries:
```
conda create --name envname python=3.7
pip install -r requirements.txt
pip install crypten
```

Run the code using `launcher`, `mpc_cifar` trains an adaptation of LeNet on CIFAR in cleartext and encrypts the model and data for inference.

```
python launcher.py --net=LeNet --epochs=20
```

Run the checkpoint for multiprocessors:
```
python launcher.py --world_size=2 --net=LeNet --evaluate --resume --model-location model_best.pth.tar --batch-size 1 --print-freq 1 --skip-plaintext --multiprocess
```

Choose different settings, for details using `python launcher.py --help`
- `--device` cpu/gpu device
- `--project` project name
- `--net` model architecture, options are LeNet and VGG16
- `--epochs` number of total epochs to run
- `--start-epoch` manual epoch number (useful on restarts)
- `--batch-size` mini-batch size (default: 256)
- `--learning-rate` initial learning rate
- `--weight-decay` weight decay (default: 1e-6)
- `--print-freq` print frequency (default: 10)
- `--model-location` path to latest checkpoint (default: none)
- `--resume` resume training from latest checkpoint
- `--evaluate` evaluate model on validation set
- `--seed` seed for initializing training
- `--lr-decay` skip validation for plaintext network
- `--multiprocess` run example in multiprocess mode