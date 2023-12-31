# Sunny camera driver

## Installation

```shell
# git clone https://...
cd sunny_camera
chmod +x *.sh
. build.sh     
sudo ./install.sh
pip install -e .
```
>note: use command (. build.sh) instead of (./build.sh), otherwise you should source ~/.bashrc before next step

# Python API Reference

## `Camera`
- **Attributes**:
  - `WIDTH(str img_type)`: The horizontal width (x-axis) of RGB and depth camera in pixels.
    - The "img_type" can be either "rgb" or "depth," with the default being "rgb" when the parameter is empty. The same principle applies to the following.
  - `HEIGHT(str img_type)`: The vertical height (y-axis) of RGB and depth camera in pixels.
  - `INTRINSIC(str img_type)`: The 3x3 intrinsic parameter matrix of the cameras.
- **Methods**:
  - `init()`: Initialize the backend of the AirBot camera.
    - Returns: `bool` - `True` if initialization is successful, otherwise `False`.
  - `deinit()`: Uninitialize the camera.
    - Returns: `bool` - `True` if deinitialization is successful, otherwise `False`.
  - `get_rgb(str img_type)`: Capture and return the color image.
    - Returns: `np.ndarray` - The captured RGB image.
  - `get_tof(str img_type)`: Capture and return the depth image.
    - Returns: `Dict[str, np.ndarray]` - The captured TOF data.
      - `"depth_image"`: `np.ndarray` - The depth image.
      - `"aligned_rgb"`: `np.ndarray` - The aligned RGB image.
      - `"point_cloud"`: `np.ndarray` - The point cloud data.