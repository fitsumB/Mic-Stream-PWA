# Mic Stream PWA

A Progressive Web Application that allows you to use your mobile device's microphone as a wireless microphone for your computer.

## Features

- Works offline (PWA)
- Simple WiFi connection
- Real-time audio streaming
- No installation required on the computer (just run the Python script)

## Setup

### Prerequisites

1. Python 3.7 or higher
2. A modern web browser that supports PWA and WebSocket
3. Both devices (mobile and computer) must be on the same WiFi network

### Installation

1. Clone this repository or download the files
2. Install the Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Start the Python server on your computer:
   ```bash
   python server.py
   ```
   The server will display its IP address.

2. Open the PWA on your mobile device:
   - Open `index.html` in your web browser
   - Install the PWA when prompted (optional but recommended)

3. Connect to the server:
   - Click the "Start Microphone" button
   - Enter the server's IP address when prompted
   - Grant microphone permissions when requested

4. The microphone will start streaming to your computer

5. To stop:
   - Click the "Stop Microphone" button
   - Or close the browser tab

## Technical Details

- The PWA uses WebSocket for real-time communication
- Audio is streamed in chunks of 1024 samples
- Sample rate: 44.1kHz
- Channels: 1 (mono)

## Security Note

This is a basic implementation for testing purposes. For production use, you should:
- Add proper authentication
- Use secure WebSocket (WSS)
- Implement error handling and reconnection logic
- Add proper audio processing and buffering

## Local Testing (Recommended)

To bypass the HTTPS requirement during testing:

1. Host the PWA locally using Python:
   ```bash
   # Navigate to your PWA directory
   cd /path/to/Mic-Stream-PWA
   
   # Start a simple HTTP server
   python -m http.server 8000
   ```

2. Access the PWA on your mobile device using:
   ```
   http://SERVER_IP:8000
   ```
   Where `SERVER_IP` is your computer's IP address (the same address shown in the audio server)

3. You can now connect to the WebSocket server without HTTPS restrictions.

## HTTPS Setup (For Production)

If you need to use the GitHub Pages hosted version with secure WebSockets:

1. Set up an SSL certificate for your local WebSocket server using a tool like ngrok:
   ```bash
   # Install ngrok
   # Start your Python server
   python server.py
   
   # In another terminal, start ngrok to create a secure tunnel
   ngrok http 8765
   ```

2. Use the secure WebSocket URL provided by ngrok in your connection. 