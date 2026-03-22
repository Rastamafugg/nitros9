# Repository Agent Instructions

These instructions apply to any agent working in `D:\retro\nitros9`.

## 1. Required Reference Material

Before performing substantive work in this repository, read and follow the relevant documents in `reference\`:

1. `reference\nitros9-reference-manual-agent.md`
2. `reference\nitros9-assembly-source-agent.md`
3. `reference\NitrOS9 EOU Technical Reference.md`

These are mandatory operating references for repository tasks involving NitrOS-9 behavior, system calls, kernel behavior, command behavior, module loading, memory management, register contracts, or low-level troubleshooting.

## 2. Authority And Precedence

Use this precedence order unless higher-level platform instructions override it:

1. Direct user request
2. This `AGENTS.md`
3. `reference\NitrOS9 EOU Technical Reference.md`
4. `reference\nitros9-reference-manual-agent.md`
5. `reference\nitros9-assembly-source-agent.md`
6. Confirmed repository source code and tests

Interpretation note:

- The Technical Reference document is authoritative for documented NitrOS-9 semantics.
- The reference-manual agent guide defines how to perform syscall-oriented research and how to structure grounded findings.
- The assembly-source agent guide defines how to verify low-level behavior against source when documentation is incomplete, ambiguous, or suspected to be wrong.

## 3. Mandatory Working Rules

All agents operating in this repository must:

1. Treat the Technical Reference document as the default source of truth for NitrOS-9 system calls, register conventions, error handling, system organization, and memory behavior.
2. Consult `reference\nitros9-reference-manual-agent.md` before answering or implementing tasks that depend on documented syscall behavior or system integration details.
3. Consult `reference\nitros9-assembly-source-agent.md` before answering or implementing tasks that require source-level verification of kernel, command, or handler behavior.
4. Distinguish clearly between:
   - documented behavior
   - source-confirmed behavior
   - inferred behavior
5. Mark inference explicitly as `[INFERRED]`.
6. Do not guess call codes, register usage, carry behavior, error codes, or handler semantics.
7. Escalate uncertainty to the user when the documentation and source do not support a reliable conclusion.

## 4. Task Routing

Use the following routing rules:

### 4.1 Syscall And System Integration Tasks

For tasks involving `F$*`, `I$*`, `SS$*`, module lifecycle, process control, memory allocation, path operations, or register staging:

1. Read the Technical Reference document first.
2. Apply the research discipline defined in `reference\nitros9-reference-manual-agent.md`.
3. If any contract detail remains uncertain, verify against source using `reference\nitros9-assembly-source-agent.md`.

### 4.2 Assembly And Kernel Verification Tasks

For tasks involving kernel internals, dispatch tables, handlers, low-level command behavior, undocumented quirks, or doc/source mismatch checks:

1. Use `reference\nitros9-assembly-source-agent.md` as the governing method.
2. Cite the exact file and label examined.
3. Report contradictions or undocumented behavior explicitly.

### 4.3 Coding Tasks

For code changes in this repository:

1. Remain aware of the Technical Reference document when the change touches NitrOS-9 semantics.
2. Do not implement behavior that conflicts with the Technical Reference unless repository source proves a deliberate project-specific divergence.
3. When relying on a divergence, state whether it is `CONFIRMED`, `UNDOCUMENTED`, `AMBIGUOUS`, or `CONTRADICTION` relative to the Technical Reference.

## 5. Output Discipline

When reporting findings or decisions:

1. Prefer grounded statements tied to the Technical Reference or repository source.
2. Keep source claims citable and specific.
3. State unresolved ambiguity directly.
4. Do not present assumptions as facts.

## 6. Minimum Compliance Expectation

An agent is not compliant with this repository if it performs NitrOS-9-related work without first being guided by the documents listed in Section 1.
