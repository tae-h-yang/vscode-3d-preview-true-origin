# 3D Viewer Light — True Origin

This is a GPL-3.0 fork of
[`tatsy/vscode-3d-preview`](https://github.com/tatsy/vscode-3d-preview),
created from upstream commit `0e982c4a9b0ee3d7bae04b8221aee32df8021c28`.

## Fork changes

- Axes and grid helpers are located at the actual world origin `(0, 0, 0)`.
- The original extension's bounding-box-based helper translation is removed.
- The world up-axis is selectable as X, Y, or Z.
- Z-up is the default and the world up-axis can be changed for files that use a
  different coordinate convention. PLY does not define a universal up-axis.
- Auto-framing still targets the geometry's bounding-box center; this changes
  only the initial view and never transforms point coordinates or helpers.

The viewer consumes the vertex coordinates already stored in a mesh or point
cloud. It does not assume a camera brand, reconstruct depth, or infer camera
intrinsics. Camera intrinsics are normally used before export to deproject a
depth image into XYZ vertices; standard PLY files do not preserve those
intrinsics or a universal camera/world coordinate convention.

## Local installation

```sh
npm ci
npm run compile
npx @vscode/vsce package
code --install-extension vscode-3d-preview-true-origin-0.1.1.vsix
```

Use **Reopen Editor With...** and select **3D Viewer Light — True Origin**.

## Marketplace publishing

Before publishing, replace the placeholder `tyang-local` publisher in
`package.json` with a publisher ID you own, then follow the
[official publishing guide](https://code.visualstudio.com/api/working-with-extensions/publishing-extension).
Local VSIX installation does not require a Marketplace account.

[![License: GPL3](https://img.shields.io/badge/License-GPL3-green.svg)](https://opensource.org/licenses/gpl-3-0)

## Description

This extension is inspired by [vscode-3dviewer](https://github.com/stef-levesque/vscode-3dviewer) but has minimal features to preview triangular meshes, and point clouds.

## Features

This extension supports 3D formats equally as [Open3D](http://www.open3d.org/docs/0.9.0/tutorial/Basic/file_io.html) (but partly not support currently).

|     | point | mesh |
|:---:|:-----:|:----:|
| obj | o | o |
| off | o | o |
| pcd | o | x |
| ply | o | o |
| stl | x | o |
| xyz | o | x |

### Mesh preview

![mesh](images/mesh_preview.jpg)

### Point cloud preview

![points](images/point_preview.jpg)

### Large color point cloud

![color_points](images/color_points.jpg)

## FAQ

- Q. When I drag and drop a mesh file, a blank display is shown.
  - A. To show a 3D data using this extension, you should first open a workspace including the 3D data that you want to open.

## Reference

- [vscode-3dviewer](https://github.com/stef-levesque/vscode-3dviewer)
- [vscode-pc-viewer](https://github.com/Obarads/vscode-pc-viewer)
- [three.js](https://threejs.org/)

## License

GNU General Public License v3 2021-2025 (c) Tatsuya Yatagawa
