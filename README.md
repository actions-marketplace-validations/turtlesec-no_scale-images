# Action to scale images on push

This action will scale all images in the `image-folder` to new images of the same type.

The sizes are hard coded to [250, 500, 1000]

## Inputs

### `image-folder`

**Required** The name images folder.

## Outputs

### `scaled`

0 if no images were found, 1 if all images were already scaled, 2 if some/all images were scaled

## Example usage

uses: actions/scale-images@v1
with:
  image-folder: 'assets'

## Build notes

ncc build index.js
