<h1>Project Name</h1>
....

<h2>Project Description</h2>
....

<h2>Motivation</h2>
I want to watch partner tv on my new 27 inch pc so how to do it.

<h2>Current setup</h2>
<ul>
<li>partner has android app and can be watched on tv</li>
<li>i want to watch basketball game via partner on pc</li>
<li>partner no longer support web view</li>
<li>my pc is connected via router it is not connected to the tv</li>
<li>my pc run windows 10 i might be willing to upgrade to windows 11</li>
<li><strong>Pc setup</strong></li>
    <ul>
        <li>Device Name: DESKTOP-P36PBLU</li>
        <li>Processor: 12th Gen Intel(R) Core(TM) i3-12100F @ 3.30 GHz</li>
        <li>Installed RAM: 16.0 GB (15.9 GB usable)</li>
        <li>Storage: <ul>
            <li>238 GB SSD (Lexar SSD NM620 256GB)</li>
            <li>298 GB HDD (Hitachi HDS721032CLA362)</li>
        </ul></li>
        <li>Graphics Card: NVIDIA GeForce GT 710 (2 GB)</li>
        <li>Device ID: 4762E43E-8FC6-4AE0-B63A-600A5FF38D72</li>
        <li>Product ID: 00326-00782-09570-AAOEM</li>
        <li>System Type: 64-bit operating system, x64-based processor</li>
        <li>Pen and touch: No pen or touch input is available for this display</li>
    </ul>
<li><strong>Windows 10 Details:</strong></li>
<ul>
    <li>Edition: Windows 10 Home</li>
    <li>Version: 22H2</li>
    <li>Installed on: 09/03/2021</li>
    <li>OS Build: 19045.6456</li>
</ul>
<li>My Mobile phone</li>
<ul>
<li>The Realme C21</li>
<li>uses a Micro-USB charging port and is designed for 10W (5V/2A) charging.</li>
</ul>
<li>Sarit tablet</li>
<ul>
<li></li>
</ul>
</ul>

<h2>Key Takeaways</h2>
<ul>
    <li>...</li>
   
</ul>

<h2>Installation</h2>

  <h3>1. Enable Developer Options & USB Debugging (on Realme C21)</h3>
<ol>
<li>Open <strong>Settings &gt; About phone</strong>.</li>
<li>Find <strong>Build number</strong> (or Software version) and tap it 7 times until you see “You are now a developer”.</li>
<li>Return to Settings &gt; System &gt; Developer options (or search “Developer options”).</li>
<li>Enable <strong>USB debugging</strong>.
<div class="note">If prompted when connecting later, accept the computer's RSA key on the phone (check &ldquo;Always allow from this computer&rdquo; if you trust it).</div>
</li>
</ol>

  <h3>2. Install Android platform-tools (adb)</h3>
  <ol>
    <li>Download the <em>platform-tools</em> (Android SDK Platform Tools) for Windows and extract the ZIP to a folder, e.g. <code>C:\tools\platform-tools</code>.</li>
    <li>Add that folder to your Windows PATH so you can run <code>adb</code> from any CMD/PowerShell window.
      <pre>// example (PowerShell) to test once extracted
cd C:\tools\platform-tools
.\adb.exe version
</pre>
    </li>
    <li>To verify with your phone connected by USB:
      <pre>adb devices
# you should see a device id and the word 'device'
</pre>
    </li>
  </ol>

  <h3>3. Install scrcpy (Windows)</h3>
  <ol>
    <li>Download the scrcpy Windows prebuilt ZIP and extract to a folder, e.g. <code>C:\tools\scrcpy</code>.</li>
    <li>Open a PowerShell or Command Prompt in that folder and run:
      <pre>.\scrcpy.exe</pre>
      <div class="tip">Common useful flags:
        <ul>
          <li><code>--fullscreen</code> &mdash; start fullscreen</li>
          <li><code>--max-size 1080</code> &mdash; limit mirrored resolution (helps bandwidth)</li>
          <li><code>--bit-rate 8M</code> &mdash; raise/lower video bitrate</li>
        </ul>
      </div>
    </li>
  </ol>

  <h3>4. Optional: Install sndcpy (for audio on PC)</h3>
  <ol>
    <li>Download the sndcpy package (a small Java wrapper) and extract it to a folder.</li>
    <li>Ensure you have a Java runtime installed (OpenJDK or Oracle JRE) or install it if missing.</li>
    <li>Run the provided <code>sndcpy.cmd</code> or <code>java -jar sndcpy.jar</code> (depending on package) while phone is connected and adb authorized. This forwards audio to the PC using a temporary local ADB port and a small Android helper app that runs without requiring installation.
    </li>
    <li>After starting sndcpy, open your PC's audio player that listens on the forwarded port (sndcpy includes instructions). Some builds automatically open the audio stream in your default media player.
    </li>
  </ol>

  <h3>5. Workflow to start mirroring + audio</h3>
  <ol>
    <li>Connect phone to PC with USB data cable.</li>
    <li>Confirm device visible: <code>adb devices</code>.</li>
    <li>Start audio forward (optional): <code>sndcpy</code> (follow package instructions).</li>
    <li>Start screen mirror: <code>scrcpy --max-size 1080 --bit-rate 8M --fullscreen</code>.</li>
  </ol>

  <h2>Troubleshooting</h2>
  <ul>
    <li><strong>No device shown by adb?</strong> Reconnect cable, confirm USB mode on phone is not “Charge only”, re-enable USB debugging, and accept the RSA prompt on phone.</li>
    <li><strong>Scrcpy fails to start:</strong> Run <code>.\scrcpy.exe -V debug</code> to see logs. Make sure adb is reachable and the scrcpy folder contains the EXEs.</li>
    <li><strong>Poor performance:</strong> Use the phone’s USB 2.0/3.0 port with a good cable; reduce <code>--max-size</code> and lower <code>--bit-rate</code>.</li>
    <li><strong>No audio on PC:</strong> Ensure sndcpy is running and that you have Java installed. Some media players may not auto-open the forwarded stream—open the stream URL or use the included helper script.</li>
  </ul>

  <h2>Notes & tips</h2>
  <ul>
    <li>If you plan to record the mirrored screen, run scrcpy with the <code>--record file.mp4</code> option.</li>
    <li>Scrcpy mirrors whatever appears on the phone screen; DRM-protected streams may be blocked or blacked out by the app.</li>
    <li>If you ever upgrade to Windows 11, the same steps apply. Upgrading is optional and not required to run scrcpy/sndcpy.</li>
  </ul>

  <h2>Example quick commands</h2>
  <pre>adb devices
// start audio (if using sndcpy)
./sndcpy
// start screen mirroring (example)
./scrcpy --max-size 1080 --bit-rate 8M --fullscreen
</pre>

  <p style="margin-top:24px">Need this as a downloadable HTML file or a version with exact download links and checksums? I can add direct link targets and a small bat file to automate startup.</p>

<h2>Usage</h2>
....

<h2>Technologies Used</h2>
....

<h2>Important concepts</h2>

<h3>scrpy</h3>

Schema

<h3>adb - android debug bridge</h3>

Schema

<img src='./figs/adb-schema.png' alt='adb schema'>

The ADB Client on the Host Machine : is the command-line program (adb) or a software interface (like in Android Studio) that sends debugging and operational commands to the ADB Server.

<h2>Design 1 - Scrcpy</h2>

<p>Scrcpy will show your basketball game (like NBA Live Mobile, Basketball Arena, etc.) very smoothly and clearly on your PC screen.</p>

<h2>Here’s what you can expect:</h2>

<section>
    <h3>🟢 What You’ll Get</h3>
    <ul>
    <li>🎥 Full HD quality (1080p or more)</li>
    <li>⚡ Almost no lag with a USB cable</li>
    <li>🎮 You’ll see the same game you play on the phone — live, real-time</li>
    <li>🔊 Sound plays on your phone (you can use Bluetooth speakers or <code>sndcpy</code> to get sound on PC too)</li>
    </ul>
</section>

<section>
    <h3>🟣 Tips for best experience</h3>
    <ul>
    <li>Use USB cable (not Wi-Fi) → smoother motion for fast games</li>
    <li>Press <code>Ctrl + F</code> → full screen</li>
    <li>Keep phone horizontal (landscape) before starting the game</li>
    <li>Close background apps</li>
    <li>Plug in charger if playing long (mirroring uses more battery)</li>
    </ul>
</section>

<section>
    <h3>✅ Summary</h3>
    <p>Yes — your basketball game will look great on PC with Scrcpy. It’s free, smooth, and has almost no delay — perfect for watching or even recording your gameplay.</p>
</section>

<h2>Demo</h2>
....

<h2>Points of Interest</h2>
<ul>
    <li>it uses debug mode - it use adb (Android Debug Bridge)</li>
   
</ul>

<h2>open issues</h2>
<ul>
    <li>should i use cable or wifi : You should use a USB cable for the best experience, as it provides extremely low latency and a more stable connection, which is ideal for watching live sports. check <img src='./figs/cable.png'/> - exist in KSP near home</li>
    <li>should i use special cable : You should use any standard USB data cable (not a cheap "charge-only" cable) that supports the full file-sharing and adb data transfer required for debugging.</li>
   <li>do i need developer account : No, you do not need a developer account, but you must enable the Developer Options and USB Debugging settings on your Android phone.</li>
</ul>

<h2>References</h2>
<ul>
    <li>...</li>
   
</ul>
