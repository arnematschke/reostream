# reostream Home Assistant Add-on

This add-on runs the published multi-architecture reostream image. Home Assistant opens reostream's web interface directly on port 8562. HTTP and RTSP streams are exposed on ports 8560 and 8561.

## Installation

1. In Home Assistant, open **Settings → Add-ons → Add-on Store**.
2. Open the store menu, select **Repositories**, and add `https://github.com/VoltTech21/reostream`.
3. Find **reostream** in the store, install it, and start it.
4. Find the one-time claim token in the add-on logs.
5. Select **Open Web UI**, enter the token on the claim page, and save the password it provides.
6. Add your cameras in the web interface. The add-on must be able to reach each camera on Reolink's Baichuan port, TCP 9000.

reostream stores its configuration and credentials in the add-on's persistent `/data` directory.

## Accessing the streams and web interface

The add-on publishes the web interface on port 8562, HTTP-MPEG-TS on port 8560, and RTSP on port 8561. Select **Open Web UI** from the add-on page, or open the web interface from a browser on your local network. Stream clients can use your Home Assistant host's address:

- HTTP-MPEG-TS: `http://<home-assistant-host>:8560/<camera>.ts`
- RTSP: `rtsp://<home-assistant-host>:8561/<camera>`
- Web interface: `http://<home-assistant-host>:8562/`

If you change the host ports in the add-on configuration, update the URLs accordingly. The web interface uses reostream's own claim and password login.

## Details

- Supported architectures: `amd64` and `aarch64` on Home Assistant OS.
- The add-on uses `ghcr.io/volttech21/reostream`. The main repository maintains the published image and its multi-architecture builds.
- Camera settings and credentials are managed by reostream in `/data`; they are not configured through Home Assistant add-on options.
