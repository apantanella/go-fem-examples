# go-fem-examples

Example problems for [go-fem](https://github.com/your-org/go-fem) — a 3D Finite Element Method library and HTTP API server written in Go.

Each example is a self-contained directory with a `problem.json` ready to POST to the `/solve` endpoint, and a `README.md` describing the problem setup and expected results.

## Prerequisites

Start the `go-fem` API server:

```bash
git clone https://github.com/your-org/go-fem.git
cd go-fem
go run ./cmd/femgo          # listens on :8080 by default
```

## Running an example

```bash
curl -s -X POST http://localhost:8080/solve \
     -H "Content-Type: application/json" \
     -d @examples/<name>/problem.json | jq .
```

---

## Examples

| Directory | Element type(s) | Load type | Description |
|-----------|----------------|-----------|-------------|
| [cantilever_beam](examples/cantilever_beam/) | `hexa8_3d` | Nodal | Steel cantilever (4 Hexa8 elements), tip point load |
| [single_hex8](examples/single_hex8/) | `hexa8_3d` | Nodal | Single unit cube under uniaxial compression |
| [tet4_patch](examples/tet4_patch/) | `tet4_3d` | Nodal | 3-element aluminium patch test (constant stress) |
| [bridge_load](examples/bridge_load/) | `hexa8_3d` | Nodal | Concrete slab (2 Hexa8), mid-span load, LU solver |
| [frame_portal](examples/frame_portal/) | `elastic_beam_3d` | Nodal | 3D portal frame, fixed bases, lateral sway load |
| [plane_frame](examples/plane_frame/) | `elastic_beam_2d` | Nodal | 2D portal frame with gravity UDL on crossbeam |
| [truss2d](examples/truss2d/) | `truss_2d` | Nodal | Simple 2D truss under vertical load |
| [beam3d](examples/beam3d/) | `hexa8_3d` | Nodal | Cantilever beam — Hexa8 mesh convergence study |
| [beam_with_dist_load](examples/beam_with_dist_load/) | `elastic_beam_3d` | `beam_dist` | Two-span beam with UDL, fixed ends |
| [pressure_on_cube](examples/pressure_on_cube/) | `hexa8_3d` | `surface_pressure` | Steel cube with uniform pressure on top face |
| [gravity_solid](examples/gravity_solid/) | `hexa8_3d` | `body_force` | Concrete cube under self-weight |
| [ortho_cube](examples/ortho_cube/) | `hexa8_3d` | Nodal | Softwood cube (orthotropic material) under axial compression |
| [timoshenko_deep_beam](examples/timoshenko_deep_beam/) | `timoshenko_beam_3d` | Nodal | Deep cantilever (L/h=2): shear adds ~16 % to EB deflection |
| [dkt3_tri_plate](examples/dkt3_tri_plate/) | `dkt3_3d` | Nodal | DKT3 triangle: clamped edge, point load and UDL variants |
| [tri_plane](examples/tri_plane/) | `tri3_2d`, `tri6_2d` | Nodal | Plane-stress cantilever meshed with CST/LST triangles |
| [mixed_3d_building](examples/mixed_3d_building/) | `hexa8_3d`, `elastic_beam_3d`, `truss_3d`, `shell_mitc4_3d`, `dkt3_3d` | Nodal + `body_force` | 3D building with 5 element types: foundation, frame, truss bracing, roof shell |

---

## Unit system

All examples use the **N-mm-MPa** unit system unless otherwise noted in the example README.

## License

MIT – see [LICENSE](LICENSE).
