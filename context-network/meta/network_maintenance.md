# Context Network Maintenance Guide

## Classification
- **Domain**: Meta/System
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Define practices for keeping the context network healthy, navigable, and valuable throughout the project lifecycle.

## Maintenance Principles

### 1. Living Documentation
- The network evolves with the project
- Outdated information gets archived, not deleted
- Changes are tracked and justified
- Regular reviews prevent drift

### 2. Signal vs Noise
- Every node must provide value
- Consolidate overlapping content
- Remove speculation that didn't pan out
- Keep decision rationale even if overturned

### 3. Navigation First
- Maintain clear pathways between related content
- Update indexes when structure changes
- Fix broken links immediately
- Create hubs for complex topics

## Regular Maintenance Tasks

### Daily (During Active Work)
```markdown
## Daily Maintenance Checklist
- [ ] Update task progress in active nodes
- [ ] Create discoveries as they occur
- [ ] Fix any broken links you encounter
- [ ] Update location references after major edits
```

### Weekly Review
```markdown
## Weekly Network Health Check

### Navigation Test
- [ ] Start from README, reach any major node in 3 clicks
- [ ] Verify index files reflect current structure
- [ ] Check for orphaned nodes (no incoming links)

### Content Freshness
- [ ] Archive completed task nodes
- [ ] Update progress markers
- [ ] Consolidate similar discoveries
- [ ] Tag nodes needing review

### Link Integrity
```bash
# Find broken internal links
find context-network -name "*.md" -exec grep -l "\[\[.*\]\]" {} \; | 
while read file; do
  grep -o "\[\[[^]]*\]\]" "$file" | 
  while read link; do
    target=$(echo "$link" | sed 's/\[\[\(.*\)\]\]/\1/')
    if ! find context-network -name "${target}.md" | grep -q .; then
      echo "Broken link in $file: $link"
    fi
  done
done
```
```

### Monthly Deep Clean
```markdown
## Monthly Maintenance Protocol

### Structure Optimization
1. **Identify Growth Areas**
   - Which folders are getting too large?
   - What new categories have emerged?
   - Where is navigation becoming difficult?

2. **Reorganize if Needed**
   - Create new subcategories
   - Split large documents
   - Consolidate sparse areas
   - Update all affected links

### Content Audit
1. **Review Node Classifications**
   - Update stability levels
   - Adjust confidence ratings
   - Revise domain assignments

2. **Archive Obsolete Content**
   - Move abandoned approaches to archive/
   - Keep with explanation of why abandoned
   - Maintain historical decision trail

### Pattern Recognition
- Review all discoveries for patterns
- Promote patterns to frameworks
- Update existing frameworks with new insights
- Create new guides from repeated solutions
```

## Archival Strategy

### When to Archive
```markdown
## Archive Triggers

### Immediate Archive
- Experimental approaches that failed
- Outdated plot threads (with reason)
- Superseded character versions
- Completed task records

### Delayed Archive (After Milestone)
- Beta feedback from previous round
- Early draft world-building
- Abandoned subplots
- Initial character concepts

### Never Archive
- Decision records (even if overturned)
- Discovery logs
- Framework evolution history
- Core principles
```

### Archive Structure
```
archive/
├── date-archived/
│   ├── context.md (why archived)
│   ├── [archived files]
├── experiments/
│   ├── failed/
│   ├── superseded/
├── old-versions/
│   ├── characters/
│   ├── plot/
│   ├── world/
```

## Node Lifecycle Management

### Node States
```markdown
## Node Status Indicators

### 🟢 Active
- Currently being updated
- Central to active work
- Frequently referenced

### 🟡 Stable
- Complete for now
- Referenced but not edited
- May need updates later

### 🔵 Reference
- Historical information
- Kept for context
- Not expected to change

### ⚫ Archived
- No longer relevant
- Kept for history
- Moved to archive/
```

### State Transitions
```mermaid
graph LR
    A[Created] --> B[Active]
    B --> C[Stable]
    C --> B
    C --> D[Reference]
    D --> E[Archived]
    B --> E
```

## Common Maintenance Patterns

### Discovery Consolidation
```markdown
## When You Have Multiple Similar Discoveries

1. **Pattern Recognition**
   - Review discoveries/ folder
   - Identify recurring themes
   - Group related insights

2. **Framework Creation**
   - Extract common principles
   - Create new framework node
   - Link discoveries as examples

3. **Discovery Cleanup**
   - Keep specific examples
   - Archive redundant ones
   - Update links to framework
```

### Index Regeneration
```bash
#!/bin/bash
# regenerate-index.sh - Rebuild index files

FOLDER=$1
INDEX_FILE="$FOLDER/index.md"

echo "# Index: $(basename $FOLDER)" > $INDEX_FILE
echo "" >> $INDEX_FILE
echo "## Documents" >> $INDEX_FILE
echo "" >> $INDEX_FILE

find $FOLDER -name "*.md" -not -name "index.md" | sort | while read file; do
  title=$(grep "^# " "$file" | head -1 | sed 's/# //')
  relative=$(echo $file | sed "s|$FOLDER/||")
  echo "- [$title]($relative)" >> $INDEX_FILE
done
```

### Link Fixing Workflow
```markdown
## Broken Link Resolution

1. **Identify broken link**
   - Note source file
   - Note intended target

2. **Determine fix type**
   - Typo: Fix spelling
   - Moved: Update path
   - Deleted: Remove or archive

3. **Global fix if needed**
   ```bash
   # Fix all instances of broken link
   find context-network -name "*.md" -exec sed -i '' 's/\[\[old-path\]\]/\[\[new-path\]\]/g' {} \;
   ```

4. **Verify fix**
   - Check link works
   - Ensure meaning preserved
   - Update related links
```

## Health Metrics

### Good Network Signs
- Can find any information quickly
- Clear evolution of ideas visible
- Decisions have rationale
- Discoveries lead to improvements
- Navigation feels intuitive

### Warning Signs
- Same information in multiple places
- Difficulty finding specific content
- Broken links accumulating
- Folders becoming unwieldy
- Index files outdated

### Critical Issues
- Core information lost
- Navigation completely broken
- Merge conflicts unresolved
- Archive larger than active
- Team confusion about structure

## Maintenance Tools

### Network Statistics
```bash
#!/bin/bash
# network-stats.sh - Context network health metrics

echo "=== Context Network Statistics ==="
echo "Total nodes: $(find context-network -name "*.md" | wc -l)"
echo "Active modifications (last 7 days): $(find context-network -name "*.md" -mtime -7 | wc -l)"
echo "Archive size: $(find context-network/archive -name "*.md" 2>/dev/null | wc -l)"
echo "Broken links: $(bash check-links.sh | wc -l)"
echo ""
echo "=== Largest Folders ==="
for dir in $(find context-network -type d -not -path "*/\.*"); do
  count=$(find "$dir" -maxdepth 1 -name "*.md" | wc -l)
  if [ $count -gt 10 ]; then
    echo "$dir: $count files"
  fi
done
```

## Relationships
- Maintains: [[All network nodes]]
- Uses: [[node_template]], [[structure]]
- Supports: [[enhancement_guide]], [[maintenance]]
- Enables: [[Long-term project health]]