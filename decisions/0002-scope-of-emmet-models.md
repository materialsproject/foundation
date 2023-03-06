# Scope of emmet document models

## Context and Problem Statement

`emmet` currently contains the document models that define schemas for certain
calculation types, particularly from VASP. The newer VASP schemas developed
alongside `atomate2` are now fairly stable, and hence should be merged into 
`emmet`. This raises several questions about backward compatibility with legacy
document models and with dependency handling. Specifically:

1. The `atomate2` documents contain new fields and changed field names compared
   to `atomate1`.
2. `atomate1` task documents use `task_id` whereas `atomate2` documents use
   `UUID` as identifiers.
3. Many `atomate2` document models contain logic for instantiating from raw
   calculation outputs, e.g. `from_vasp_files()`. Should these live in the emmet
   document models, or elsewhere?
4. The methods in item 3) may create dependency bloat - how should this be
   handled?
5. When should a document model "graduate" from `atomate2` to `emmet`?
6. Is the purpose of `emmet-core` to power MP, or to host general document 
   models for the community?

Clarification of the above is also important not only for updating our VASP
models, but to guide other work-in-progress document models in `atomate2` (e.g.,
Q-Chem).

## Decision Drivers

- It is often unfeasible to re-parse existing MP calculations. Any changes to 
  key names or reorganization of task documents need to be accompanied by a
  database migration script.
- Alternatively, `atomate2` document models can just *add* keys without
  modifying existing ones. 
- As part of updating document models, the meaning of `task_label` should be
  revisited because it is sometimes overloaded by users, which breaks queries.

## Considered Options

### Option 1: Use optional dependencies

Dependencies that are only required by specific methods (e.g. 
`from_vasp_files()`) will be made optional and imported from within the method
itself. We make sure that only non-optional dependencies are required to
instantiate a document model with arbitrary data. @utf or other `atomate2`
maintainers can be made maintainers of `emmet` as well to reduce development
friction.

- Good, because this avoids dependency bloat
- Good, because this allows methods that instantiate Task Docs from calculation
  outputs to be defined in the same place as the Task Doc itself
- Neutral, because making `atomate2` maintainers `emmet` maintainers minimizes
  development friction

### Option 2: Keep calculation code-specific dependencies in separate packages

`emmet` can be used to define code-agnostic document models (as is currently the
case in `emmet-core`), while document models specific to a code (e.g. VASP)
would live in separate I/O packages e.g. `pymatgen.io.vasp`. 

- Good, because this would keep most of the code maintenance that requires
  detailed knowledge of a specific calculation code in one repo. 
- Bad, because this approach will result in document models defined in multiple
  places.

### Proposed clarification of the purpose of `emmet-core`

The purpose of `emmet-core` is to power MP and to provide examples and base
classes (e.g. `TaskDocument`, `PropertyDoc`) that the community can build on. We
can encourage users of other codes or new methods to check `emmet` first to see
if a document model exists for that calculation type, and if it doesn't, to
develop the new model in `atomate2` alongside their workflows. `emmet` and
`atomate2` maintainers / MP Staff can make decisions about whether and when
it makes sense to port any of these into `emmet`.

- It is not sustainable for `emmet` to be a general home for document models of
  any type, because of the sheer number of codes and calculation types

## Decision Outcome

The decision was taken to proceed with option 1. `emmet` will be used to house
documents that are used in the Materials Project website and core workflows.
Documents that provide `from_files` functions will ensure that all imports are
performed inside the function itself to prevent dependency bloat.

To ensure maximum compatibility with the existing set of parsed calculation
data, all field names that have been changed in `atomate2` will be updated to
match the field names in `emmet`. New fields such as `UUID` will be kept.

It is expected that some task documents may start out in `atomate2` but 
ultimately become part of the Materials Project infrastructure. When this
happens the documents will be moved to `emmet`. These decisions will be made on
a case-by-case basis.

## More Information

[emmet issue #517](https://github.com/materialsproject/emmet/issues/517)

[atomate 2 #150](https://github.com/materialsproject/atomate2/issues/150)
