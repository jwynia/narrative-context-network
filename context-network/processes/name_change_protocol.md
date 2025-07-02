# Name Change Protocol

## Classification
- **Domain**: Technical/Editorial
- **Stability**: Stable
- **Abstraction**: Concrete
- **Confidence**: High

## Purpose
Define systematic approach for changing character, location, or concept names throughout manuscripts and context network.

## Pre-Change Checklist

### Impact Assessment
```markdown
## Name Change Impact Analysis

### Target: [Old Name] → [New Name]

#### Scope Check
- [ ] Character name (first, last, nicknames)
- [ ] Location name (city, region, landmarks)  
- [ ] Concept name (organizations, items, terms)

#### Usage Audit
```bash
# Count occurrences
echo "Manuscript occurrences:"
grep -c "Old Name" manuscripts/*.md | grep -v ":0"

echo "Context network occurrences:"
grep -r -c "Old Name" context-network/ | grep -v ":0"

echo "Variant checks:"
grep -c -i "oldname\|Old Name\|OldName" manuscripts/*.md
```

#### Relationship Check
- [ ] Possessive forms (Old Name's)
- [ ] Dialogue references ("call me Old")
- [ ] Nicknames/shortened forms
- [ ] Related names (family, derivatives)
```

## Implementation Process

### Step 1: Create Change Branch
```bash
git checkout -b rename/oldname-to-newname
git status # Ensure clean working directory
```

### Step 2: Systematic Replacement

#### Automated Base Replacement
```bash
#!/bin/bash
# rename-character.sh

OLD_NAME="$1"
NEW_NAME="$2"

# Backup first
cp -r manuscripts manuscripts.backup
cp -r context-network context-network.backup

# Replace in manuscripts
find manuscripts -name "*.md" -type f -exec sed -i '' "s/\b${OLD_NAME}\b/${NEW_NAME}/g" {} \;
find manuscripts -name "*.md" -type f -exec sed -i '' "s/\b${OLD_NAME}'s\b/${NEW_NAME}'s/g" {} \;

# Replace in context network  
find context-network -name "*.md" -type f -exec sed -i '' "s/\b${OLD_NAME}\b/${NEW_NAME}/g" {} \;
find context-network -name "*.md" -type f -exec sed -i '' "s/\b${OLD_NAME}'s\b/${NEW_NAME}'s/g" {} \;

echo "Base replacement complete. Manual review required."
```

#### Manual Review Points
```markdown
## Manual Review Checklist

### Dialogue Variations
- [ ] Check informal usage ("Hey, Old!")
- [ ] Verify nicknames consistency
- [ ] Update character voice docs

### Context-Sensitive Usage
- [ ] Chapter titles
- [ ] File names
- [ ] Metadata references
- [ ] Index entries

### Edge Cases
- [ ] Partial matches avoided
- [ ] Compound words handled
- [ ] Case variations caught
```

### Step 3: Validation

#### Consistency Check
```bash
# Verify complete replacement
echo "Remaining old name instances:"
grep -r "$OLD_NAME" manuscripts/ context-network/

# Check for broken patterns
echo "Potential issues:"
grep -r "${NEW_NAME}${NEW_NAME}" manuscripts/  # Double replacement
grep -r "[^A-Za-z]${NEW_NAME}[A-Z]" manuscripts/  # Mid-word replacement
```

#### Read-Through Validation
```markdown
## Read-Through Checklist

### Critical Scenes
- [ ] First appearance
- [ ] Major dialogue scenes
- [ ] Emotional moments
- [ ] Name revelation scenes

### Flow Check
- [ ] Dialogue sounds natural
- [ ] Narration flows smoothly
- [ ] No jarring transitions
- [ ] Nicknames make sense
```

### Step 4: Context Network Updates

#### Update Documentation
```markdown
## Context Network Updates

### Character Node
- [ ] Update main character file name
- [ ] Fix all internal references
- [ ] Update relationship files
- [ ] Revise character arc docs

### Decision Record
- [ ] Create decision record for name change
- [ ] Document rationale
- [ ] Note implementation date
- [ ] Link to relevant discussion
```

#### Create Decision Record
```markdown
# Decision: Rename [Old Name] to [New Name]

## Date: YYYY-MM-DD

## Decision
Change character name from "[Old Name]" to "[New Name]" throughout all materials.

## Rationale
- [Primary reason - e.g., cultural authenticity]
- [Secondary reason - e.g., avoid confusion with other character]
- [Additional factors]

## Implementation
- Scope: All manuscripts and documentation
- Method: Automated replacement + manual review
- Verification: Read-through of key scenes

## Impacts
- No plot changes required
- Minor dialogue adjustments for flow
- Update marketing materials if any

## Rollback Plan
If issues discovered:
```bash
git checkout manuscripts
git checkout context-network
```
```

### Step 5: Commit and Tag

```bash
# Commit changes
git add -A
git commit -m "Global rename: ${OLD_NAME} -> ${NEW_NAME} throughout manuscripts and context network

- Updated all character references
- Adjusted dialogue for natural flow  
- Updated context network documentation
- Verified consistency across all files

Ref: decisions/rename-oldname-newname"

# Tag for easy reference
git tag rename-${OLD_NAME,,}-to-${NEW_NAME,,}
```

## Common Patterns

### Character Name Types

#### Simple First Name
```bash
sed -i '' "s/\bJohn\b/James/g" manuscripts/*.md
sed -i '' "s/\bJohn's\b/James's/g" manuscripts/*.md
```

#### Full Name Change
```bash
# Handle variations
sed -i '' "s/\bJohn Smith\b/James Wilson/g" manuscripts/*.md
sed -i '' "s/\bJohn\b/James/g" manuscripts/*.md  
sed -i '' "s/\bSmith\b/Wilson/g" manuscripts/*.md
sed -i '' "s/\bMr\. Smith\b/Mr. Wilson/g" manuscripts/*.md
```

#### Nickname Preservation
```markdown
## Nickname Mapping
- Old: John → Johnny, Jack
- New: James → Jamie, Jim

Note: Update nicknames for consistency or preserve for character history
```

### Location Names

#### City/Place Names
```bash
# Include prepositions
sed -i '' "s/\bOldton\b/Newville/g" manuscripts/*.md
sed -i '' "s/\bto Oldton\b/to Newville/g" manuscripts/*.md
sed -i '' "s/\bfrom Oldton\b/from Newville/g" manuscripts/*.md
sed -i '' "s/\bof Oldton\b/of Newville/g" manuscripts/*.md
```

## Rollback Procedures

### Quick Rollback
```bash
# If immediately discovered issue
git reset --hard HEAD~1
git tag -d rename-${OLD_NAME,,}-to-${NEW_NAME,,}
```

### Selective Rollback
```bash
# If only certain files need reverting
git checkout HEAD~1 -- manuscripts/chapter3.md
git checkout HEAD~1 -- context-network/characters/oldname.md
```

## Post-Change Verification

### Quality Checks
1. **Flow Test**: Read aloud key dialogue scenes
2. **Search Test**: Ensure old name fully removed
3. **Cross-Reference**: Verify context network consistency
4. **Beta Test**: Have someone read changed chapters

### Documentation Updates
- [ ] Update style guide with new name
- [ ] Add to project glossary
- [ ] Update character reference sheet
- [ ] Note in revision history

## Relationships
- Uses: [[consistency_checks]], [[version_control]]
- Supports: [[revision_cycles]], [[delivery]]
- Creates: [[decisions/]], [[changes]]
- Part of: [[editorial_workflow]]