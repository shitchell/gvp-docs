# GVP Roadmap

Future considerations and evolution paths for the GVP framework.


## Typed Mappings

**Status:** Deferred (YAGNI — no current use case requires edge labels)

Currently all relationships use a single `maps_to` field with untyped
edges. The relationship semantics (e.g., "advances", "depends on",
"operationalizes") are derivable from the types of the source and
target nodes.

If a use case emerges where edge labels carry non-derivable information,
the evolution path is:

1. Rename `maps_to` to `mappings` and accept both strings and objects
2. Plain strings are sugar for `{target: "...", type: null}`
3. Typed edges are opt-in: `{target: personal:P3, type: depends_on}`
4. Relationship types defined in a separate YAML file (like tags.yaml)

This is backwards-compatible — existing simple references still work.


## Relationship Type Registry

**Status:** Deferred (blocked by typed mappings)

A `relationship_types.yaml` file defining valid edge labels, similar
to how `tags.yaml` defines valid tags. Would enable validation that
typed mappings use known relationship types.
