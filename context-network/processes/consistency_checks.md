# Consistency Checks Process

## Classification
- **Domain**: Quality Assurance
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Define systematic approaches to finding and fixing inconsistencies across manuscripts and context network.

## Automated Consistency Checks

### Name Consistency
```bash
#!/bin/bash
# check-names.sh - Find potential name inconsistencies

echo "=== Checking Character Names ==="

# Extract all capitalized words that might be names
grep -h -o '\b[A-Z][a-z]\+\b' manuscripts/*.md | sort | uniq -c | sort -nr > tmp_names.txt

# Find similar names (potential typos)
while read count name; do
  if [ $count -lt 5 ]; then  # Names appearing less than 5 times might be typos
    echo "Rare name: $name (appears $count times)"
    # Find similar names
    grep -h -o '\b[A-Z][a-z]\+\b' manuscripts/*.md | sort | uniq | 
    while read other; do
      if [ "$name" != "$other" ] && [ ${#name} -eq ${#other} ]; then
        # Simple similarity check (same length)
        similarity=$(comm -12 <(echo $name | grep -o . | sort) <(echo $other | grep -o . | sort) | wc -l)
        if [ $similarity -gt $((${#name} - 2)) ]; then
          echo "  Possible typo? Similar to: $other"
        fi
      fi
    done
  fi
done < tmp_names.txt

rm tmp_names.txt
```

### Timeline Consistency
```bash
#!/bin/bash
# check-timeline.sh - Verify timeline references

echo "=== Timeline Consistency Check ==="

# Find all time references
echo "Day references:"
grep -n -h "day\|Day\|morning\|afternoon\|evening\|night" manuscripts/*.md | 
grep -E "(first|second|third|next|previous|yesterday|tomorrow)" > timeline_refs.txt

# Check specific problem patterns
echo -e "\nPotential issues:"

# Look for "yesterday" followed by multiple day gap
grep -B2 -A2 "yesterday" manuscripts/*.md | grep -E "(three days|week|days ago)"

# Find conflicting moon phases
echo -e "\nMoon phase references:"
grep -n "moon\|Moon" manuscripts/*.md | grep -E "(full|new|crescent|quarter)"

# Check season references
echo -e "\nSeason references:"
grep -n -E "(spring|summer|autumn|fall|winter|Spring|Summer|Autumn|Fall|Winter)" manuscripts/*.md
```

### World Rule Validation
```markdown
## World Consistency Audit

### Magic System Rules
1. **Rule**: Magic requires physical gesture
   - **Check**: Search for magic use without gesture mention
   ```bash
   grep -B2 -A2 -E "(cast|spell|magic)" manuscripts/*.md | 
   grep -v -E "(gesture|hand|finger|movement)"
   ```

2. **Rule**: Teleportation limited to line of sight
   - **Check**: Find teleportation scenes
   ```bash
   grep -B5 -A5 -E "(teleport|vanish|appear)" manuscripts/*.md
   ```

### Cultural Rules
1. **Rule**: Northern culture uses patronymics
   - **Check**: Verify northern character names
   ```bash
   grep -E "(son|dottir|sson|ovna)" manuscripts/*.md
   ```
```

## Manual Consistency Workflows

### Character Appearance Tracking
```markdown
## Character Physical Description Audit

### Process
1. Extract all physical descriptions per character
2. Create reference sheet
3. Check each subsequent mention

### Reference Template
| Character | Hair | Eyes | Height | Distinctive | First Mention |
|-----------|------|------|---------|-------------|---------------|
| Marcus | Black, short | Gray | Tall | Scar on left cheek | ch01.md:45 |
| Elena | Red, braided | Green | Average | Freckles | ch02.md:123 |

### Verification Checklist
- [ ] Hair color consistent
- [ ] Eye color never changes
- [ ] Height relationships maintained
- [ ] Scars/marks in correct location
- [ ] Clothing style fits character
```

### Relationship Dynamics
```markdown
## Relationship Consistency Matrix

### Character Relationship Status
| Ch | Marcus→Elena | Elena→Marcus | Evidence |
|----|--------------|--------------|-----------|
| 1 | Distrust | Curiosity | "stepped back" ch01:234 |
| 3 | Respect | Interest | "nodded slowly" ch03:456 |
| 5 | Trust | Affection | "reached for her hand" ch05:789 |
| 7 | Love | Love | "couldn't imagine life without" ch07:012 |

### Validation Points
- [ ] No relationship jumps without development
- [ ] Both characters progress logically
- [ ] Physical interactions match emotional state
- [ ] Dialogue reflects relationship stage
```

## Discovery-Based Consistency

### Pattern Recognition
```markdown
## Discovered Patterns Log

### Speech Patterns
- **Pattern**: Character X always says "you know" when nervous
- **Violations Found**: Ch7, Ch12 (missing during stress scenes)
- **Resolution**: Add back for consistency

### Behavioral Patterns  
- **Pattern**: Character Y touches weapon when threatened
- **Violations Found**: Ch9 confrontation (no mention)
- **Resolution**: Add gesture or explain why not
```

### Cross-Reference Validation
```bash
#!/bin/bash
# validate-cross-refs.sh - Check context network references

echo "=== Checking Manuscript References in Context Network ==="

# Find all manuscript references in context network
grep -r "manuscripts/" context-network/ | while read line; do
  file=$(echo $line | grep -o 'manuscripts/[^:]*')
  if [ ! -f "$file" ]; then
    echo "Missing file: $file"
    echo "  Referenced in: $(echo $line | cut -d: -f1)"
  fi
done

# Find broken line number references
grep -r "manuscripts/.*:[0-9]" context-network/ | while read line; do
  ref=$(echo $line | grep -o 'manuscripts/[^:]*:[0-9-]*')
  file=$(echo $ref | cut -d: -f1)
  lines=$(echo $ref | cut -d: -f2)
  
  if [ -f "$file" ]; then
    total_lines=$(wc -l < "$file")
    end_line=$(echo $lines | cut -d- -f2)
    if [ $end_line -gt $total_lines ]; then
      echo "Line reference out of range: $ref (file has $total_lines lines)"
    fi
  fi
done
```

## Consistency Report Generation

### Automated Report
```markdown
# Consistency Check Report - [Date]

## Automated Checks
- Name consistency: [X issues found]
- Timeline validation: [X conflicts identified]  
- World rules: [X violations detected]

## Manual Reviews Needed
1. Character descriptions in Ch7-9
2. Relationship progression Ch10-12
3. Magic system usage Ch5

## Priority Fixes
1. **Critical**: Timeline impossibility Ch8-9
2. **High**: Character name variation (Marcus/Marc)
3. **Medium**: Moon phase conflicts
4. **Low**: Dialogue tag variety

## Next Steps
- [ ] Fix critical issues
- [ ] Update context network
- [ ] Run verification pass
- [ ] Update style guide
```

## Integration Patterns

### With Revision Process
- Run before each revision stage
- Focus checks based on revision type
- Update context network with findings

### With Version Control
```bash
# Pre-commit hook for basic checks
#!/bin/bash
# .git/hooks/pre-commit

# Check for common issues
if grep -r "TODO\|FIXME\|XXX" manuscripts/; then
  echo "Warning: Unresolved TODOs found"
fi

if grep -r "\s\s" manuscripts/; then
  echo "Warning: Double spaces found"
fi
```

## Relationships
- Supports: [[revision_cycles]], [[validation]]
- Uses: [[manuscripts/tracking/consistency]]
- Integrates with: [[characters/voice_consistency]]
- Enables: [[quality_assurance]]