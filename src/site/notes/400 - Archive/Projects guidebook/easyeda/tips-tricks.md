---
{"dg-publish":true,"dg-path":"easyeda/tips-tricks.md","permalink":"/easyeda/tips-tricks/"}
---

# EasyEDA Tips and Tricks

This section provides practical tips and workflow enhancements for using EasyEDA in schematic design and PCB layout.

## 1. General Workflow Best Practices

*   **Schematic-First Design:** Always initiate designs with a schematic. This serves as the foundational blueprint for PCB layout and simplifies subsequent modifications.
*   **Project Organization:** Utilize new projects to maintain design organization. Projects can be configured as private or public.
*   **Component Library Utilization:** Leverage the extensive component library. Employ search functionality and verify component symbols via preview before placement.
*   **Error Checking:** Employ EasyEDA's integrated error-checking mechanisms to identify common schematic design errors.
*   **Design Rule Check (DRC):** Execute DRC post-routing to identify and rectify violations (e.g., track-to-track, track-to-pad clearances). This ensures manufacturability.
*   **Ground Planes:** Incorporate ground planes on one or more layers to enhance signal integrity, aid heat dissipation, and mitigate electromagnetic interference.
*   **Final Review:** Prior to manufacturing export, meticulously review the PCB layout. Verify component placement, routing, and clearances. Utilize the 3D preview feature for comprehensive inspection.
*   **Gerber File Generation:** EasyEDA offers one-click Gerber file generation. Ensure all necessary layers are selected for export.

## 2. Productivity Enhancements

### 2.1. Keyboard Shortcuts

Mastering keyboard shortcuts significantly accelerates the design process. EasyEDA allows extensive hotkey re-configuration.

*   **Common Shortcuts:**
    *   `Space` + Drag: Panning
    *   `Ctrl` + Mouse Wheel: Zooming
    *   `R`: Rotate components
    *   `Ctrl` + `D`: Duplicate selections
    *   `Shift` + `F`: Open component search box
    *   `B` (or `T`): Change layers (Bottom or Top) during routing, automatically adding a via.
    *   `Right-click` (during routing): Terminate current track while maintaining tool activation.

### 2.2. Settings Adjustment

*   **Snap Size and Grid:** Adjust for precise component placement.
*   **Units:** Verify correct unit settings (e.g., millimeters).

## 3. Schematic Design Tips

*   **Net Ports:** Employ net ports to simplify schematics by abstracting physical connections, particularly in complex circuits.
*   **Component Placement:** Strategically position components on the PCB workspace, considering signal flow, thermal management, and physical constraints.
*   **Annotation and Labeling:** Annotate components with clear reference designators (e.g., R1, C2).

## 4. PCB Layout Tips

*   **Track Widths:** Configure design rule settings for appropriate track widths, clearances, and via sizes.
*   **Routing Angles:** Utilize 45-degree angles for tracks instead of 90-degree angles.
*   **Component Orientation:** Optimize component orientation to minimize crossed traces and simplify routing.
*   **Digital vs. Analog Separation:** Maintain separation between digital and analog circuits to mitigate interference.
*   **Multi-layer Boards:** For complex or high-frequency circuits, consider multi-layer boards for dedicated ground and power planes.
*   **Custom Components:** Create custom components with symbols, footprints, and 3D models if not available in the library.

## 5. Manufacturing and Ordering

*   **JLCPCB Integration:** EasyEDA integrates with JLCPCB for PCB ordering. Gerber files can be generated and components ordered directly.
*   **LCSC Assembled Library:** For JLCPCB assembly services, ensure components are sourced from the 'LCSC Assembled' library for compatibility.

## Resources

*   [EasyEDA Official Documentation](https://docs.easyeda.com/en/Introduction/EasyEDA-Features/index.html)
*   [AnyPCBA - EasyEDA Tips and Tricks](https://www.anypcba.com/blog/easyeda-tips-and-tricks.html)

## Video Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/your_easyeda_tips_tricks_video_id" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
