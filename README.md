# Basta Filter Packs

Pre-built SMS spam filter categories for the [Basta](https://github.com/oribarilan/basta) app.

## Structure

```
basta-packs/
├── manifest.json          # Pack metadata (id, name, icon)
├── packs/
│   ├── political.json     # Political campaign texts
│   ├── package-scams.json # Fake delivery notifications
│   ├── financial.json     # Banking/financial scams
│   └── gambling.json      # Gambling & lottery spam
└── README.md
```

## Pack Format

Each pack JSON file follows this structure:

```json
{
  "id": "pack-id",
  "version": "1.0.0",
  "rules": [
    {"type": "contains", "value": "spam phrase", "action": "junk"},
    {"type": "regex", "value": "pattern\\d+", "action": "junk"}
  ]
}
```

### Rule Types

| Type | Description | Example |
|------|-------------|---------|
| `contains` | Case-insensitive substring match | `"vote for"` |
| `regex` | Regular expression pattern | `"text\\s+\\w+\\s+to\\s+\\d{5}"` |

### Actions

| Action | Description |
|--------|-------------|
| `junk` | Filter message to junk/spam |
| `promotion` | Mark as promotional |
| `transaction` | Mark as transactional |

## Contributing

Want to improve spam detection? Contributions are welcome!

### Adding Rules

1. Fork this repository
2. Edit the appropriate pack in `packs/`
3. Test your regex patterns at [regex101.com](https://regex101.com)
4. Submit a pull request with:
   - Description of the spam you're targeting
   - Example messages that would match (sanitized)

### Guidelines

- **Be specific**: Avoid overly broad patterns that could block legitimate messages
- **Test thoroughly**: False positives (blocking real messages) are worse than false negatives
- **Use case-insensitive matching**: The app handles case normalization
- **Document patterns**: Explain what each regex pattern is meant to catch

### Proposing New Packs

Open an issue to discuss new pack categories before implementation.

## License

MIT License - see [LICENSE](LICENSE) for details.
