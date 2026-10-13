# Klisten MeterMCP for Gemini CLI — v0.1.0

Read this API key’s current usage reservation totals by UTC day.

Query at most 31 inclusive UTC dates. Amounts are integer micro-USD strings and reflect current reservation states grouped by budget day. They are not account balance, bank receipts, historical end-of-day snapshots or third-party settlement. This connector cannot move money.

## Authentication and scope

Endpoint: https://api.klisten.co.kr/mcp/metermcp
Create your own dedicated key at https://klisten.co.kr/app with `meter:read`. Configure the sensitive extension setting `KLISTEN_METERMCP_API_KEY`. Never place credentials in prompts, arguments, files in this package or public repositories. No administrator or shared operator key is supplied. API key authentication only; no OAuth flow is claimed.

Prerequisites: No prior spending required; zero totals are a legitimate result.

## Installation and removal

Install this published repository: `gemini extensions install https://github.com/daehoonkwon-hash/klisten-metermcp-gemini-extension`. The local path command below is an alternative for downloaded source.

From the parent directory run `gemini extensions install ./klisten-metermcp`. Enter your key only in the sensitive setting. Inspect `/mcp` in Gemini CLI. Uninstall with `gemini extensions uninstall klisten-metermcp`; separately revoke the key in your account. Uninstall does not delete hosted data. If secure settings are unavailable, stop rather than hardcode a key.

Expected tools: `metermcp_usage_get`.

## Grounded examples

- Request: Read today’s usage reservation totals.
  Tool(s): metermcp_usage_get. Expected: Totals and UTC date range; zero is valid.
- Request: Read the last seven UTC dates.
  Tool(s): metermcp_usage_get. Expected: Bounded daily usage for this key only.
- Request: Try an inverted date range.
  Tool(s): metermcp_usage_get. Expected: Validation rejection; no financial action.

## Limits and verification

This is an integration package, not a purchase, paid subscription, safety certification or service SLA. Existing product prerequisites and pricing apply; installation itself does not charge or replenish credit. Do not infer that every underlying operation is free. No money transfer or paid execution is authorized by installing. Any paid action or data mutation requires the account holder’s authorization. Missing records and denied access are errors, not successful demonstrations.

Gemini CLI 0.63.0 native MCP library tool discovery: PASS (2026-10-13). Discovery alone does not prove authentication enforcement; protected call results are listed separately. This was a scripted library harness, not the interactive Gemini application or a model conversation. Gemini conversation tools/call: NOT_VERIFIED. Local installation/removal evidence is recorded separately and does not prove service or conversation success. Prior revoked validation keys cannot be reused. GitHub distribution and the gallery discovery topic do not establish gallery listing or approval.

Documentation: https://klisten.co.kr/docs.html
Privacy: https://klisten.co.kr/privacy.html
Terms: https://klisten.co.kr/terms.html
Support: klisteninc@gmail.com

## Required Gemini 0.63 environment setting

Gemini 0.63 redacts API_KEY environment values from MCP transport headers by default. Explicitly allow only this extension's variable in your isolated Gemini profile settings.json, merging without removing existing settings:

```json
{"security":{"environmentVariableRedaction":{"allowed":["KLISTEN_METERMCP_API_KEY"]}}}
```

This file contains the variable name only, never the key. Keep the key in the sensitive extension setting. Do not disable redaction globally or allow all environment variables. Without this narrow exception, authentication returns 401. After installation and this configuration, inspect `/mcp` before any use.

Latest safe native-library call verification: PASS. metermcp_usage_get
