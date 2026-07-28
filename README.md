# Cinatra Blog Idea Authoring

The authoring methodology Cinatra follows when a workspace user asks the chat to draft a blog-post idea, outline or angle. It is the knowledge half of `@cinatra-ai/blog-idea-artifact`, packaged as its own skill so the artifact extension declares a dependency on it instead of shipping it inside.

**Install:** Install `@cinatra-ai/blog-idea-authoring-skill` in your Cinatra instance. `@cinatra-ai/blog-idea-artifact` installs it automatically as a declared dependency.

**Usage:** The chat assistant loads this skill through the artifact extension's declared `authoring` dependency edge when the user asks for a new Blog Idea — you do not invoke it directly. It gathers the inputs it needs, composes the document and emits it as a typed artifact.

**Configuration:** None. The skill carries no credentials and reads no settings; the host supplies the model runtime.

**Development:** Clone the repository and run `node extension-kind-gate.mjs --package-root .` to validate the manifest. The bundle lives in `skills/blog-idea-authoring/` — a single `SKILL.md` router with no reference files.

**Troubleshooting:** If the chat says the extension has no authoring skill, check that `@cinatra-ai/blog-idea-artifact` is installed and that its declared dependency on this package resolved; an unresolved edge leaves the authoring path with nothing to follow.

## Works with

- Cinatra Blog Idea artifact extension
- Any extension declaring a skill dependency on this package

## Capabilities

- Ask the user for the inputs Blog Idea needs before writing anything
- Compose the document in the section structure the matcher recognizes
- Emit the result as a typed Cinatra artifact rather than chat prose
- Refuse to invent facts, links or metrics the user did not supply
