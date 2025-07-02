# Discoveries System

## Classification
- **Domain**: Knowledge Management
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Capture and organize insights discovered during writing, revision, and analysis. These discoveries inform future decisions and maintain story coherence.

## Discovery Categories

### Character Discoveries
Location: `character/`
- Voice patterns and quirks
- Relationship dynamics
- Behavioral patterns
- Growth opportunities

### Plot Discoveries  
Location: `plot/`
- Structure insights
- Pacing revelations
- Conflict patterns
- Theme emergence

### World Discoveries
Location: `world/`
- Setting details that emerge
- Cultural patterns
- System rules clarifications
- Environmental storytelling

### Theme Discoveries
Location: `themes/`
- Emergent meanings
- Symbol patterns
- Metaphor systems
- Resonance points

### Pattern Discoveries
Location: `patterns/`
- Recurring elements
- Style observations
- Reader engagement points
- Technique effectiveness

## Discovery Record Format

```markdown
# [Discovery Title]

## Discovery Metadata
- **Date**: YYYY-MM-DD
- **Discovered During**: [Writing/Revision/Analysis]
- **Impact Level**: [High/Medium/Low]
- **Integration Status**: [Pending/Integrated/Archived]

## What Was Found
**Location**: → manuscripts/[file]:[lines]
**Context**: [What you were working on when discovered]
**Discovery**: [The actual insight]

## Significance
[Why this matters to the story/project]

## Application
- **Immediate**: [How to use right away]
- **Future**: [Considerations for later]
- **Retroactive**: [What needs updating]

## Related Elements
- [[Link to affected character/plot/world elements]]
- [[Link to relevant frameworks]]
- [[Link to decision records if applicable]]

## Integration Checklist
- [ ] Update relevant character/plot/world nodes
- [ ] Check for consistency impacts
- [ ] Apply retroactively if needed
- [ ] Document in style guide if pattern
- [ ] Create framework if systematic
```

## Discovery Workflow

### During Writing
1. Notice pattern or insight
2. Quick note in manuscript margin
3. Create discovery record immediately
4. Continue writing
5. Integrate during revision

### During Revision
1. Identify pattern across chapters
2. Create discovery record
3. Assess impact on consistency
4. Plan integration approach
5. Execute changes systematically

### During Analysis
1. Review multiple elements
2. Recognize connections
3. Document meta-patterns
4. Create framework if applicable
5. Update planning documents

## Discovery Types

### Organic Discoveries
Things that emerge naturally from the writing:
- Character voice evolution
- Unplanned symbolism
- Natural plot connections
- Relationship chemistry

### Analytical Discoveries
Insights from deliberate analysis:
- Pacing patterns
- Structure optimizations
- Theme reinforcement opportunities
- Reader engagement mechanics

### Problem-Solving Discoveries
Solutions found while fixing issues:
- Plot hole resolutions
- Character motivation clarifications
- World-building solutions
- Consistency fixes

## Discovery Integration

### Priority Levels

#### High Priority
- Affects main plot or character arc
- Solves major problem
- Creates significant opportunity
- Reader experience critical

#### Medium Priority  
- Enhances story depth
- Improves consistency
- Adds useful pattern
- Nice-to-have improvement

#### Low Priority
- Minor enhancement
- Style preference
- Future consideration
- Experimental element

### Integration Tracking
```markdown
## Integration Status Key

### Pending
- Discovery recorded
- Impact assessed
- Not yet implemented
- Scheduled for: [revision round]

### Integrated
- Changes made to manuscripts
- Context network updated
- Consistency verified
- Completed: [date]

### Archived
- Considered but not used
- Superseded by better solution
- Not applicable to final version
- Archived: [date] because [reason]
```

## Best Practices

### Capture Immediately
- Don't rely on memory
- Record exact location
- Include enough context
- Note your thinking

### Be Specific
- Quote exact text when relevant
- Reference precise locations
- Describe concrete applications
- Avoid vague insights

### Think Systemically
- Consider broad impacts
- Look for patterns
- Connect to existing elements
- Plan integration carefully

### Review Regularly
- Check pending discoveries
- Group related insights
- Promote patterns to frameworks
- Archive obsolete discoveries

## Discovery Mining

### Character Voice Mining
```bash
# Extract unique phrases per character
for char in Marcus Elena Kai; do
  echo "=== $char ==="
  grep -h "$char said\|$char asked" manuscripts/*.md | 
  grep -o '"[^"]*"' | sort | uniq -c | sort -nr | head -20
done
```

### Plot Pattern Recognition
```bash
# Find scene transitions
grep -n "^\*\*\*\|^###" manuscripts/*.md | 
awk -F: '{print $1 ": " $2}' > scene_boundaries.txt

# Analyze chapter lengths
for f in manuscripts/ch*.md; do
  echo "$f: $(wc -l < $f) lines"
done
```

### Theme Extraction
```bash
# Find recurring imagery
echo "Water imagery:"
grep -n -i "water\|river\|ocean\|rain\|flow" manuscripts/*.md | wc -l

echo "Light/Dark imagery:"
grep -n -i "light\|dark\|shadow\|bright\|dim" manuscripts/*.md | wc -l
```

## Relationships
- Feeds: [[elements/]], [[processes/]]
- Supports: [[revision_cycles]], [[consistency_checks]]
- Creates: [[frameworks]], [[patterns]]
- Uses: [[manuscripts/tracking/]]