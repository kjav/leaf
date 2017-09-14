# Leaf: A rust game server

Leaf is a lightweight, fast game server written in rust and designed to be run in a container.

## Commands
  1. CreateSession
  2. ListSessions
  3. JoinSession
  4. LeaveSession
  5. ChangeSettings
  6. ChangeState
  7. Action

User ID:
  name
  publickey

User key:
  signature

### CreateSession
  In: User ID, User key, session settings, session rules, session state
  Out: Successful, Session ID?
  Change: Add session to session list

### ListSessions
  In: User ID, User key
  Out: [sessions]
  Change: -

### JoinSession
  In: User ID, Session ID, User key
  Out: Sussessful
  Change: session[Session ID].state.users.push(User ID)

### LeaveSession
  In: User ID, Session ID, User key
  Out: Successful
  Change: session[Session ID].state.users.remove(User ID)

### ChangeSettings
  In: User ID, Session ID, User key, Settings
  Out: Successful
  Change: session[Session ID].settings = Settings

### ChangeState
  In: User ID, Session ID, User key, State
  Out: Successful
  Change: session[Session ID].state = State

### Action
  In: Action, User ID, Session ID, User key
  Out: Successful
  Change: session[Session ID].state.actions.push(Action)
