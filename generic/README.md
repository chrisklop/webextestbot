# WidgetScope - Webex Connect Debug Dashboard

A generic, reusable debug dashboard for testing and troubleshooting Webex Connect (IMI Chat) chatbot widgets.

## Features

- **Real-time PostMessage monitoring** - See all communication between widget iframe and parent page
- **Console log capture** - Intercepts and displays all JavaScript console output
- **Network activity tracking** - Monitors XHR and Fetch requests
- **Widget event logging** - Tracks widget lifecycle events
- **Noise filtering** - Automatically filters React DevTools and browser extension messages
- **Boolean highlighting** - Green for true, red for false in JSON displays
- **Widget config parsing** - Displays parsed widget configuration in sidebar
- **Comprehensive documentation** - Built-in help panel with SDK reference

## Quick Start

### Option 1: URL Parameters

Just add your credentials to the URL:

```
index.html?guid=YOUR-WIDGET-GUID&bind=YOUR-BIND-ID&org=Your%20Company
```

### Option 2: Setup Modal

1. Open `index.html` in a browser
2. The setup modal will appear automatically
3. Enter your Widget GUID and Data Bind ID
4. Click "Save & Load Widget"

Your credentials are saved to localStorage for future visits.

### Option 3: Direct Configuration

Edit the `divicw` element directly:

```html
<div id="divicw"
     data-bind="YOUR-BIND-ID"
     data-guid="YOUR-WIDGET-GUID">
</div>
```

## Where to Find Your Credentials

1. Log in to **Webex Engage Admin Console**
2. Go to **Assets** > **LiveChat**
3. Select your widget
4. Find the **Installation** tab
5. Copy the `data-guid` and `data-bind` values from the snippet

## URL Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `guid` | Widget GUID from Webex Engage | Yes |
| `bind` | Data Bind ID from installation snippet | Yes |
| `org` | Organization name (displayed in sidebar) | No |

## Dashboard Panels

### Left Sidebar
- Widget status indicators
- Session information
- Filter controls
- Widget configuration display
- Quick action buttons

### Console Logs
Captures all `console.log`, `console.error`, `console.warn`, and `console.info` calls.

### PostMessages
Shows all `postMessage` communication. Messages are categorized:
- **WIDGET** (green) - Messages from media.imi.chat
- **BROWSER** (gray) - Browser extension noise
- **DEBUG** (blue) - Debug panel messages

### Network
Tracks all XHR and Fetch requests with timing and response data.

### Widget Events
Logs widget lifecycle events like script loading, DOM mutations, and config receipt.

## Quick Actions

| Button | Action |
|--------|--------|
| Inspect | Logs current widget DOM state |
| Ping | Tests connectivity to IMI servers |
| Full Report | Copies comprehensive debug report to clipboard |
| Copy Config | Copies widget configuration JSON |

## Keyboard Shortcuts

- `Escape` - Close help panel or setup modal

## Deployment

This is a single HTML file with no dependencies. Deploy it anywhere:

- Static file hosting (GitHub Pages, Netlify, Vercel)
- Local file system
- Any web server

### Vercel Example

```bash
npm i -g vercel
vercel --prod
```

## Customization

### Branding
The organization badge is configurable via:
- URL parameter: `?org=Your%20Company`
- Setup modal
- LocalStorage: `webex_widget_org`

### Filters
Toggle these in the sidebar:
- Hide React DevTools noise
- Hide debug panel test messages
- Collapse repeated messages

## Troubleshooting

### Widget Not Loading
1. Check that GUID and Bind ID are correct
2. Verify your domain is whitelisted in Webex Engage Admin Console
3. Use the Ping button to test connectivity
4. Check Console Logs for errors

### No PostMessages Appearing
1. Disable the "Hide React DevTools" filter temporarily
2. Check if the widget script loaded (see Network panel)
3. Look for `loadstyles` action - if missing, widget failed to initialize

### Common Errors
- **404 on imichatinit.js** - Script URL may be blocked
- **CORS errors** - Domain not whitelisted
- **No agent_avail** - Check agent schedules in Admin Console

## License

MIT License - Feel free to use, modify, and distribute.

## Resources

- [Webex Engage Developer Guide](https://docs.imi.chat/reference/introduction)
- [LiveChat Channel Setup](https://docs.imi.chat/docs/livechat-channel)
- [Cisco Community Forum](https://community.cisco.com/t5/webex-connect/bd-p/connect)
