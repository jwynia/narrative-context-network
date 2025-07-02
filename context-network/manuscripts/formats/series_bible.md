# Series Bible Format

## Classification
- **Domain**: Multi-Book/Publishing
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Maintain consistency across multiple books in a series, tracking evolving elements while preserving canon.

## Series Bible Structure

### Core Canon
```markdown
# [Series Name] Bible - Core Canon

## Immutable Elements
These elements CANNOT change without breaking series continuity:

### World Rules
1. **Magic System**: [Core mechanics that can't change]
2. **Physical Laws**: [What's possible/impossible]
3. **History**: [Established past events]
4. **Geography**: [Fixed locations and distances]

### Character Foundations
1. **Origin Stories**: [Established backstories]
2. **Core Relationships**: [Family, key connections]
3. **Defining Moments**: [Past events referenced]
4. **Physical Traits**: [Unchangeable features]

## Flexible Elements  
These can evolve but must track changes:

### Character Growth
- Skills and abilities (can increase)
- Relationships (can change)
- Beliefs and values (can evolve)
- Knowledge (can expand)

### World Expansion
- New locations (can discover)
- Hidden history (can reveal)
- Political changes (can occur)
- Cultural evolution (can happen)
```

### Book-Specific Tracking
```markdown
# Book [Number]: [Title]

## Story Status
- **Timeline**: [When in series chronology]
- **Draft Status**: [Planning/Writing/Revision/Complete]
- **Word Count**: [Current/Target]
- **POV Characters**: [Who narrates]

## New Introductions
### Characters
| Name | Role | Introduction | Status at End |
|------|------|--------------|---------------|
| [Name] | [Role] | Ch.X | [Alive/Dead/Missing] |

### Locations
| Place | Type | Introduction | Significance |
|-------|------|--------------|--------------|
| [Name] | [City/Region] | Ch.X | [Why important] |

### Concepts/Terms
| Term | Definition | Introduction | Usage Rules |
|------|------------|--------------|-------------|
| [Term] | [Meaning] | Ch.X | [How to use] |

## Character Arcs
### [Character Name]
- **Start State**: [Where they begin this book]
- **End State**: [Where they end this book]
- **Key Growth**: [What changes]
- **Carried Forward**: [What continues to next book]

## Plot Threads
### Resolved This Book
- [Thread]: [How resolved]

### Continuing to Next
- [Thread]: [Current status]
- **Cliffhanger**: [If applicable]

### Seeds Planted
- [Future thread]: [What was hinted]
- **Planned Payoff**: Book [X]
```

### Cross-Book Continuity
```markdown
# Continuity Tracking

## Character Status Matrix
| Character | Book 1 | Book 2 | Book 3 | Notes |
|-----------|---------|---------|---------|-------|
| Marcus | Soldier | Captain | General | Rapid promotion arc |
| Elena | Mage | Exile | Archmage | Power loss/regain |
| Kai | Ally | Missing | Antagonist | Corruption arc |

## Relationship Evolution
### Marcus ↔ Elena
- **Book 1**: Distrust → Respect
- **Book 2**: Partners → Romance
- **Book 3**: Separated → Reunited
- **Key Scenes**: [Book:Chapter references]

## Power Progression
### Magic Users
| Character | Book 1 | Book 2 | Book 3 | Limits |
|-----------|---------|---------|---------|--------|
| Elena | Apprentice | Journeyman | Master | Can't resurrect |
| Sage | Master | Grandmaster | Ascended | Reality-bound |

## Timeline Coordination
### Major Events
| Event | Book | Date | Impact |
|-------|------|------|---------|
| The Breaking | 1 | Year 0 | Magic returns |
| First War | 1-2 | Year 1-3 | Kingdom falls |
| Reunification | 3 | Year 5 | New order |
```

## Format Guidelines

### Consistency Requirements
```markdown
## Must Match Across Books

### Language/Terms
- Spell names remain constant
- Place names don't change spelling
- Character epithets stay consistent
- Cultural terms maintain meaning

### Character Details
- Physical descriptions match
- Speech patterns evolve logically
- Backstory references align
- Relationship history consistent

### World Details
- Travel times between locations
- Season/weather patterns
- Political structures (unless changed in story)
- Economic systems

### Magic/Technology
- What's possible stays possible
- Limitations remain (unless addressed)
- Cost/consequence consistency
- Power scaling logic
```

### Evolution Tracking
```markdown
## Changes Between Books

### Intentional Changes
Document when things change ON PURPOSE:

#### Example: Political Change
- **Book 1**: Kingdom of Aldara (monarchy)
- **Book 2**: Aldaran Republic (revolution in book)
- **Change Point**: Book 2, Chapter 15
- **Impact**: All titles/ranks adjusted

### Growth/Development
Track natural progression:

#### Example: Character Skill
- **Book 1**: "Marcus fumbled with his sword"
- **Book 2**: "Marcus moved with practiced ease"
- **Book 3**: "Marcus's blade work was legendary"
- **Training Shown**: Book 1 end, Book 2 beginning
```

## Series Planning Tools

### Arc Planning Matrix
```markdown
## Multi-Book Arc Planning

### Character Arcs
| Arc | Book 1 | Book 2 | Book 3 | Resolution |
|-----|---------|---------|---------|------------|
| Marcus Identity | Questions heritage | Discovers truth | Accepts destiny | Becomes king |
| Elena Power | Awakens ability | Masters control | Transcends limits | Saves world |
| Kai Loyalty | Faithful friend | Seeds of doubt | Betrayal | Redemption? |

### Plot Thread Weaving
| Thread | Introduced | Developed | Complicated | Resolved |
|--------|------------|-----------|-------------|----------|
| Ancient Prophecy | B1Ch3 | B1-2 | B2Ch15 | B3Ch20 |
| Missing Heir | B1Ch1 | B2 | B3Ch1-10 | B3Ch19 |
| Dark Cult | B1Ch8 | B2-3 | B3Ch5 | B4? |
```

### Reader Experience Tracking
```markdown
## Information Management

### What Reader Knows
| Information | Book 1 | Book 2 | Book 3 |
|-------------|---------|---------|---------|
| Marcus is heir | Suspicious | Confirmed | Accepted |
| Elena's origin | Hidden | Hinted | Revealed |
| Villain identity | Unknown | Clues | Exposed |

### Mystery/Reveal Tracking
- **Mystery**: Who killed the king?
  - **Clues**: B1Ch4 (weapon), B2Ch7 (witness), B3Ch2 (motive)
  - **Red Herrings**: B1Ch8 (false suspect), B2Ch3 (fake evidence)
  - **Reveal**: B3Ch15 (confrontation scene)
```

## Technical Continuity

### File Organization
```
series-name/
├── bible/
│   ├── core-canon.md
│   ├── character-roster.md
│   ├── world-map.md
│   ├── timeline.md
├── book-1/
│   ├── manuscript/
│   ├── book-specific.md
├── book-2/
│   ├── manuscript/
│   ├── book-specific.md
├── continuity/
│   ├── cross-book-tracking.md
│   ├── evolution-log.md
```

### Version Control for Series
```bash
# Tag each book completion
git tag book-1-final
git tag book-2-final

# Branch for each book
git checkout -b book-3-development

# Track bible changes
git add bible/
git commit -m "Bible: Update character status post-Book-2"
```

## Common Series Pitfalls

### Continuity Errors to Avoid
- Character ages not advancing properly
- Forgetting established injuries/scars
- Changing fundamental rules mid-series
- Contradicting established history
- Losing track of side character status

### Reader Trust Maintenance
- Honor promises made in earlier books
- Resolve all major threads by series end
- Keep power scaling believable
- Maintain character voice consistency
- Respect established relationships

## Relationships
- Uses: [[manuscripts/]], [[characters/]], [[world/]]
- Supports: [[planning/milestones]], [[delivery]]
- Creates: [[continuity]], [[reader-trust]]
- Integrates with: [[revision_cycles]]