# Version Control Strategy for Manuscripts

## Classification
- **Domain**: Writing/Technical
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Define git workflows optimized for narrative projects, managing both manuscripts and context network evolution.

## Branch Strategy

### Main Branches
```
main          → Published/final version
develop       → Active writing branch
editing       → Editorial changes branch
```

### Feature Branches
```
plot/subplot-name     → Experimental plot threads
character/name-arc    → Character development
revision/beta-feedback → Incorporating reader feedback
fix/consistency-issue → Addressing specific problems
```

## Commit Patterns

### Atomic Story Commits
```bash
# One scene per commit
git add manuscripts/ch07.md
git commit -m "Add confrontation scene between Maya and the Council"

# Context updates with manuscript changes
git add manuscripts/ch07.md context-network/elements/plot/confrontations.md
git commit -m "Add Maya/Council confrontation with plot analysis"
```

### Revision Commits
```bash
# Track revision rounds
git commit -m "R2: Strengthen Maya's motivation in Ch7 confrontation"
git commit -m "R3: Fix timeline inconsistency in Ch7 (moved from Tuesday to Thursday)"
```

### Global Changes
```bash
# Character rename
git commit -m "Rename: Meridian → Stanton throughout manuscripts"

# Setting changes
git commit -m "Update: Change city name from Ironhold to Ashmere (Ch1-Ch5)"
```

## Tag Conventions

### Milestone Tags
```bash
# Draft completion
git tag -a v1.0-first-draft -m "First complete draft - 85,000 words"

# Revision rounds
git tag -a v2.0-dev-edit -m "Post-developmental editing"
git tag -a v2.1-beta -m "Ready for beta readers"
git tag -a v3.0-final -m "Final manuscript for submission"
```

### Chapter Tags
```bash
# Stable chapter versions
git tag ch07-stable
git tag part2-complete
```

## Workflow Examples

### Starting New Chapter
```bash
git checkout develop
git checkout -b chapter/ch08-conflict
# Write chapter
git add manuscripts/ch08.md
git commit -m "Draft Ch8: Initial conflict setup"
# Update context
git add context-network/elements/plot/ch08-outline.md
git commit -m "Add Ch8 plot outline and connections"
# Merge when ready
git checkout develop
git merge chapter/ch08-conflict
```

### Major Revision Cycle
```bash
git checkout -b revision/pacing-fix
# Make changes across multiple chapters
git add manuscripts/ch0[3-7].md
git commit -m "R4: Compress timeline from 2 weeks to 5 days (Ch3-7)"
# Update context network
git add context-network/elements/plot/timeline.md
git commit -m "Update timeline documentation for pacing revision"
```

### Experimental Plot Thread
```bash
git checkout -b plot/maya-secret-past
# Try new subplot
git add manuscripts/ch09-alternate.md
git commit -m "Experiment: Add Maya's hidden connection to antagonist"
# If keeping:
git checkout develop
git merge plot/maya-secret-past
# If discarding:
git checkout develop
git branch -D plot/maya-secret-past
```

## Context Network Synchronization

### Parallel Updates
Always update context network when:
- Adding new plot elements
- Changing character relationships
- Modifying world rules
- Discovering narrative patterns

### Discovery Workflow
```bash
# During writing, discover important pattern
echo "## Maya's Speech Pattern
**Found**: \`manuscripts/ch08.md:234-245\`
**Discovery**: Maya drops contractions when lying
**Significance**: Subtle tell for reader attention" >> context-network/discoveries/character-voices.md

git add manuscripts/ch08.md context-network/discoveries/character-voices.md
git commit -m "Add Maya deception scene with speech pattern discovery"
```

## Recovery Patterns

### Finding Lost Scenes
```bash
# Search all branches for deleted content
git log --all --grep="scene name" 

# Recover specific scene
git show commit-hash:manuscripts/ch07.md > recovered-scene.md
```

### Comparing Versions
```bash
# See how scene evolved
git log -p manuscripts/ch07.md:234-289

# Compare two versions
git diff v1.0-first-draft v2.0-dev-edit manuscripts/ch07.md
```

## Best Practices

1. **Commit Frequently**: Every scene or major paragraph
2. **Descriptive Messages**: Include what changed and why
3. **Tag Milestones**: Mark significant versions for easy reference
4. **Branch Experiments**: Try alternatives without fear
5. **Update Context**: Keep network synchronized with manuscript

## Relationships
- Supports: [[tracking/discoveries]], [[processes/revision_cycles]]
- Integrates with: [[source_linking]], [[chapter_mapping]]
- Enables: [[meta/maintenance]]