# NEO 2.3.1 — Deployment Release Notes

## Authentication / access
- Fixed the production `Secure` session-cookie bug on plain HTTP development/local deployments. Secure cookies are now sent only when the actual request is HTTPS or the configured public origin is HTTPS.
- Existing installations with an older administrator record can be re-synchronized to `NEO_ADMIN_PASSWORD` once at boot until the password becomes user-managed.
- System Administrator recovery accepts the configured recovery mailbox even if the stored administrator email differs.
- Login now reports missing production recovery configuration instead of leaving users with a generic failure.
- Protected pages still redirect to login when there is no authenticated session.

## Signup / approval
- Every public signup requests a full NEO department and department-specific role.
- Access remains PENDING until System Administrator approval.
- Approval can retain the requested password or issue a temporary password.
- Production approval mail is sent through Resend or SMTP when configured.
- System Maintenance remains System-Administrator-only.
- Added a System-Administrator-only production email test action.

## QMS / deviations
- Canonical department normalization is used across deviation, audit, incident and department APIs.
- Clinical Trial deviation creation works with the full department name.
- Locked deviations remain viewable; signed workflow steps cannot be reopened.

## NEO answer engine
- Added a direct server-side Gemini text answer path using `GOOGLE_GEMINI_API_KEY` and `NEO_TEXT_MODEL=gemini-3.8-flash` when no custom `NEO_CHAT_URL` is configured.
- Internal NEO knowledge, runtime records/history, Google results and configured enterprise connector results are supplied to the answer engine.
- Internal, Google and enterprise retrieval is parallelized with bounded fast-response timeouts.
- Conversation-history request fields are normalized and sent to the optional model gateway.

## Live voice
- Global NEO Live companion on authenticated workspace pages.
- Department/page context is passed to the Live session.
- Clinical and Pharmacovigilance workflows are permission checked server-side.
- Gemini Live uses short-lived server-issued credentials.
- Browser speech fallback is available when Gemini Live credentials are not configured.
- Voice microphone output is routed through a zero-gain monitor path to reduce local mic echo.

## Enterprise / UX
- Restored Careers and Contact links in the authenticated Command Center.
- Contact phone is presented as `+91 88981 82631` with mail/tel/map actions.
- Enterprise connector status and search remain server-side.
- Deployment docs now include production email and enterprise connector setup.
