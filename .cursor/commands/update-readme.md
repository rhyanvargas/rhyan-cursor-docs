# /update-readme

Synchronize README.md with current codebase state.

## Usage

Update README based on current repo:
```
/update-readme
```

Update specific sections:
```
/update-readme --section tech-stack
/update-readme --section structure
/update-readme --section status
```

## Behavior

1. **Scan** - Analyze codebase for current state
2. **Compare** - Identify discrepancies with README
3. **Update** - Apply changes to keep README accurate
4. **Verify** - Confirm all references are valid

## Instructions

When the user invokes `/update-readme`:

### 1. Gather Evidence

Scan these sources to determine actual state:

| Source | Information |
|--------|-------------|
| `package.json` / `Cargo.toml` / `go.mod` / `requirements.txt` | Dependencies, tech stack |
| `src/` or main source directory | Project structure, modules |
| `tests/` or `test/` or `__tests__/` | Test coverage |
| `docs/` | Documentation structure |
| `.github/workflows/` | CI/CD configuration |

### 2. Update Sections

#### Tech Stack
- Read dependency manifest (package.json, Cargo.toml, etc.)
- List only technologies actually installed
- **Never assume** - verify each dependency exists
- Add reference: "See `[manifest file]` for versions"

#### Project Structure
- List actual directories and key files
- Mark empty/placeholder directories as "(planned)"
- Describe purpose based on actual code, not assumptions

#### Documentation Links
- Verify all linked files exist
- Add new docs if missing from README
- Remove broken links

#### Project Status
- Cross-reference source directories with README claims
- Check for actual test files to verify test coverage claims
- Update completion status based on implementation evidence

### 3. Formatting Rules

**Reference, don't duplicate:**

| Instead of... | Do this... |
|---------------|------------|
| Inline code examples | Link to source file |
| Hardcoded config samples | Link to actual config file |
| Duplicated schemas | Link to schema file |
| Version numbers | Reference manifest file |

**File reference format:**
```markdown
See [`path/to/file.ext`](path/to/file.ext) for details.
```

**For diagrams:**
- Keep mermaid diagrams in README (renders on GitHub)
- If diagram exists elsewhere, add source reference

### 4. Validation Checklist

Before finishing, verify:
- [ ] Tech stack matches dependency manifest exactly
- [ ] All source directories reflected accurately  
- [ ] Test files mentioned if tests exist
- [ ] No hardcoded versions (reference manifest instead)
- [ ] All doc links resolve to existing files
- [ ] Status reflects actual implementation state

## Anti-Patterns

| Don't | Why |
|-------|-----|
| Hardcode dependency versions | They drift from manifest |
| Copy code into README | Becomes stale when code changes |
| List planned features as complete | Misleads users |
| Assume tech stack | Always verify in manifest |
| Include implementation details | Link to source files instead |
| Guess file purposes | Read the code first |

## Output

After updating, provide a summary:

```markdown
## README Update Summary

**Sections Updated**: [list sections]

### Changes Made
- [Section]: [What changed] (evidence: [file])

### Verified Sources
- [manifest]: X dependencies checked
- [src dir]: X modules scanned  
- [test dir]: X test files found
- [docs dir]: X documents linked
```

## Next Steps

After update:
- Review changes in README.md
- Commit if accurate: `git add README.md && git commit -m "docs: sync README with codebase"`
