![CI](https://github.com/turtlesec-no/scale-images/workflows/CI/badge.svg)

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
Invoking the scaling action
~~~~
    - name: Run scaling step
      id: scale
      uses: turtlesec-no/scale-images@v1.0
      with:
       image-folder: 'test_images'
~~~~
Checking the action output
~~~~
    - name: Check scaling output 0
      if: steps.scale.outputs.scaled == '0'
      run: echo "No images found"

    - name: Check scaling output 1
      if: steps.scale.outputs.scaled == '1'
      run: echo "All images were already scaled"

    - name: Check scaling output 2
      if: steps.scale.outputs.scaled == '2'
      run: echo "Some images were scaled"
~~~~
The images can then be commited in a subsequent step (example)
~~~~
    - name: Commit image files
      working-directory: test_images
      run: | 
        git config user.email "bot@turtlesec.no"
        git config user.name "Turtle Bot (GitHub Action)"
        if [[ "$( git status --porcelain *.jpg)" != "" ]]; then
          git add -A *.jpg
          git commit -m "Updated image files"
          git push
        fi
~~~~

## Build notes

ncc build index.js

## Acknowledgements

Based on the [resize image GitHub Workflow](https://github.com/tech-women/tech-women.github.io/pull/15) by [Markus Tacker](https://github.com/coderbyheart/).
