# Context Network Pruning Guide

## Classification
- **Domain**: Meta/System
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Define strategies for identifying and removing unnecessary complexity while preserving valuable project history and decision rationale.

## Pruning Philosophy

### What to Keep
- **Decision records** - Even overturned ones show evolution
- **Failed experiments** - Document what didn't work and why
- **Discovery paths** - How you found solutions matters
- **Relationship maps** - Connections between elements

### What to Prune
- **Redundant information** - Same content in multiple places
- **Speculative planning** - Ideas that were never pursued
- **Outdated templates** - Replaced by better versions
- **Broken fragments** - Incomplete thoughts without context

## Pruning Triggers

### Size Triggers
```markdown
## When to Consider Pruning

### Folder Level
- More than 20 files in a single folder
- Navigation requires multiple levels
- Similar named files accumulating
- Index files becoming unwieldy

### File Level  
- Single file over 500 lines
- Multiple topics in one document
- Repeated information sections
- Historical cruft overwhelming current

### Network Level
- Total nodes exceed 200
- Archive larger than active content
- Cross-references becoming tangled
- Team reports difficulty finding things
```

### Content Triggers
```markdown
## Content Smell Indicators

### Redundancy Smells
- "See also [same 5 links]" repeatedly
- Copy-pasted sections across files
- Multiple versions of same framework
- Overlapping decision records

### Obsolescence Smells  
- References to abandoned features
- Planning for canceled milestones
- Superseded technical approaches
- Outdated team structures

### Confusion Smells
- Conflicting information
- Unclear ownership
- Mixed abstraction levels
- Circular dependencies
```

## Pruning Strategies

### 1. Consolidation Pattern
```markdown
## Consolidating Related Content

### Before: Multiple Character Voice Files
characters/
├── marcus-voice-notes.md
├── marcus-speech-patterns.md  
├── marcus-dialogue-guide.md
├── marcus-voice-evolution.md

### After: Single Comprehensive File
characters/
├── marcus-voice.md (consolidated)
archive/2024-01/
├── consolidation-note.md
├── marcus-voice-notes.md (original)
├── marcus-speech-patterns.md (original)
```

### 2. Extraction Pattern
```markdown
## Extracting Reusable Components

### Before: Monolithic Planning Doc
planning/story-plan.md (800 lines)
- Project goals
- Character summaries  
- World building rules
- Plot outlines
- Theme exploration
- Technical notes

### After: Focused Documents
planning/
├── goals.md (50 lines)
├── timeline.md (75 lines)
characters/
├── roster.md (100 lines)
world/
├── rules.md (150 lines)
elements/
├── themes.md (100 lines)
```

### 3. Archive-with-Context Pattern
```markdown
## Archiving with Rationale

### Archive Entry Template
archive/2024-01-plot-restructure/
├── README.md
├── original-structure/
│   ├── [moved files]

### README.md Content:
# Archive: Plot Restructure 2024-01

## Date Archived: 2024-01-15

## Reason
Major plot restructure after beta feedback made this approach obsolete.

## What This Contains
- Original three-timeline structure
- Character backstories for removed subplot
- World-building for abandoned locations

## Key Decisions Preserved
- Why we initially chose three timelines
- What feedback changed our minds
- How new structure addresses issues

## Lessons Learned
- Complex timeline structures need clear markers
- Beta readers value straightforward chronology
- Flashbacks work better than parallel timelines
```

## Pruning Workflow

### Phase 1: Analysis
```bash
#!/bin/bash
# analyze-for-pruning.sh

echo "=== Large Files (>300 lines) ==="
find context-network -name "*.md" -exec wc -l {} \; | 
awk '$1 > 300 {print $2 " (" $1 " lines)"}' | sort -nr

echo -e "\n=== Rarely Accessed (>30 days) ==="
find context-network -name "*.md" -atime +30 -type f

echo -e "\n=== Potential Duplicates ==="
# Find files with similar names
find context-network -name "*.md" | 
awk -F/ '{print $NF}' | sort | uniq -d

echo -e "\n=== Broken Links ==="
bash check-broken-links.sh
```

### Phase 2: Planning
```markdown
## Pruning Plan Template

### Round: [Date]

#### Consolidation Targets
- [ ] Merge: voice-patterns.md + dialogue-guide.md → character-voice.md
- [ ] Merge: world-rules-*.md → unified world-rules.md

#### Extraction Targets  
- [ ] Split: massive-planning.md → goals.md, phases.md, metrics.md
- [ ] Split: character-everything.md → individual character files

#### Archive Targets
- [ ] Obsolete: old-magic-system.md (replaced by new-magic-system.md)
- [ ] Completed: beta-round-1-tasks.md (all tasks done)

#### Deletion Targets (Rare)
- [ ] Empty: placeholder-*.md files with no content
- [ ] Broken: corrupted files that can't be recovered
```

### Phase 3: Execution
```markdown
## Pruning Execution Checklist

### Pre-Pruning
- [ ] Create pruning branch
- [ ] Full backup of context-network
- [ ] Document pruning rationale
- [ ] Notify team of planned changes

### During Pruning
- [ ] Move files to archive with context
- [ ] Update all affected links
- [ ] Consolidate content carefully
- [ ] Preserve decision history

### Post-Pruning  
- [ ] Run link checker
- [ ] Verify navigation paths
- [ ] Update index files
- [ ] Test key workflows
- [ ] Commit with detailed message
```

## Pruning Patterns by Type

### Character Document Pruning
```markdown
## Character Consolidation

### Indicators
- Multiple files per character
- Overlapping information
- Inconsistent updates

### Strategy
1. Create comprehensive character doc
2. Extract voice → voice-consistency.md
3. Extract relationships → relationships.md
4. Archive original fragments

### Result
- One source of truth per character
- Specialized docs for cross-character patterns
- Clear update locations
```

### Plot Document Pruning
```markdown
## Plot Structure Cleanup

### Indicators  
- Abandoned subplot threads
- Multiple outline versions
- Mixed planning and analysis

### Strategy
1. Separate active vs abandoned plots
2. Create plot-archive/ for old versions
3. Extract analysis to discoveries/
4. Maintain single active outline

### Result
- Current plot clearly visible
- History preserved but separated
- Analysis linked but not inline
```

## Anti-Patterns to Avoid

### ❌ Over-Pruning
- Deleting "failed" experiments (keep for lessons)
- Removing all historical context
- Consolidating unlike things
- Pruning during active development

### ❌ Under-Pruning  
- Keeping everything forever
- Never consolidating related content
- Avoiding archive decisions
- Letting network grow unbounded

### ❌ Context Loss
- Archiving without explanation
- Breaking links without redirects
- Losing decision rationale
- Removing discovery paths

## Success Metrics

### Good Pruning Results
- **Before**: 10 clicks to find character voice info
- **After**: 2 clicks through clear path

- **Before**: 5 files with partial world rules  
- **After**: 1 comprehensive file with sections

- **Before**: 300+ nodes, unclear structure
- **After**: 150 nodes, clear categories

### Health Indicators
```bash
# Quick health check after pruning
echo "Active nodes: $(find context-network -name "*.md" -not -path "*/archive/*" | wc -l)"
echo "Archive nodes: $(find context-network/archive -name "*.md" | wc -l)"
echo "Broken links: $(bash check-links.sh | wc -l)"
echo "Average file size: $(find context-network -name "*.md" -exec wc -l {} \; | awk '{sum+=$1; count++} END {print sum/count " lines"}')"
```

## Relationships
- Part of: [[network_maintenance]]
- Uses: [[archive_strategy]], [[consolidation_patterns]]
- Prevents: [[navigation_breakdown]], [[information_overload]]
- Enables: [[sustainable_growth]], [[team_efficiency]]