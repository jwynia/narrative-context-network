# Interactive Narrative Format

## Classification
- **Domain**: Interactive Media/Gaming
- **Stability**: Evolving
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Structure branching narratives for games, interactive fiction, or choose-your-own-adventure formats while maintaining narrative coherence across paths.

## Interactive Structure Patterns

### Branch Mapping
```markdown
# Story Branch: [Branch Name]

## Branch Metadata
- **ID**: B001
- **Parent**: [Previous branch ID or START]
- **Type**: [Major/Minor/Flavor]
- **Impact**: [High/Medium/Low]
- **Prerequisites**: [What must happen before this]

## Decision Point
**Scene**: [Where this choice occurs]
**Context**: [What led to this moment]
**Stakes**: [What player risks/gains]

## Choices Available
### Choice A: [Action]
- **Immediate Result**: [What happens next]
- **Long-term Impact**: [Future consequences]
- **Leads to**: Branch B002
- **Flags Set**: [SAVED_ALLY, BROKE_PROMISE]

### Choice B: [Action]
- **Immediate Result**: [What happens next]
- **Long-term Impact**: [Future consequences]
- **Leads to**: Branch B003
- **Flags Set**: [LOST_ALLY, KEPT_PROMISE]

### Choice C: [Conditional - requires FLAG]
- **Required**: [PREVIOUS_KNOWLEDGE]
- **Result**: [Special outcome]
- **Leads to**: Branch B004
```

### State Tracking
```markdown
# Game State Variables

## Character Relationships
| Character | Variable | Range | Impact |
|-----------|----------|--------|---------|
| Elena | ELENA_TRUST | -100 to 100 | Dialogue options |
| Marcus | MARCUS_RESPECT | 0 to 100 | Quest availability |
| Kai | KAI_LOYALTY | 0 to 100 | Betrayal threshold |

## World State Flags
| Flag | Type | Description | Set By |
|------|------|-------------|---------|
| KING_DEAD | Boolean | King assassinated | B015 or B027 |
| CITY_SAVED | Boolean | Prevented invasion | B044 |
| MAGIC_LEARNED | Boolean | Player knows magic | B008 |
| ARTIFACT_FOUND | Counter | Ancient items (0-5) | Various |

## Resource Tracking
| Resource | Variable | Impact |
|----------|----------|---------|
| Gold | PLAYER_GOLD | Shop access |
| Reputation | REPUTATION | NPC reactions |
| Magic Power | MANA_LEVEL | Spell options |
```

### Convergence Design
```markdown
# Convergence Point: [Major Story Beat]

## Converging Branches
Multiple paths lead here to maintain narrative coherence:

### From Path A (Hero Route)
- **Entry State**: Allies intact, resources high
- **Adaptation**: Easier combat, more support

### From Path B (Rogue Route)  
- **Entry State**: Alone, resources moderate
- **Adaptation**: Stealth options, different dialogue

### From Path C (Dark Route)
- **Entry State**: Enemies everywhere, resources low
- **Adaptation**: Hostile NPCs, limited options

## Shared Elements
Regardless of path, player experiences:
- Core revelation about antagonist
- Key emotional character moment
- Critical world lore
- Major gameplay mechanic introduction
```

## Dialogue Systems

### Branching Dialogue
```markdown
# Dialogue: [Character] - [Scene Name]

## NPC: Elena
## Location: Tavern
## Prerequisites: FIRST_MEETING_COMPLETE

### Player Options

#### 1. "Tell me about the artifact" 
**Requirements**: None
**Response**: "It's older than the kingdom itself..."
**Effects**: 
- INFO_ARTIFACT flag set
- ELENA_TRUST +5
**Leads to**: Artifact_Dialogue_Tree

#### 2. "I don't trust you"
**Requirements**: None  
**Response**: "Trust is earned, I suppose..."
**Effects**:
- ELENA_TRUST -10
- Locks future romance options
**Leads to**: Mistrust_Path

#### 3. "I know you're lying" 
**Requirements**: PERCEPTION > 15 OR FOUND_EVIDENCE
**Response**: "How did you...?"
**Effects**:
- ELENA_TRUST -5
- ELENA_RESPECT +10
- Unlocks Truth_Path
**Leads to**: Confrontation_Tree

#### 4. [Kiss her]
**Requirements**: ELENA_TRUST > 75 AND ROMANCE_FLAG
**Response**: [Depends on prior choices]
**Effects**: 
- ROMANCE_CONFIRMED
- Major story branch
**Leads to**: Romance_Path
```

### Dynamic Text Adaptation
```markdown
# Adaptive Narrative Elements

## Character Address Variants
Based on PLAYER_CLASS:
- Warrior: "mighty warrior" / "soldier"
- Mage: "wise one" / "mage"
- Rogue: "shadow" / "quick one"

## Contextual Descriptions
Based on previous choices:

### If BURNED_VILLAGE:
"The smell of ash reminds you of what you've done."

### If SAVED_VILLAGE:  
"Children wave as you pass, remembering your heroism."

### If NEVER_VISITED_VILLAGE:
"The small village seems peaceful and untouched by war."

## Relationship Flavoring
Based on COMPANION_TRUST levels:

### High Trust (>75):
"Elena grabs your hand without hesitation."

### Medium Trust (25-75):
"Elena pauses, then takes your offered hand."

### Low Trust (<25):
"Elena stares at your extended hand, unmoved."
```

## Technical Implementation

### Scene Structure
```markdown
# Scene ID: S001_Throne_Room

## Scene Setup
- **Background**: throne_room.jpg
- **Music**: royal_theme.mp3
- **Characters Present**: [King, Elena, Guards]
- **Available Exits**: [Corridor, Secret_Passage*]
*Requires FOUND_SECRET flag

## Scene Script
```
ENTER scene
IF first_visit:
    SHOW king_intro_cutscene
    SET throne_room_visited
    
CHECK player_reputation:
    IF reputation > 50:
        King: "Welcome, hero!"
    ELIF reputation < -50:
        King: "Guards, watch this one."
    ELSE:
        King: "State your business."

PRESENT choices:
    1. Request audience
    2. Ask about quest
    3. [Attack] (requires AGGRESSIVE_PATH)
    4. Leave quietly
```
```

### Branch Testing Matrix
```markdown
# Path Testing Checklist

## Critical Paths
Test all major story routes:

### Hero Path
- [ ] All allies survive
- [ ] Maximum resources reached
- [ ] Best ending accessible
- [ ] No locked content

### Neutral Path
- [ ] Some allies lost
- [ ] Moderate resources
- [ ] Standard ending
- [ ] Some content locked

### Dark Path
- [ ] Minimal allies
- [ ] Low resources  
- [ ] Dark ending forced
- [ ] Much content locked

## Edge Cases
- [ ] Impossible state combinations
- [ ] Sequence breaks
- [ ] Rapid alignment changes
- [ ] Resource exploits
- [ ] Dialogue loops
```

## Content Scaling

### Writing Multiplication
```markdown
# Content Requirements by Branch Depth

## Linear Story
- 12 chapters × 5,000 words = 60,000 words

## 2-Branch Story
- 12 chapters × 2 paths × 4,000 words = 96,000 words
- Plus convergence writing

## 3-Branch Story  
- 12 chapters × 3 paths × 3,500 words = 126,000 words
- Plus convergence writing
- Plus conditional content

## Mitigation Strategies
1. **Hub Design**: Shared locations reduce duplication
2. **Convergence Points**: Merge paths at key moments
3. **Modular Scenes**: Reusable with variations
4. **Conditional Text**: Adapt rather than rewrite
```

### Scope Management
```markdown
# Interactive Scope Control

## High-Impact Choices (Limit to 5-7)
- Major character death
- Faction allegiance
- World-changing events
- Core relationship status

## Medium-Impact Choices (10-15)
- Quest resolution method
- Resource management
- Secondary relationships
- Skill development path

## Flavor Choices (Unlimited)
- Dialogue tone
- Cosmetic options
- Minor scene variations
- Personality expression
```

## Quality Assurance

### Narrative Coherence Checks
```markdown
## Story Logic Validation

### Temporal Consistency
- [ ] Events happen in possible order
- [ ] Travel time respected
- [ ] Age progression logical
- [ ] Season changes consistent

### Character Knowledge
- [ ] Characters only know what they've learned
- [ ] Player knowledge != Character knowledge  
- [ ] Information gating works
- [ ] No psychic NPCs

### Emotional Continuity
- [ ] Reactions match prior events
- [ ] Relationship changes feel earned
- [ ] Character growth tracks
- [ ] Tone shifts justified
```

### Player Agency Validation
```markdown
## Choice Impact Verification

### Immediate Feedback
- [ ] Every choice has visible result
- [ ] Player understands consequence
- [ ] No false choices
- [ ] Clear cause-effect

### Long-term Consequences
- [ ] Early choices matter later
- [ ] Callbacks to decisions
- [ ] Multiple payoffs per choice
- [ ] No forgotten threads
```

## Relationships
- Uses: [[plot/interactive_narrative_frameworks]]
- Enhances: [[elements/plot/scene_building]]
- Requires: [[state_management]], [[branch_design]]
- Supports: [[game_development]], [[if_creation]]