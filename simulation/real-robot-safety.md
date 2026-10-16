---
title: Real Robot Safety
parent: Simulation and Learning
nav_order: 5
permalink: /simulation/real-robot-safety/
---

# Real Robot Safety

<div role="note" aria-label="Caution: real robot testing" style="border: 6px solid #1a1a1a; border-radius: 14px; overflow: hidden; max-width: 640px; margin: 1.5rem 0; background: #ffffff;">
  <div style="background: #ffd400; border-bottom: 6px solid #1a1a1a; padding: 0.6rem 1rem; text-align: center; color: #1a1a1a; font-weight: 800; font-size: 2rem; letter-spacing: 0.08em; line-height: 1.2;">
    <span aria-hidden="true">⚠</span> CAUTION
  </div>
  <div style="padding: 1rem 1.25rem; color: #1a1a1a;">
    <p style="margin: 0 0 0.6rem; font-size: 1.35rem; font-weight: 700;">Real robot testing</p>
    <ul style="margin: 0; padding-left: 1.25rem; font-size: 1.1rem; line-height: 1.6;">
      <li><strong>Never test alone.</strong> Work with your team.</li>
      <li><strong>Keep a hand on the E-stop</strong> at all times.</li>
      <li><strong>Don't trust your simulation.</strong> Expect a sim-to-real gap.</li>
    </ul>
  </div>
</div>

In this course, you will deploy your trained policy on the real robot. Read this page before every hardware test.

{: .warning }
> **Don't trust your simulation result.** A policy that walks perfectly in simulation can behave very differently on the real robot. There is **always a sim-to-real gap**, from actuator differences, friction, delay, sensor noise, and assembly variations. Expect the unexpected.

## Rules for every hardware test

1. **Never test alone.** Always run tests together with your team members in the class.
2. **Keep a hand on the emergency stop.** One person's only job is the **E-stop**, ready to press it at any moment. Press it as soon as anything looks wrong. Don't wait to see what happens.
3. **Keep clear of the robot.** Stay out of the robot's reach, especially its legs, while it is powered.

{: .important }
When in doubt, **press the E-stop.** A stopped test can be restarted; a broken robot or an injury can't be undone.

## Before you deploy

- **Check the E-stop works** before you run a policy: press it and confirm the motors lose power.
- **Start small.** Try the policy on a supported or lifted robot first, with low commands, before letting it walk freely.
- **Check the hardware.** Look for loose bolts, damaged wires, and correct battery levels.
- **Clear the area** around the robot.

See the [Body System]({{ '/hardware/body-system/' | relative_url }}) page for how the emergency stop is wired into the power circuit.
