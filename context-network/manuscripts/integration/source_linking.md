# Source File Linking

## Classification
- **Domain**: Writing/Integration
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Define patterns for linking context network nodes to specific locations in manuscript files.

## Linking Patterns

### Direct Location References
```markdown
→ manuscripts/chapter-03.md:145-167  # Scene: First confrontation
→ manuscripts/book2/ch07.docx:p23    # Dialogue: Promise made
→ drafts/v3/prologue.md:1-45         # Opening hook
```

### Context Node References
```markdown
## Character Voice Discovery
**Found**: `manuscripts/ch12.md:445-498`
**Context**: Elara's speech pattern shifts when discussing her past
**Significance**: Establishes vulnerability through linguistic markers
**See also**: [[characters/elara/voice_evolution]]
```

### Bidirectional Linking
In manuscript files:
```markdown
<!-- CONTEXT: [[world/magic_system/limitations]] -->
The spell flickered and died...

<!-- CHARACTER_NOTE: [[characters/marcus/growth_arc#chapter7]] -->
Marcus hesitated, remembering his father's words...
```

## Location Index Format

### Chapter-Level Index
```markdown
# Chapter 7 Key Locations

## Opening Hook
- **Location**: `ch07.md:1-15`
- **Purpose**: Establish tension through weather
- **Context**: [[plot/rising_action/storm_sequence]]

## Character Revelation
- **Location**: `ch07.md:234-289`
- **Purpose**: Marcus discovers the truth
- **Context**: [[characters/marcus/arc#revelation]]

## Cliffhanger
- **Location**: `ch07.md:1250-1265`
- **Purpose**: Set up Chapter 8 conflict
- **Context**: [[plot/structure/cliffhangers]]
```

### Scene-Level Tracking
```markdown
# Scene: Council Meeting (Ch9)

## Setup
- **Location**: `ch09.md:45-123`
- **Elements**: [[world/politics/council]], [[characters/antagonist]]

## Conflict
- **Location**: `ch09.md:124-445`
- **Techniques**: [[dialogue/conflict_escalation]]

## Resolution
- **Location**: `ch09.md:446-523`
- **Impact**: [[plot/consequences/council_decision]]
```

## Best Practices

### 1. Granularity
- Link to specific line ranges, not entire files
- Use meaningful excerpts in discovery records
- Track both micro (line-level) and macro (scene-level) locations

### 2. Maintenance
- Update links when moving text between chapters
- Archive outdated links with version notes
- Use relative paths within manuscript directory

### 3. Searchability
- Include key phrases in location descriptions
- Tag with relevant character/plot elements
- Maintain reverse index (manuscript → context)

## Integration Tools

### Quick Reference Script
```bash
# Find all references to a specific chapter
grep -r "ch07.md" context-network/

# List all manuscript links in character nodes
find context-network/elements/characters -name "*.md" -exec grep -l "manuscripts/" {} \;
```

### Link Validation
```bash
# Check for broken manuscript links
for link in $(grep -r "→ manuscripts/" context-network/ | grep -o "manuscripts/[^:]*:[0-9-]*"); do
  file=$(echo $link | cut -d: -f1)
  lines=$(echo $link | cut -d: -f2)
  if [ ! -f "$file" ]; then
    echo "Missing: $file"
  fi
done
```

## Relationships
- Supports: [[tracking/discoveries]], [[tracking/location_indexes]]
- Uses: [[meta/node_template]]
- Enables: [[processes/revision_cycles]]