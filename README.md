# PartCAD Index

This is a registry of all public PartCAD packages.

Add a reference to other public package by creating a pull request.
Add new files or extend the existing ones. Create your own directory if needed.
New files need to be referenced to by existing files.

## Syntax

Each `partcad.yaml` file in this repository follows the below syntax.
The part repositories maintained by the same party/owner are expected
to be placed in the same file.

```yaml
dependencies:
    <package-name>:
        desc: <(optional) textual description>
        type: <git|tar|local>
        path: <(local only) relative-path-within-the-repository>
        url: <(git|tar only) url-of-the-package>
        relPath: <(git|tar only) relative-path-within-the-repository>
        web: <(optional) project or maintainer's url>
        poc: <(optional) maintainer's email>
```

## Example

Here is an example of making a reference to an external git repository:

```yaml
dependencies:
    OpenVMP-custom-parts:
        desc: Custom parts for OpenVMP robots
        type: git
        url: https://github.com/openvmp/openvmp-models.git
        relPath: parts/custom
        web: https://openvmp.com/
        poc: openvmp@proton.me
    OpenVMP-robots:
        desc: OpenVMP robots
        type: git
        url: https://github.com/openvmp/openvmp-models.git
        relPath: robots
        web: https://openvmp.com/
        poc: openvmp@proton.me
```

## Usage

### Use the whole index repository

The top level of this repository is a PartCAD package by itself
(with it's own top level `partcad.yaml`).
It can be referenced in your PartCAD project by adding the below
to your own `partcad.yaml`:

```yaml
dependencies:
    partcad-index:
        type: git
        url: https://github.com/openvmp/partcad.git
        relPath: .
```

### Use a part of the index repository

Multiple `local`-type packages (sub-directories) are used
for ease of maintenance and to enable referencing a subset of packages.
Use it with caution as the directory structure may change
(at this early stage of PartCAD).
Below is an example of using a subset of packages in your project:

```yaml
dependencies:
    partcad-metric:
        type: git
        url: https://github.com/openvmp/partcad.git
        relPath: standard/metric.yaml
    partcad-openvmp:
        type: git
        url: https://github.com/openvmp/partcad.git
        relPath: opensource/openvmp.yaml
```

