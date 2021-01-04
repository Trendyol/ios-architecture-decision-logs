# Use CoreTracker and CoreTrackable Interface instead of Legacy Trackable Interface

 * Status: accepted
 * Deciders: iOS Team
 * Date: 2020-01-04

## Context

Our team created new Core Tracker Interface for tracking events. For consistency we should replace and use CoreTrackable instead of Legacy Trackable Interface.

## Decision

Every new events must use CoreTrackable. Also every new event should use new Tracker approach.

 ## Consequences

 * All events tracking will be in the same format.
 * With CoreTrackable handling events are easy and simple
