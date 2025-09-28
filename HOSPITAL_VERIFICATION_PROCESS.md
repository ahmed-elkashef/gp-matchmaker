# GP MatchMaker - Hospital Verification Process

## Overview
Systematic verification of hospital training locations for each GP scheme rank with official sources and documentation.

## Step-by-Step Process

### 1. Select Next Rank
- Work through ranks sequentially (1, 2, 3, etc.)
- Focus on one rank at a time for accuracy

### 2. Research Official Sources
Search for **OFFICIAL** documentation only:
- NHS Deanery websites (e.g., yorksandhumberdeanery.nhs.uk)
- Official NHS Trust websites
- Health Education England documentation
- Medical school GP training pages

**Required for each hospital:**
- Hospital name
- Full address with postcode
- Official source URL where this is documented
- Confirmation it's specifically for GP training (not just any hospital in the area)

### 3. Verification Criteria
**INCLUDE hospitals only if:**
- Found on official NHS/Deanery website
- Explicitly mentioned as GP training placement site
- Have verifiable source URL

**EXCLUDE hospitals if:**
- No official source found
- Only geographic proximity (not confirmed training site)
- Speculation or unofficial information

### 4. Update HTML Data
Add hospitals with this format:
```javascript
{
    name: "Hospital Name",
    address: "Full Address, Postcode",
    maps: "Google Maps URL",
    source: "Official Source URL",
    verified: true
}
```

**For schemes that cannot be verified:**
```javascript
{
    name: "Hospital Name",
    address: "Full Address, Postcode",
    maps: "Google Maps URL",
    note: "Research found: [brief summary of findings and why verification failed]"
    // No source or verified fields - will show as UNVERIFIED
}
```

### 5. UI Display
- ✅ VERIFIED hospitals: Green border, source link
- ⚠️ UNVERIFIED hospitals: Yellow border, no source
- ℹ️ Research Notes: Shows when `note` field exists, hover for details

### 6. Handling Unverifiable Schemes
When a scheme cannot be verified despite thorough searching:

1. **Document the research effort**: Add comprehensive searches performed
2. **Add research notes**: Include findings in `note` field with format:
   - "Research found: [what was discovered]"
   - "But no official source found specifying [specific need]"
3. **Update comment**: Mark scheme as "UNVERIFIED (no official source found)"
4. **Continue systematically**: Don't skip, document and move to next rank

### 7. Quality Control
- Double-check source URLs are accessible
- Verify information matches official documentation
- Mark rank as complete in todo list

### 8. Progress Tracking
- Update todo list after each rank
- Note any schemes where no official sources found
- Continue systematically through all 161 ranks

### 9. Scheme Name Consistency Check
**CRITICAL**: After verifying hospitals, check scheme name descriptiveness:

**Problem Identified**: Some scheme names lack detail compared to others
- ❌ **Inconsistent**: "Bath", "Bristol", "Derby" (too brief)
- ✅ **Consistent**: "Yorkshire and the Humber - West - Leeds GP Scheme" (detailed)

**Solution Process**:
1. **Compare naming patterns** across regions
2. **Identify less descriptive schemes** (usually single city names)
3. **Enhance scheme names** to match detailed patterns:
   - Add "GP Training Scheme" suffix
   - Include county/area information in `area` field
   - Maintain regional consistency

**Example Enhancement**:
```javascript
// BEFORE (less descriptive)
{rank: 67, region: "South West", area: "", scheme: "Bath", start: "Aug", places: 0}

// AFTER (consistent detail)
{rank: 67, region: "South West", area: "Somerset", scheme: "Bath GP Training Scheme", start: "Aug", places: 0}
```

**Regions to Check for Consistency**:
- South West schemes (often too brief)
- East Midlands schemes (missing area information)
- Single-word scheme names across all regions

**When to Apply**:
- After completing hospital verification for a batch of 10+ ranks
- When scheme names appear inconsistent with established patterns
- Before committing major verification milestones

## Current Status
- Ranks 1-80: ✅ Complete - All hospitals verified and scheme names enhanced
- Ranks 81+: Pending verification

## Important Notes
- **Quality over speed** - better to have fewer verified hospitals than many unverified
- **Official sources only** - no guessing or assumption
- **Document everything** - always include source URLs
- **Be systematic** - don't skip ranks or work out of order
- **Maintain consistency** - ensure all scheme names follow similar descriptive patterns