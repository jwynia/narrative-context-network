# Revision Cycles Process

## Classification
- **Domain**: Writing/Editorial
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Structure systematic approaches to manuscript revision, from developmental editing through final proofing.

## Revision Stages Overview

### Stage 1: Structural/Developmental
Focus: Story architecture, plot logic, character arcs, pacing

### Stage 2: Line Editing  
Focus: Scene flow, paragraph structure, voice consistency

### Stage 3: Copy Editing
Focus: Grammar, consistency, fact-checking

### Stage 4: Proofreading
Focus: Typos, formatting, final polish

## Stage 1: Structural Revision Process

### Pre-Revision Analysis
```markdown
## Structural Analysis Checklist

### Plot Architecture
- [ ] Map all plot threads in context network
- [ ] Identify pacing issues by chapter
- [ ] Mark scenes for: Keep/Cut/Combine/Expand
- [ ] Verify setup/payoff for all major elements

### Character Arcs  
- [ ] Validate each arc has clear progression
- [ ] Check relationships evolve logically
- [ ] Ensure character decisions drive plot
- [ ] Confirm voice evolution matches growth

### World Consistency
- [ ] Audit all world rules are followed
- [ ] Check timeline for impossibilities  
- [ ] Verify geography/travel makes sense
- [ ] Validate cultural elements consistent
```

### Revision Planning
```markdown
## Revision Plan: [Version Name]

### Priority 1: Critical Structure Issues
1. **Issue**: Timeline impossibility Ch7-9
   - **Solution**: Compress three days to one
   - **Chapters Affected**: 7, 8, 9
   - **Context Updates**: [[world/timeline]]

2. **Issue**: Character arc stalls Ch5-6  
   - **Solution**: Add failure/growth moment
   - **Chapters Affected**: 5, 6
   - **Context Updates**: [[characters/protagonist/evolution]]

### Priority 2: Pacing Improvements
[Continue pattern...]
```

### Implementation Tracking
```bash
# Create revision branch
git checkout -b revision/structural-r1

# Track each change
git commit -m "R1: Fix timeline impossibility Ch7-9"
git commit -m "R1: Add Marcus growth beat Ch5"

# Update context network in parallel
git commit -m "Context: Update timeline documentation for Ch7-9 compression"
```

## Stage 2: Line Editing Process

### Scene-Level Analysis
```markdown
## Scene Flow Checklist

### Opening Hook
- [ ] First line engages immediately
- [ ] Establishes when/where efficiently  
- [ ] Character perspective clear
- [ ] Tension/question present

### Scene Body
- [ ] Clear scene goal
- [ ] Conflict escalates appropriately
- [ ] Dialogue serves multiple purposes  
- [ ] Description balanced with action

### Scene Close  
- [ ] Propels to next scene
- [ ] Emotional resonance achieved
- [ ] Plot advanced or complicated
- [ ] Reader question maintained
```

### Voice Consistency Pass
```markdown
## Voice Audit Process

1. **Extract all dialogue for each character**
   ```bash
   # Create character dialogue file
   grep -n "^\".*\"$" manuscripts/ch*.md | grep -B1 -A1 "Marcus said" > marcus-dialogue.md
   ```

2. **Review against voice guide**
   - Check [[characters/voice_consistency]]
   - Mark inconsistencies
   - Note evolution points

3. **Revise for character voice**
   - Adjust vocabulary to match education/background
   - Ensure emotional markers consistent
   - Validate relationship dynamics in speech
```

## Stage 3: Copy Editing Process

### Consistency Tracking
```markdown
## Copy Edit Tracking Log

### Names/Terms
| Original | Standardized | Chapters | Notes |
|----------|--------------|----------|-------|
| grey/gray | gray | All | American spelling |
| Marc/Marcus | Marcus | 3,7,9 | Character name |
| Council/council | Council | All | Proper noun |

### Timeline/Facts
| Chapter | Issue | Resolution |
|---------|-------|------------|
| Ch4 | Says "yesterday" but was 3 days | Changed to "three days ago" |
| Ch7 | Moon phase wrong | Adjusted to match Ch3 reference |

### Repeated Issues
- Overuse of "suddenly" - removed 80%
- Inconsistent hyphenation - standardized
- Dialog tag variety - reduced "said" by 30%
```

### Style Guide Application
```markdown
## Project Style Decisions

### Dialogue
- Use em-dashes for interruptions—
- Ellipses for trailing off...
- Single quotes for thoughts
- Double quotes for speech

### Numbers
- Spell out one through ten
- Use numerals for 11+
- Always spell in dialogue
- Military time as numerals

### Series-Specific
- Capitalize: Council, Order, Power
- Lowercase: magic, elder, warrior
- Italicize: foreign terms first use
- Small caps: written documents
```

## Stage 4: Proofreading Process

### Final Pass Checklist
```markdown
## Proofreading Checklist

### Typography
- [ ] No double spaces
- [ ] Correct dash types (em/en)
- [ ] Consistent ellipses spacing
- [ ] Smart quotes throughout

### Formatting
- [ ] Chapter headings consistent
- [ ] Scene break markers uniform
- [ ] Paragraph indentation correct
- [ ] No widows/orphans

### Final Reads
- [ ] Read backwards for typos
- [ ] Read aloud for flow
- [ ] Fresh eyes read (after break)
- [ ] Format-specific check (ebook/print)
```

## Revision Workflow Integration

### Context Network Updates
During each revision stage:
1. Update relevant framework documents
2. Log significant changes in decisions
3. Track discoveries about story
4. Maintain location indexes

### Version Control
```bash
# Tag each revision stage
git tag -a v2.1-post-structural -m "Structural revision complete"
git tag -a v2.2-post-line -m "Line editing complete"
git tag -a v2.3-post-copy -m "Copy editing complete"  
git tag -a v2.4-final -m "Proofread and ready"
```

## Relationships
- Uses: [[manuscripts/]], [[characters/voice_consistency]]
- Supports: [[tracking/consistency]], [[validation]]
- Integrates with: [[decisions/]], [[milestones]]
- Enables: [[delivery]]