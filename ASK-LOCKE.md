# ASK LOCKE
### A document-selection assistant with a controlled handoff into real forms

**Portfolio case study · Source inspected November 13, 2026**

Ask Locke is not a generic legal-advice chatbot. Its architecture separates **product discovery** from **in-form assistance**, keeping the final document-generation authority outside the AI conversation.

## Discover the appropriate document

A visitor describes the underlying situation rather than naming an instrument. Ask Locke receives a controlled subset of the catalog, can ask a clarifying question, and returns a recommended product. The server accepts the recommendation **only when the slug is present among available catalog products**; the UI then offers a handoff into the selected workflow.

## Support the person once the form is open

When a real document is selected, the assistant can receive allowed field IDs, labels, options and limited state context. It can explain questions and propose entries from facts the person volunteers. Parsed suggestions are validated against **actual field IDs** and remain pending until the person selects **Apply to form**. The assistant cannot silently choose new legal clauses or change the document engine itself.

## Twelve inspected design elements

| Element | Implementation evidence |
|---|---|
| Situation-led questions | Two-mode assistant, with a document-picker prompt |
| Clarification handling | Brief question when selection is ambiguous |
| Real catalog grounding | Recommended slug must match an available product |
| State context | Normalized state from page or visitor context |
| Direct workflow handoff | Selected product linked into the correct form |
| Active form awareness | Dedicated field-help mode after selection |
| Contextual field explanations | Field labels, types, sections and options |
| Draft-entry suggestions | Structured fill output based on user-supplied facts |
| Restricted targets | Suggestions checked against allowed field identifiers |
| Human approval | Explicit Apply-to-form control; no silent form mutation |
| Deliberate data minimization | Completed answers excluded from model context unless the person shares them, except limited jurisdiction context |
| Resource and failure controls | Message bounds, request/session rate limits and an unavailable-state response |

The core pipeline in the private application comprises an API endpoint for Ask Locke, the prompt/response parser and the browser's controlled application of suggestions. The final legal instrument is assembled independently from maintained content and rules.

## Why it matters for engineering teams

This implementation demonstrates **LLM output validation, safe human approval, schema integration, user-context reduction and a clear boundary between conversational generation and authoritative application state**. Competing services offer AI and guided drafting, so this is an implementation-level showcase—not a claim that other vendors have no comparable functions.

**[Full market comparison](COMPARISON.md)** · **[Official demo](https://www.lockedirect.com/media/locke-direct-demo.mp4)** · **[Back to portfolio](README.md)**

*Based on inspected source files from the live product's private repository; independent benchmark results are not claimed.*
