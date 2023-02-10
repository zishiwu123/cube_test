### Goal
App that allows you to test yourself on cube net problems for spatial reasoning.
For example, see https://www.intelligencetest.com/questions/visualization/difficult/1/8.html?cmtx_perm=23

### How to Install and Run
1. Install VS Code: https://code.visualstudio.com/download
2. Open VS Code and install Live Server extension: https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer
3. Open this folder with VS Code and press "Go Live" button to run live server
4. Browser should launch and go to URL http://127.0.0.1:5500/, which renders a cube with 6 letters for its faces

### TODO
1. Instead of a single cube that continously rotates, we want 3 static cubes that are
    pre-rotated in different isometric views
2. Calculate answer for 2d cross-shaped cube net and have a button that shows the user the answer.
    This should be a div showing a scros made of 6 squares which are initially blank.
    Then when user clicks button, each square on the cross is populated with its corresponding letter.
2. Deploy as static site, one option is Github pages: https://pages.github.com/ 

### Cube 2D image texture atlas requirements
1. Image needs to have aspect ratio of width / height = 2.
2. To generate this image manually, I made a free account on Canva https://www.canva.com/ and
    uploaded 6 square images of letters which can be found in letters/ folder.
    Then shrank each image to 200x200 pixels and arranged them so the 6 letters filled the
    first 3 columns of a 800x400 image and the rightmost column was empty whitespace.
    See textures/6_letters_v1.png for example.
3. TODO: figure out how to generate 2D image of texture atlas using automated programming tools.

### How to calculate cube net answer
1. Need to find mapping of letter positions between the following:
    * textures/6_letters_v1.png
    * 2D cube net shaped like a cross

2. For example, suppose textures/6_letters_v1.png looked like this and have indices (right side ascii art)

    ****************    ****************
    * F * E * C *  *    * 0 * 1 * 2 *  *
    ****************    ****************
    * D * B * A *  *    * 3 * 4 * 5 *  *
    ****************    ****************

    Then 2d cube net (with F being the top of the cube) will look like this and have indices (right side ascii art)

        *****           *****
        * A *           * 0 *
    *************   *************
    * C * F * D *   * 1 * 2 * 3 *
    *************   *************
        * B *           * 4 *
        *****           *****
        * E *           * 5 *
        *****           *****

    Then the mapping of indices from texture atlas image to 2d cube net would be:
    - 0 -> 2 (F)
    - 1 -> 5 (E)
    - 2 -> 1 (C)
    - 3 -> 3 (D)
    - 4 -> 4 (B)
    - 5 -> 0 (A)

### Acknowledgements
- Got code to render cube with textures in WebGL from tutorial: https://webglfundamentals.org/webgl/lessons/webgl-3d-textures.html
