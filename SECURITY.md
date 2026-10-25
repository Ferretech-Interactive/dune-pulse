# Security policy

Dune Pulse includes a kernel driver and a background service, so we take security reports seriously and handle them privately.

## Reporting a vulnerability

**Don't open a public issue.** Use GitHub's private reporting instead:

1. Go to the [**Security** tab](../../security) of this repository.
2. Choose **Report a vulnerability** and fill in the form.

Only FerreTech maintainers see the report. We aim to acknowledge it within **3 business days** and to tell you what we'll do about it within **14 days**.

Please include:

- the Dune Pulse version (from **About**, or the setup file name) and your Windows version;
- what the weakness is, and what an attacker could do with it, starting from what access (standard user, administrator, network);
- steps to reproduce, on a machine you own.

Please **don't** include private keys, certificates, passwords or tokens, even ones you found. Tell us where they are and how they're exposed instead.

## What's in scope

- The **driver**: anything that lets a program other than Dune Pulse's own signed service use it, read memory it shouldn't, or crash Windows.
- The **signed approval list** (caller policy): forging, replaying or bypassing it.
- The **background service and the app**: anything that lets another user or program get at the data, or run code with the service's rights.
- **Setup and updates**: anything that gets an unsigned or unofficial file installed, or changes the PC in ways setup doesn't describe.
- **Privacy**: anything that shows, stores or sends information about other players, or sends anything about you.

## Known limits

These are documented design limits, not new findings. Report them only if you've found something beyond them:

- An **administrator** or code running in the **kernel** can defeat Dune Pulse's protections, as with any Windows software.
- The integrity checks cover each Dune Pulse program's main executable. They don't cover DLLs or code injected into a running process.

## Testing

Test only on machines you own or are allowed to test. Don't test against other players, game servers, or FerreTech's download host.

## After a report

We'll keep you informed while we fix it, credit you in the release notes if you'd like, and publish a fixed release before giving details.
