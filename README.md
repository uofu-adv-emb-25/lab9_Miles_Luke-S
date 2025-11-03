## Invariants
1. An approach signal will always precede a depart signal
2. The power will never be interrupted
3. Trains on each track only run in one direction
4. There will be no mechanical or electrical failures
5. Trains will never reach the crossing before the gate has lowered
6. The gates will always be lowered when a train is in the crossing
7. The alarm will always be on when a train is present
8. A timer emits an event elasped 10 seconds after the alarm starts ringing

## Varying Invariants
#### Does there exist a sequence of events, such that an invariant is no longer true?
In a real world situation, there are numerous sequences of events that cause our established invariants to no longer be true. For example, a speeding train could be going fast enough to reach the gate before it has completely lowered. 

#### Counter-Example Sequence
If both a southbound and northbound train approach, the alarm starts, the gate lowers, and then only the southbound train departs, the northbound train may still be on the tracks. This makes invariant 6 false.

## Checking FSMs
In Miles's FSM, once the system has entered the Alarm Startup state, if a train approaches the same instant that the elapsed signal occurs, there are multiple conditions met simultaneously. This could cause an error in logic and a disruption to the system's state. 
One fix to this could be adding more state transitions from Alarm Startup to Barrier Lowered that account for both the elapsed and train arrival signals. Alternatively, we could state assumptions for how the system would behave in this case. We could, for example, define a priority determining which transition take precedence over others.

## Proving the Model Correct
| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | time elasped | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|--------------|---------------|
| 0      | 0         | 0        | 0                  | 0                  | 6              | 5              | 16           | 16           | 23           | 16, 23        |
| 1      | 0         | 0        | 0                  | 1                  |                |                |              |              |              | 21, 22        |
| 2      | 0         | 0        | 1                  | 0                  |                |                |              |              |              | 21, 22        |
| 3      | 0         | 0        | 1                  | 1                  |                |                |              |              |              | 21, 22        |
| 4      | 0         | 1        | 0                  | 0                  | 6              | 5              | 16           | 16           | 0            | 16            |
| 5      | 0         | 1        | 0                  | 1                  | 7              | 16             | 16           | 20           | 13           | 16, 20        |
| 6      | 0         | 1        | 1                  | 0                  | 16             | 7              | 20           | 16           | 14           | 16, 20        |
| 7      | 0         | 1        | 1                  | 1                  | 16             | 16             | 20           | 20           | 15           | 16, 20        |
| 8      | 1         | 0        | 0                  | 0                  |                |                |              |              |              | 21            |
| 9      | 1         | 0        | 0                  | 1                  |                |                |              |              |              | 22            |
| 10     | 1         | 0        | 1                  | 0                  |                |                |              |              |              | 22            |
| 11     | 1         | 0        | 1                  | 1                  |                |                |              |              |              | 22            |
| 12     | 1         | 1        | 0                  | 0                  |                |                |              |              |              | 21            |
| 13     | 1         | 1        | 0                  | 1                  | 15             |                |              |              |              |               |
| 14     | 1         | 1        | 1                  | 0                  |                |                |              |              |              |               |
| 15     | 1         | 1        | 1                  | 1                  |                |                |              |              |              |               |

| number | invariant |
|--------|-----------|
| 16     | An approach signal will always precede a depart signal |
| 17     | The power will never be interrupted |
| 18     | Trains on each track only run in one direction |
| 19     | There will be no mechanical or electrical failures |
| 20     | Trains will never reach the crossing before the gate has lowered |
| 21     | The gates are only lowered when a train is in the crossing |
| 22     | The alarm will always be on when a train is present |
| 23     | A timer emits an event elasped 10 seconds after the alarm starts ringing|