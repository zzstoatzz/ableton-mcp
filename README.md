# AbletonMCP: Control Ableton Live with Claude

AbletonMCP is a Model Context Protocol (MCP) implementation that allows Claude to control Ableton Live through natural language commands. This project enables users to generate music and control Ableton using simple English prompts.

## Overview

AbletonMCP consists of two main components:

1. **AbletonOSC** - A third-party MIDI Remote Script that allows communication with Ableton Live via OSC (Open Sound Control)
2. **AbletonMCP Server** - A Python server that acts as a bridge between Claude and Ableton Live

With this setup, you can ask Claude to:
- Create drum patterns
- Generate melodies and basslines
- Create complete tracks in specific styles
- Control Ableton's transport, devices, and parameters

## Installation

### Prerequisites

- Ableton Live 11 or above
- Python 3.7+
- Claude access (via web interface or API)

### Automatic Installation

1. Download this repository
2. Run the installer script:
   ```
   python installer.py
   ```
   
The installer will:
- Install required Python packages
- Download and install AbletonOSC to your Ableton MIDI Remote Scripts folder
- Set up the AbletonMCP server in your home directory

### Manual Installation

If you prefer to install manually:

1. **Install Python Packages**:
   ```
   pip install fastmcp python-osc pythonosc
   ```

2. **Install AbletonOSC**:
   - Download [AbletonOSC](https://github.com/ideoforms/AbletonOSC)
   - Copy the `AbletonOSC` folder to your Ableton User Library/Remote Scripts folder:
     - Windows: `\Users\[username]\Documents\Ableton\User Library\Remote Scripts`
     - macOS: `Macintosh HD/Users/[username]/Music/Ableton/User Library/Remote Scripts`

3. **Install AbletonMCP Server**:
   - Copy `ableton_mcp_server.py` to a directory of your choice
   - Create a startup script or use the provided `start_ableton_mcp.py`

## Usage

### Step 1: Configure Ableton Live

1. Start Ableton Live
2. Go to Preferences > Link / MIDI
3. In the "Control Surface" dropdown, select "AbletonOSC"
4. Ableton should display a message saying "AbletonOSC: Listening for OSC on port 11000"

### Step 2: Start the AbletonMCP Server

1. Navigate to the AbletonMCP directory (default: `~/AbletonMCP`)
2. Run the start script:
   ```
   python start_ableton_mcp.py
   ```

### Step 3: Connect to Claude

1. Connect to Claude via your preferred method (web interface or API)
2. You can now ask Claude to create music in Ableton!

## Example Commands

- "Create a basic 4/4 drum beat with kick on beats 1 and 3, snare on beats 2 and 4"
- "Create an 80s style synthwave track with a driving bassline, atmospheric pads, and a catchy lead melody"
- "Create a loops and cats rhythm with drums"
- "Set the tempo to 120 BPM"
- "Add a bass line that follows the chord progression"

## How It Works

1. You send a natural language request to Claude
2. Claude interprets your request and calls the appropriate tools in the AbletonMCP server
3. The server translates these commands into OSC messages
4. AbletonOSC receives the OSC messages and controls Ableton accordingly
5. Any responses from Ableton are sent back to Claude through the same path

All the musical intelligence and decision-making happens in Claude, while the server simply provides the communication tools without any built-in music logic.

## Troubleshooting

- If Claude can't connect to Ableton, make sure AbletonOSC is selected in Ableton's preferences
- Check that both Ableton Live and the AbletonMCP server are running
- Restart the AbletonMCP server if you encounter any connection issues
- Check the logs in the AbletonMCP directory for more detailed error information

## Limitations

- Currently limited to the functionality exposed by AbletonOSC
- Sound selection depends on instruments already loaded in Ableton
- Some advanced features (like loading specific VST presets) may require templates

## Future Enhancements

- Extended support for device-specific parameters
- Template library for common music styles
- Integration with sample libraries
- Support for arrangement view automation

## Credits

- AbletonOSC by Sam Haines: https://github.com/ideoforms/AbletonOSC
- Based on the Blender MCP integration architecture

## License

MIT