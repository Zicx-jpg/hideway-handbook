# Link your account to Discord

The Hideway Discord bot can link your **launcher account** to your Discord. It shows the time you have left, frees your PC when you change computer, and gives you the **Hideway Client** role while your license is active.

## Link it (once)

1. Open the launcher and **create an account** (the **Create account** tab) with a license key, if you have not already.
2. In the Hideway Discord, type `/launcher link` and paste **a license key you already used on your account**. Only you see the answer.
3. The bot replies **Launcher account linked**.

Why a key you already used? Only the buyer knows a used key, and it proves the account is yours. A key nobody used yet is refused: create the account in the launcher first, then link.

* You can link up to **3** launcher accounts.
* An account is linked to **one** Discord member. If it is already taken by someone else, open a ticket and the staff will move it.
* `/launcher unlink account:<username>` removes a link. It never touches the account itself.

## Commands

| Command | What it does |
|---|---|
| `/launcher link key:<key>` | Links your launcher account with a key you already used. |
| `/launcher status` | Shows the time left on each linked account and whether a PC is attached. |
| `/launcher reset-pc` | Frees the account from its PC so you can sign in on another one. Add `account:` only if you linked several. |
| `/launcher unlink account:<name>` | Removes a link. |

## Changing PC

1. Run `/launcher reset-pc`.
2. Sign in to the launcher on the new PC.

You can free your PC **2 times per 30 days**. If you are over the limit, the bot tells you when the next one is possible; otherwise open a ticket. If no PC is attached yet, there is nothing to free: just sign in.

## Role and reminders

* While a linked account has time left you get the **Hideway Client** role. It is removed when the time ends. If KeyAuth does not answer, the role stays as it is.
* You get **one direct message 3 days** and **one 1 day** before the end, with a link to get a key. Turn these off in your Hideway account settings (direct messages). Keep your DMs open for the server.
* To add time, use **Add a key** in the launcher (click the license box at the bottom left).

## If something does not work

| You see | Do this |
|---|---|
| *Key Not Used Yet* | Create the account in the launcher with that key first, then run `/launcher link` again. |
| *Key Not Found* | Check the key for typos. |
| *Already Linked* | The account belongs to another member: open a ticket. |
| *KeyAuth Is Busy* | Try again in a minute. |
| *Limit Reached* | You used your 2 PC changes this month: open a ticket. |
| No role after linking | The role is given within 30 minutes. Still missing after that: open a ticket. |