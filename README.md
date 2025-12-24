# SysCli - Brendan Gregg USE Method as CLI wiki

I hate searching for commands arguments, learning by heart, maybe needing to check one or two descriptions. Besides I also always have a tab opened in Brendan website, specifically the [USE Method](https://www.brendangregg.com/USEmethod/use-linux.html)

This CLI is just meant to ease my laziness

## QuickStart

### Show help with available filters
```bash
./syscli --help
```

### Show all data
```bash
./syscli
```

### Filter by resource
```bash
./syscli --resource cpu
./syscli -r cpu
```

### Filter by type
```bash
./syscli --type utilization
./syscli -t utilization
```

### Combine filters
```bash
./syscli -r cpu -t errors
```
