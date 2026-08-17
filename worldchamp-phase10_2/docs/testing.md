# P10.2 Validation Logging

## Setup

1. Add WorldChamp P10.2 to a 5-minute NAS100 chart.
2. Set **Operating mode = Validation**.
3. Keep **Enable WCLOG session logging = ON**.
4. Set the validation calendar window to about 45 days for roughly 30 market sessions.
5. Allow the chart to load the available history.

## Open Pine Logs

Open the indicator's menu (three dots next to WorldChamp P10.2) and choose **Pine Logs**. In the Pine Logs panel, search/filter for `WCLOG`.

P10.2 emits one line per completed NY session in this format:

`WCLOG,2026-08-14,CTX_P=0,CTX_B=18,RET=0,R15=0,R1=0,SRC=n/a,GEO_L=0,GEO_R=0,GEO_V=0,GEO_S=0,GEO_A=0,TOUCH=0,FV=0,PART=...,OF=...,AGG_B=...,AGG_S=...,ABS_SA=...,ABS_BA=...,ABS_P=...,DOM_B=...,DOM_S=...,SET_L=...,SET_S=...`

## Send results

Copy all `WCLOG` lines for the test period and paste them into ChatGPT. A text file containing the copied lines is also fine. No daily screenshots are required.

## Important

Logging is diagnostic only. It does not alter context, location, `.886` invalidation, value, participation, order-flow, READY, plan, or management logic.
