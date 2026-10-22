
# Black-Box Testing Practice: ESPN


## Step 1: Select a Website

**Website name:** ESPN

**URL:** https://www.espn.com/

**Features to test:**
1. Searching for a sports team or player.
2. Signing in to an ESPN account.

## Step 2: Equivalence Partitioning

**Feature:** Searching for a sports team or player.

| Partition | Type | Test Input | Expected Result |
|---|---|---|---|
| Team name | Valid | Seattle Seahawks | Relevant team results |
| Player name | Valid | Patrick Mahomes | Relevant player results |
| Partial name | Valid | Seahawks | Matching results |
| Empty input | Invalid | Blank | Request a search term |
| Random text | Invalid | xyz123qwerty | No relevant results |
| Special characters | Invalid | !@#$%^ | Handle input safely |



## Step 3: Decision Table Testing

**Feature:** Adding a favorite team to an ESPN account.

**Conditions:**
- C1: Is the user logged in?
- C2: Has a team been selected?
- C3: Is the team available?

**Actions:**
- A1: Save the team.
- A2: Request login.
- A3: Request team selection.
- A4: Display an error or no-results message.

| Condition / Action | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Logged in? | Yes | No | Yes | Yes |
| Team selected? | Yes | Yes | No | Yes |
| Team available? | Yes | Yes | N/A | No |
| A1: Save team | Yes | No | No | No |
| A2: Request login | No | Yes | No | No |
| A3: Request selection | No | No | Yes | No |
| A4: Display message | No | No | No | Yes |

**Test cases:**
1. Logged in + available team: team is saved.
2. Logged out + save attempt: request login.
3. No team selected: request team selection.
4. Unavailable team: display an appropriate message.

## Step 4: State Transition Testing

**Feature:** ESPN account sign-in.

**States:**
- S1: Logged out
- S2: Entering login information
- S3: Logged in
- S4: Login error displayed

**Events:**
- E1: Click login.
- E2: Submit valid credentials.
- E3: Submit invalid credentials.
- E4: Correct credentials and retry.
- E5: Cancel login.
- E6: Access favorites while logged out.

| Current State | Event | Next State | Transition |
|---|---|---|---|
| S1 | E1: Click login | S2 | Valid |
| S2 | E2: Valid credentials | S3 | Valid |
| S2 | E3: Invalid credentials | S4 | Valid |
| S4 | E4: Retry | S2 | Valid |
| S4 | E5: Cancel | S1 | Valid |
| S1 | E6: Access favorites | S1 | Valid; access restricted |
| S3 | E1: Click login again | S3 | No new login required |



## Conclusion

This assignment helped me understand how black-box testing can be used to test a website like ESPN without looking at its code. I learned how to group test inputs, use decision tables to check different scenarios, and test how the website responds to different user actions. These techniques can help identify problems and make sure the website works as expected.
