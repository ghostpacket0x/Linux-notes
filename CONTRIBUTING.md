# Contributing

Thanks for helping improve these notes. Mistakes, missing commands, and clearer explanations are all welcome.

## Report a problem

Open an **Issue** if you find:

- a command that doesn't work, or an example with the wrong output
- a broken link or a table that doesn't display properly
- a command that's missing or unclear

Include the section or file name, the command you ran, and what you expected compared with what happened.

## Suggest a change

1. Fork the repository.
2. Create a branch with a clear name, such as `fix-cron-example`.
3. Make your change in the matching file.
4. Open a **Pull Request** and describe what you changed and why.

## Writing style

Every command entry follows the same pattern:

| Column | What to write |
|---|---|
| Command | The command in code formatting, with placeholders in `<angle brackets>` |
| What it does | One short sentence, in plain English |
| Example | A working example, ideally from a Kali VM |

Keep the explanations in your own words. Link to the man page for detail rather than copying it.

## Safety rules

- **Never include passwords, private keys, flags, or lab answers.** This includes Hack The Box and other platforms that ask for answers to stay private.
- **Remove personal information** such as real IP addresses, usernames, and hostnames from examples. Use placeholders instead.
- **Use test values for destructive commands**, and say clearly when a command deletes files, changes permissions, or changes firewall rules.
- **Only write about testing you're allowed to do.** Notes on scanning or exploitation should always mention permission.

## Labs

Each lab needs a goal, the steps, what to check, and a clean-up section. Put any command that changes the system in a practice folder, or in a VM you're allowed to change.
