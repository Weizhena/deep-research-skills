# Deep Research Skill for Claude Code

> Inspired by [RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context](https://arxiv.org/abs/2511.18743)

A structured research workflow skill for Claude Code, supporting two-phase research: outline generation (extensible) and deep investigation. Human-in-the-loop design ensures precise control at every stage.

## Use Cases

- **Academic Research**: Paper surveys, benchmark reviews, literature analysis
- **Technical Research**: Technology comparison, framework evaluation, tool selection
- **Market Research**: Competitor analysis, industry trends, product comparison
- **Due Diligence**: Company research, investment analysis, risk assessment

## Commands

| Command | Description |
|---------|-------------|
| `/research` | Generate research outline with items and fields |
| `/research/add-items` | Add more items to existing outline |
| `/research/add-fields` | Add more fields to existing outline |
| `/research/deep` | Deep research each item with parallel agents |

## Installation

Copy the `skills/` folder to your Claude Code directory:

```bash
cp -r skills/* ~/.claude/skills/
```

## Workflow

### Phase 1: Generate Outline
```
/research <topic>
```
- Uses model knowledge + web search
- Asks for existing field definitions
- Outputs `{topic}_outline.yaml` in current directory

### Phase 2: Deep Research
```
/research/deep
```
- Reads outline automatically from current directory
- Launches parallel agents (5 per batch)
- Outputs structured JSON per item
- Supports resume from checkpoint

### Optional: Expand Outline
```
/research/add-items    # Add more research targets
/research/add-fields   # Add more field definitions
```

## Output Format

### Outline (YAML)
```yaml
topic: "your topic"
items:
  - name: "Item1"
    source: "source info"
fields:
  basic_info:
    - name: "field_name"
      description: "field description"
      detail_level: "detailed|brief"
execution:
  batch_size: 5
```

### Research Result (JSON)
Each item outputs a structured JSON file with all defined fields.

## References

- RhinoInsight: Improving Deep Research through Control Mechanisms for Model Behavior and Context

## License

MIT
