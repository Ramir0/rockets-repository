# rockets-repository 
Coding Exercise: Dragon Rockets Repository

# Analysis

## Core Entities

### Rocket
- **Properties**: `id`, `name`, `status`
- **Statuses**:
    - `On ground` (initial status)
    - `In space`
    - `In repair`

### Mission
- **Properties**: `id`, `name`, `status`, `rockets`
- **Statuses**:
    - `Scheduled` (initial status)
    - `Pending`
    - `In Progress`
    - `Ended`
- **Constraints**:
    - Can have multiple rockets

## Operations

- Add a new rocket
- Assign rockets to a mission
- Change rocket status
- Add a new mission
- Change mission status
- Get a summary of missions

## Business Rules

### Rocket Assignment
- Rocket can be assigned only to one mission at a time

### Mission Status Logic
- **Scheduled**: Initial status, no rockets assigned
- **Pending**: At least one rocket assigned and one or more assigned rockets are in repair
- **In Progress**: At least one rocket is assigned and none of them is in repair
- **Ended**: Final stage, rockets should not be assigned anymore

### Rocket Status Effects
- **In repair**: Implies mission status becomes 'Pending'

### Summary Sorting
- Sorting missions by number of assigned rockets
- Missions with the same number of rockets ordered in descending alphabetical order

## Edge Cases

- Assigning rocket to a mission when rocket is already assigned
- Assigning rockets to an ended mission
- Removing rockets from a mission when ended
- Null/invalid inputs
- Mission status transitions that shouldn't be allowed
(i.e. From Pending to In Progress when rockets are in repair)
