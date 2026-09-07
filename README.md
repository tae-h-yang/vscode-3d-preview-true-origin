# 3D Viewer Light — True Origin

This is a GPL-3.0 fork of
[`tatsy/vscode-3d-preview`](https://github.com/tatsy/vscode-3d-preview),
created from upstream commit `0e982c4a9b0ee3d7bae04b8221aee32df8021c28`.

## Fork changes

- Axes and grid helpers are located at the actual world origin `(0, 0, 0)`.
- The original extension's bounding-box-based helper translation is removed.
- The world up-axis is selectable as X, Y, or Z.
- Z-up is the default, matching ROS and Orbbec `camera_link` point clouds.
- Auto-framing still targets the geometry's bounding-box center; this changes
  only the initial view and never transforms point coordinates or helpers.

## Local installation

```sh
npm ci
npm run compile
npx vsce package --allow-missing-repository --no-rewrite-relative-links
code --install-extension vscode-3d-preview-true-origin-0.1.0.vsix
```

Use **Reopen Editor With...** and select **3D Viewer Light — True Origin**.

## Marketplace publishing

Before publishing, replace the placeholder `tyang-local` publisher in
`package.json` with a publisher ID you own, update the repository URL, then use
`vsce login <publisher-id>` and `vsce publish`. Publishing requires a Visual
Studio Marketplace publisher and personal access token; local VSIX installation
does not.

[![License: GPL3](https://img.shields.io/badge/License-GPL3-green.svg)](https://opensource.org/licenses/gpl-3-0)
[![Visual Studio Marketplace Version](https://img.shields.io/visual-studio-marketplace/v/tatsy.vscode-3d-preview)](https://marketplace.visualstudio.com/items?itemName=tatsy.vscode-3d-preview)
[![Visual Studio Marketplace Installs](https://img.shields.io/visual-studio-marketplace/r/tatsy.vscode-3d-preview)](https://marketplace.visualstudio.com/items?itemName=tatsy.vscode-3d-preview)
[![Visual Studio Marketplace Installs](https://img.shields.io/visual-studio-marketplace/d/tatsy.vscode-3d-preview)](https://marketplace.visualstudio.com/items?itemName=tatsy.vscode-3d-preview)

**See in VS Marketplace:** [vscode-3d-preview](https://marketplace.visualstudio.com/items?itemName=tatsy.vscode-3d-preview)

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
