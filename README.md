# Scale Images GitHub Action

This action will scale all images in the `image-folder` to new images of the same type.

The sizes are hard coded to [250, 500, 1000]

**Works on**: Linux

## Inputs

### `image-folder`

**Required** The name of the folder that contains the images.

## Outputs

### `scaled`

The result of running the scaler: no images were found (0), all images found were already scaled (1), some/all images found were scaled (2)

## Example usage
~~~~
uses: actions/scale-images@v1
with:
  image-folder: 'assets'
~~~~

## Build notes

ncc build index.js
