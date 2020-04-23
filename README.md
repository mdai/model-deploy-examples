# model-deploy

## Examples

Example model deployments for training/testing/inference on MD.ai are located in the `examples/` folder.

## Setup

Python 3.7+ required. Initial setup:

```sh
# Create virtualenv
virtualenv .venv
source .venv/bin/activate

# Install deps
pip install -r requirements.txt
```

## Development

### File Structure
The file structure below needs to be followed for development. MD.ai related files are place in the .mdai folder and the model with its associated files are placed in the model folder.

```sh
$ROOT
  |__ .mdai/
      |__ config.yml            # Contains configuration parameters to be used during bulid
      |__ mdai_deploy.py        # Framework which communicates between server and model
      |__ requirements.txt      # Lists the libraries needed to run the model
  |__ model/
```

### Building the image

To build a production image, we use the `dev/build-image.py` script

```sh
dev/build-image.py --image_name <image_name> --target_folder <path_to_root_folder>
```

To build an image for dev usage,`--hot_reload` arg is used. This auto-refreshes the server which saves significant time in building and running the image again. An example is as follows


```sh
dev/build-image.py --image_name <image_name> --target_folder <path_to_root_folder> --hot-reload
```

### Running the image

In order to run the built image, we use the `dev/run-image.py` script. This runs the most recently built image.

```sh
dev/run-image.py
```

### Testing the image

The output from the container can be tested using the `dev/inference.py` script. This sends images to the deployed model to be tested and recieves results in json

```sh
dev/inference.py <path_to_test_data>
```

### Usage statistics

To profile memory usage of the container, the `dev/profile.py` script can be used.

```sh
dev/profile.py
```

---

&copy; 2020 MD.ai, Inc.
