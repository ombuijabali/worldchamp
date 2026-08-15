# Architecture

WorldChamp is a manual-execution decision-support system.

## Data flow

4H -> 1H -> 15M -> 5M

- 4H: macro environment context
- 1H: intermediate structure context
- 15M: location refinement
- 5M: operating chart and eventual order-flow confirmation

## Non-repainting policy

Higher-timeframe decision data uses confirmed values only. The Pine implementation requests HTF values with a one-bar offset and `barmerge.lookahead_on`.

## Execution policy

The project intentionally does not call `strategy.entry`, `strategy.exit`, or any automated execution primitive. The trader remains responsible for every order.
