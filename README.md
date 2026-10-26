<div align="center">
  <a href="https://prism-pipeline.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://prism-pipeline.com/wp-content/uploads/prism-logos/prism-pipeline-logo-white.png">
      <source media="(prefers-color-scheme: light)" srcset="https://prism-pipeline.com/wp-content/uploads/prism-logos/prism-pipeline-logo.png">
      <img src="https://prism-pipeline.com/wp-content/uploads/prism-logos/prism-pipeline-logo.png" alt="Prism Pipeline" width="420">
    </picture>
  </a>
  <p><strong>Your ComfyUI workflows, connected to your production pipeline.</strong></p>
  <p>
    <a href="https://prism-pipeline.com">Website</a> &middot;
    <a href="https://prism-pipeline.com/docs/latest/plugins/comfyui">Documentation</a> &middot;
    <a href="https://registry.comfy.org/nodes/comfyui-prism-pipeline">ComfyUI Registry</a> &middot;
    <a href="https://github.com/PrismPipeline/ComfyUI-Prism-Pipeline/issues">Report an Issue</a>
  </p>
</div>

# Prism Pipeline for ComfyUI

Bring ComfyUI into a structured VFX and animation pipeline. Manage assets and shots, version workflows, and move images, image sequences, videos, and 3D assets between ComfyUI and your project.

[Prism Pipeline](https://prism-pipeline.com) connects production tools such as Nuke, Blender, Maya, Houdini, and Unreal Engine. This repository provides its ComfyUI custom-node package and browser integration.

## What You Can Do

- **Version workflows.** Save and open ComfyUI workflows as Prism scenefile versions, with comments and project context.
- **Find project media.** Browse assets, shots, and media versions through the Prism Project Browser.
- **Load media into workflows.** Use **Prism Load Media** for images, image sequences, and videos from a direct filepath or Prism media context.
- **Save results to your project.** Use **Prism Save Media** to write generated images and videos to versioned Prism media locations.
- **Exchange assets across tools.** Import project media and supported 3D assets into ComfyUI for use alongside your other DCC applications.

The desktop Prism ComfyUI plugin also supports **App Mode**: run saved workflows from the standalone Prism Project Browser with editable inputs, previews, and generation history, without opening the ComfyUI nodegraph. Submit locally or to Comfy Cloud, or automate submissions with Prism's Execution Graph plugin. See the [plugin documentation](https://prism-pipeline.com/docs/latest/plugins/comfyui) for requirements and setup.

## Installation

### From ComfyUI

1. Install **Prism Pipeline** from the [ComfyUI Registry](https://registry.comfy.org/nodes/comfyui-prism-pipeline) using your custom-node manager.
2. Restart ComfyUI and open the **Prism** sidebar tab.
3. If Prism is not detected, choose **Download Prism** in the configuration dialog, or point the integration to an existing Prism installation.
4. Open the Prism Project Browser and select or create your project.

Automatic setup downloads Prism and its required runtime. Progress appears in the setup dialog, with detailed output in the ComfyUI console. On Linux and macOS, `PRISM_ROOT` can point to an existing installation if it is not detected automatically.

### From Prism Hub

Already using Prism? Install the **ComfyUI** plugin from Prism Hub, then add your ComfyUI installation under **Prism User Settings > DCC apps > ComfyUI > Add**. Restart ComfyUI afterward.

### Manual Installation

From your ComfyUI root directory:

```shell
git clone https://github.com/PrismPipeline/ComfyUI-Prism-Pipeline.git custom_nodes/prism_pipeline
```

Restart ComfyUI, then follow the configuration steps above. Install through either your custom-node manager, Prism Hub, or Git; avoid keeping multiple copies of the same integration in `custom_nodes`.

## Quick Start

### Load Existing Media

Add a **Prism Load Media** node and click **Select Version...** to choose project media. Connect its `images`, `mask`, or `video` output to your workflow as appropriate.

A direct `filepath` takes precedence over the context fields. Clear it and use `version = latest` when you want Prism to resolve the latest project version on execution.

### Save Generated Media

Add a **Prism Save Media** node, connect an `images` or `video` input, and click **Select Entity...** to choose an asset or shot. Set an `identifier` for the output and leave the version empty, or use `next`, for automatic versioning.

### Version Your Workflow

Use **Save Version** or **Save with Comment** in the Prism sidebar. Open the Project Browser to find and reopen saved workflow versions.

## Requirements and Connection

- A running ComfyUI installation and a graphical desktop session for Prism's UI.
- Windows, Linux, or macOS. Linux may require additional system Qt/XCB libraries.
- Browser actions and Prism media-context lookups communicate with the desktop Prism ComfyUI context through `ws://localhost:8765`. Keep that port available.
- App Mode needs a running ComfyUI server for local execution, but not an open browser nodegraph. Cloud execution requires a Comfy API key and a compatible workflow.

For platform-specific configuration, environment variables, App Mode preparation, cloud execution, and troubleshooting, read the [ComfyUI plugin documentation](https://prism-pipeline.com/docs/latest/plugins/comfyui).

## Help and Feedback

Visit [prism-pipeline.com](https://prism-pipeline.com) to learn more about Prism and its integrations. For problems with this package, [open an issue](https://github.com/PrismPipeline/ComfyUI-Prism-Pipeline/issues) with your OS, ComfyUI version, reproduction steps, and relevant console output. Remove API keys and other sensitive information before posting logs.

## License

This package is licensed under [LGPL-3.0-or-later](license-LGPL.txt).