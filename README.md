## Invariants
1. An approach signal will always precede a depart signal
2. The power will never be interrupted
3. Trains on each track only run in one direction
4. There will be no mechanical or electrical failures
5. Trains will never reach the crossing before the gate has lowered
6. The gates will always be lowered when a train is in the crossing


## Varying Invariants
#### Does there exist a sequence of events, such that an invariant is no longer true?
In a real world situation, there are numerous sequences of events that cause our setablished invariants to no longer be true. For example, a speeding train could be going fast enough to reach the gate before it has completely lowered. 

#### Counter-Example Sequence
If both a southbound and northbound train approach, the alarm starts, the gate lowers, and then only the southbound train departs, the northbound train may still be on the tracks. This makes invariant 6 false.