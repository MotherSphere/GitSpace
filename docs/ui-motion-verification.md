# UI motion verification checklist

This checklist is intended for validating that all menus and interactive elements animate as expected and that motion feels consistent across the UI.

## Motion checklist

Use the **Dev Gallery** tab in debug builds to quickly inspect common UI elements, then validate the full app panels listed below.

### Global checks
- [ ] Hover states animate smoothly (no abrupt jumps or flash frames).
- [ ] Focus states are visible and animated (keyboard and mouse focus).
- [ ] Selected states animate between accent and neutral colors.
- [ ] Menus open/close with fade + slide + scale (no popping).
- [ ] Motion respects the current settings (reduced motion / intensity).
- [ ] Animations stop once complete (no continuous repainting).

### Panels and menus
- [ ] Sidebar navigation items animate on hover/selection.
- [ ] Tab bar buttons animate on hover/selection and drag hover.
- [ ] Tab context menu animates on open.
- [ ] Clone panel:
  - [ ] Combo box icon animates on hover/open.
  - [ ] Clone results menu animates on open.
- [ ] Recent/Open list:
  - [ ] List row hover animations render smoothly.
- [ ] Repo overview:
  - [ ] Summary cards/rows animate on hover.
- [ ] Stage panel:
  - [ ] File list rows animate on hover/selection.
  - [ ] Commit template menu animates on open.
- [ ] History panel:
  - [ ] Branch filter menu animates on open.
- [ ] Branches panel:
  - [ ] Row hover and context menu animations.
- [ ] Auth panel:
  - [ ] Button hover/focus animations.
- [ ] Settings panel:
  - [ ] Theme/release/motion intensity combo menus animate.
- [ ] Notifications:
  - [ ] Toast entry/exit animations and action hover states.

## Dev-only UI gallery

The **Dev Gallery** tab is available in debug builds and lists common elements (menu items, buttons, toggles, sliders, and combo boxes) to verify hover and focus effects quickly.

## Performance considerations

- Keep animations bounded to 60 fps (or lower if reduced motion is active).
- Avoid continuous repaint when an animation has finished.
- Use lightweight, deterministic computations for hover animations (avoid dynamic allocations in hot paths).
- Reuse animation IDs for stable transitions.
- Monitor `PerfScope` measurements when adding new motion effects.

## Accessibility considerations

- Ensure reduced motion settings disable or shorten animations appropriately.
- Maintain sufficient contrast for animated color transitions.
- Preserve keyboard focus indicators during animations.
- Avoid motion that could be distracting (no large, rapid offsets).
- Provide clear state changes even when motion is reduced.
