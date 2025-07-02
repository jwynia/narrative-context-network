# Character Voice Consistency Framework

## Classification
- **Domain**: Character Development
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Track and maintain consistent character voices throughout the narrative, including dialogue patterns, internal monologue styles, and narrative voice when in character POV.

## Voice Components

### Dialogue Patterns
```markdown
## Character Name: [Name]

### Speech Characteristics
- **Vocabulary Level**: [Simple/Moderate/Complex/Technical]
- **Sentence Structure**: [Short/Varied/Complex/Fragmentary]
- **Formality**: [Casual/Mixed/Formal/Archaic]
- **Contractions**: [Always/Usually/Sometimes/Never]

### Unique Markers
- **Catchphrases**: 
  - "[Phrase]" - Used when [situation]
  - "[Phrase]" - Indicates [emotional state]
- **Verbal Tics**:
  - [Description] → Example: "manuscripts/ch03.md:234"
- **Avoidance Patterns**:
  - Never says [word/phrase] because [reason]
```

### Emotional Voice Shifts
```markdown
## Emotional State Variations

### When Angry
- Sentence length: [Shortens/Lengthens]
- Vocabulary: [Simplifies/Becomes more complex]
- Unique markers: [Specific changes]
- Example: → manuscripts/ch07.md:445-456

### When Nervous
- Speech patterns: [Rambles/Becomes taciturn/Repeats]
- Physical indicators in dialogue tags
- Example: → manuscripts/ch04.md:123-134

### When Lying
- Subtle changes: [List specific markers]
- Consistency breaks: [What changes]
- Example: → manuscripts/ch09.md:678-690
```

## Voice Evolution Tracking

### Arc-Based Changes
```markdown
## Voice Evolution Timeline

### Act 1 - Establishment
- **Baseline Voice**: [Description]
- **Key Examples**: 
  - Introduction: → manuscripts/ch01.md:45-67
  - First conflict: → manuscripts/ch03.md:234-245

### Act 2 - Development
- **What Changes**: [Specific elements]
- **Why It Changes**: [Character growth/trauma/learning]
- **Transition Scene**: → manuscripts/ch08.md:123-145

### Act 3 - Resolution
- **Final Voice**: [How it differs from baseline]
- **Integration**: [What elements remain, what's new]
- **Climax Speech**: → manuscripts/ch11.md:890-920
```

### Relationship-Based Variations
```markdown
## Voice Modulation by Relationship

### With Authority Figures
- Formality level: [Changes]
- Specific adaptations: [List]
- Example: → manuscripts/ch05.md:345-367

### With Peers
- Casual markers: [List]
- Shared language: [In-jokes, references]
- Example: → manuscripts/ch06.md:123-145

### With Romantic Interest
- Vulnerability markers: [What changes]
- Unique patterns: [Specific to this relationship]
- Evolution: [How it changes over story]
```

## Consistency Checking Tools

### Quick Reference Card
```markdown
# [Character Name] Voice Card

## Never Says
- Contractions when formal
- Technical jargon (unless explaining)
- Modern slang (maintains period voice)

## Always Does
- Questions when uncertain (doesn't state)
- Uses metaphors from [background/profession]
- Addresses others by [title/name/nickname]

## Red Flags for Inconsistency
- Using contractions in formal settings
- Vocabulary above/below established level
- Breaking established speech patterns without cause
```

### Dialogue Audit Checklist
```markdown
## Chapter [X] Dialogue Review

- [ ] Check formality matches situation
- [ ] Verify vocabulary consistency
- [ ] Confirm emotional markers align
- [ ] Validate relationship-appropriate voice
- [ ] Track any intentional evolution
- [ ] Note discoveries for pattern library
```

## Implementation Examples

### Strong Voice Consistency
```markdown
## Maya - Scholarly Voice

### Established Pattern (Ch1)
"The historical precedents would suggest that such an endeavor, 
while not without merit, faces considerable structural impediments."

### Maintained Under Stress (Ch7)
"The structural impediments I mentioned? They're here. Now. 
And they're armed." [Formality cracks but vocabulary remains]

### Evolution Complete (Ch12)
"History taught me the words. You taught me when to stop 
using them." [Acknowledges change while honoring origin]
```

### Voice Differentiation
```markdown
## Contrasting Voices in Same Scene

**Scholar**: "The archaeological evidence suggests—"
**Soldier**: "Doc, short version. Bad guys. Where?"
**Scholar**: "Ah. Yes. North. Armed. Many."
**Soldier**: "Now you're talking my language."

[Note how scholar adapts but maintains core identity]
```

## Discovery Integration

Link all voice discoveries to this framework:
```markdown
## Recent Voice Discoveries
- [[discoveries/maya-drops-contractions]] - When lying
- [[discoveries/kai-battlefield-voice]] - Reverts to training
- [[discoveries/elder-speech-rituals]] - Formal patterns
```

## Relationships
- Enhances: [[naming_frameworks]], [[overview]]
- Supports: [[manuscripts/tracking/consistency]]
- Integrates with: [[elements/plot/dialogue_frameworks]]
- Used by: [[processes/revision_cycles]]