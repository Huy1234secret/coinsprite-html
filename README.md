# coinsprite-html

## Troubleshooting Discord errors

### `BUTTON_COMPONENT_INVALID_EMOJI`
If you see an error like:

```
DiscordAPIError[50035]: Invalid Form Body
data.components[...].emoji.id[BUTTON_COMPONENT_INVALID_EMOJI]: Invalid emoji
```

It means a button component is trying to use an invalid emoji. To fix it:

1. **Use a valid Unicode emoji** (no `id` field required), for example `"emoji": { "name": "✅" }`.
2. **Or use a valid custom emoji** that exists in a guild the bot can access, for example:
   ```json
   "emoji": { "id": "123456789012345678", "name": "my_emoji" }
   ```
3. **Avoid passing empty or mismatched emoji data** (e.g., an `id` that does not exist, or an `id` without a matching `name`).

Once the emoji payload is corrected, the interaction update should succeed without the 50035 error.
