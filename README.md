# Typst Bot

A Discord bot that renders Typst code.

Built with poise so it has all the goodies like edit tracking, typing status, and automatic help generation.

## Hosting

The bot uses two binaries:

- `bot`: connects to Discord and processes messages
- `worker`: receives requests, interacts with Typst, responds

`bot` will automatically spawn `worker`, so you only need to run `bot`.

To set up the working environment, create a directory with the following items:

- `worker`: The worker binary, copied/hardlinked from the target directory after building. If you put the worker somewhere else, you can set `TYPST_BOT_WORKER_PATH` to it.
- `bot`: The bot binary, copied/hardlinked from the target directory after building. (This doesn't need to be in this directory, but having everything in one place simplifies things.)
- `db.sqlite`: You can just `touch` this, but the bot needs to be able to write to it.
(Legacy note: you don't need `fonts` anymore because we use `typst-assets` now.)

To run, CD into this directory, set `DISCORD_TOKEN` to your bot token, set `CACHE_DIRECTORY` and `DB_PATH` to suitable locations, and run the `bot` binary (not the `worker` binary that's also in the directory).

### Docker

There is a `Dockerfile` and `docker-compose.yml` for running the bot inside a Docker container.

To set up the bot with Docker, create a `discord_token.txt` file containing your bot token and start the container with `docker compose up -d`.

### Public Instance

Here is a link you can use to invite a public instance run by [@frozolotl](https://github.com/frozolotl): https://discord.com/oauth2/authorize?client_id=1183804211264225301&permissions=3072&scope=bot

Note: the bot may be limited from joining more servers because we require the message content (since slash commands don't support code blocks) and Discord denied verification, so we are limited to 100 servers. Accordingly, we request that you remove the bot from your servers if you are not using it anymore.

## License

AGPL. Use `?source` to get a link to the source from deployments of the bot.
