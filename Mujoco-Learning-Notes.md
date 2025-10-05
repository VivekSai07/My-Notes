## 1️⃣ P-Controller (Proportional Controller)
- **Idea**: APply a force/torque proportional to the errot (difference between desired and actual state).

```math
u(t) = K_p \times e(t)
```
- $e(t) = x_{desired} - x(t)$ [The eror].
- $K_p$ = proportional gain (scales the correction).
- $u(t)$ = control input (force/torque/velocity command).

✅ **Pros**: Simple, effective.
❌ **Cons**: May cause steady-state error (system stops close to target but not exactly at it).

## 2️⃣ PD-Controller (Proportional + Derivative)
Adds a derivative term (acts like damping).

```math
u(t) = K_p \times e(t) + K_d \times {de(t) \over dt}
```
- $K_d$ = derivative gain.
- The derivative term reacts to rate of change of error (velocity).

> 👉 Intuition:
> - Proportional term pulls you to the target.
> - Derivative term slows you down when you’re moving fast, preventing overshoot & oscillation.

✅ Pros: More stable than P-only.
❌ Cons: Still might not reach exact target (steady-state error remains).

## 3️⃣ PID-Controller (Proportional + Integral + Derivative)
Adds an integral term to fix steady-state error.

```math
u(t) = K_p \times e(t) + K_i \times \int_0^t e(\tau) d\tau + K_d \times {de(t) \over dt}
```

- $K_i$ = integral gain.
- The integral accumulates past errors - eliminates bias/offset.

👉 Example in robotics:
If a motor is under constant load, P/PD might never reach the target (error persists). The integral term adds torque until error is gone.

✅ Pros: Very accurate, handles disturbances well.
❌ Cons: More complex to tune, integral can cause instability (windup).
