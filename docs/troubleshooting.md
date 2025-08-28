---
title: Troubleshooting
---

# Troubleshooting

Here are some common issues and solutions in case you run into problems with getting the blending working.

## Blending is not visible

[//]: # (1. Make sure you went through the installation steps correctly.)

[//]: # (2. Ensure you have an active post process volume with the blend material added.)

[//]: # (   It's a good idea to make it unbound &#40;infinite&#41;.)

[//]: # (3. Double-check your materials have the blend material function hooked up.)

[//]: # (4. Open your editor viewport and enable `Buffer Visualization` > `Material Ambient Occlusion`.)

[//]: # (   If the )

[//]: # (5. Turn off **Static Lighting**.)

[//]: # (6. Ensure `Deferred Rendering` is enabled. `Forward Rendering` is not supported.)

[//]: # (-----)

[//]: # (<input type="checkbox" id="option1" name="options" value="value1">)
[//]: # (<label for="option1">Make sure you went through the installation steps correctly.</label>)

[//]: # (-----)

<div class="ue-checklist" data-checklist-id="ue-autoblend-setup">
  <ul>
    <li>
      <label>
        <input type="checkbox" id="ue-c1">
        Make sure you went through the <a href="/autoblend/#setup">installation</a> steps correctly.
      </label>
    </li>
    <li>
      <label>
        <input type="checkbox" id="ue-c2">
        Ensure you have an active post process volume with the blend material added.<br>
        It's a good idea to make it unbound (infinite).
      </label>
    </li>
    <li>
      <label>
        <input type="checkbox" id="ue-c3">
        Double-check your materials have the blend material function hooked up.
      </label>
    </li>
    <li>
      <label>
        <input type="checkbox" id="ue-c4">
        Open your editor viewport and enable <code>Buffer Visualization</code> &gt; <code>Material Ambient Occlusion</code>.<br>
        If the screen is white it means the AO channel is not being written to, and blending won't work.
        This could be due to static lighting / forward rendering being enabled.
        It could also indicate you haven't set up the material function correctly.
        Make sure you're not viewing <code>Ambient Occlusion</code> since that's a separate unrelated buffer.
      </label>
    </li>
    <li>
      <label>
        <input type="checkbox" id="ue-c5">
        Turn off <strong>Static Lighting</strong>, it is not supported.
      </label>
    </li>
    <li>
      <label>
        <input type="checkbox" id="ue-c6">
        Ensure <code>Deferred Rendering</code> is enabled. <code>Forward Rendering</code> is not supported.
      </label>
    </li>
  </ul>

  <div class="ue-actions">
    <button type="button" class="ue-btn" data-action="check-all">Check all</button>
    <button type="button" class="ue-btn" data-action="reset">Reset</button>
  </div>
</div>

<style>
.ue-checklist ul { list-style: none; padding-left: 0; }
.ue-checklist li { margin: .4rem 0; }
.ue-checklist input[type="checkbox"] { margin-right: .5rem; transform: scale(1.2); }
.ue-actions { margin-top: .75rem; display: flex; gap: .5rem; flex-wrap: wrap; }
.ue-btn { cursor: pointer; border: 1px solid currentColor; background: transparent; padding: .3rem .6rem; border-radius: .4rem; }
</style>

<script>
(function () {
  const NAMESPACE = "ue-checklist";
  const checklists = document.querySelectorAll(".ue-checklist");

  checklists.forEach(root => {
    const id = root.dataset.checklistId || "default";
    const key = (cbId) => `${NAMESPACE}:${location.pathname}:${id}:${cbId}`;
    const boxes = root.querySelectorAll('input[type="checkbox"]');

    // restore saved state
    boxes.forEach(cb => {
      const saved = localStorage.getItem(key(cb.id));
      if (saved !== null) cb.checked = saved === "1";
      cb.addEventListener("change", () => {
        localStorage.setItem(key(cb.id), cb.checked ? "1" : "0");
      });
    });

    // actions
    root.querySelectorAll(".ue-btn").forEach(btn => {
      btn.addEventListener("click", () => {
        const action = btn.dataset.action;
        if (action === "check-all") {
          boxes.forEach(cb => { cb.checked = true; localStorage.setItem(key(cb.id), "1"); });
        } else if (action === "reset") {
          boxes.forEach(cb => { cb.checked = false; localStorage.removeItem(key(cb.id)); });
        }
      });
    });
  });
})();
</script>