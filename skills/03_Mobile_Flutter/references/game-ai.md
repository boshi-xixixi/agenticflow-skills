# Flutter Game AI Patterns

This document outlines patterns for implementing AI in Flutter games (e.g., using Flame engine).

## 1. AI Architecture

```
Game Loop -> Update State -> AI Decision -> Execute Action
```

## 2. Core Components

### A. Finite State Machine (FSM)
Used for simple NPC behaviors (Idle, Patrol, Chase, Attack).

```dart
enum NPCState { idle, patrol, chase, attack }

class NPC extends Component {
  NPCState state = NPCState.idle;

  void update(double dt) {
    switch (state) {
      case NPCState.idle:
        // Check for player visibility
        if (canSeePlayer()) state = NPCState.chase;
        break;
      case NPCState.chase:
        moveTowardsPlayer();
        if (distanceToPlayer() < attackRange) state = NPCState.attack;
        break;
      // ...
    }
  }
}
```

### B. Behavior Trees
Used for complex decision making.

- **Selector**: Tries children until one succeeds (e.g., "Protect Self" OR "Attack").
- **Sequence**: Runs children in order (e.g., "Find Cover" AND "Reload").

### C. A* Pathfinding
Used for navigating complex maps.
