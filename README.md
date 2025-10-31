<h1>Project Name</h1>
Mirror Android App Screen to PC Screen (Partner TV)


<h2>Project Description</h2>
This project documents a <strong>reliable, low-latency, wired method</strong> for mirroring any Android application onto a Windows PC display using the <strong>Scrcpy</strong> tool and the <strong>Android Debug Bridge (ADB)</strong> protocol. It provides a technical solution for streaming content when <strong>web viewers are unavailable</strong>. Specifically, this guide is motivated by the need to bypass the lack of a web view for the <strong>Partner TV</strong> Android app, enabling users to enjoy live, fast-moving content (such as a basketball game) on a larger PC monitor with minimal lag and high stability.

<h2>Motivation</h2>
I wanted to watch live Partner TV content (like basketball games) on my 27" PC monitor. Since Partner TV no longer supports web viewing, I needed a stable and lag-free method to mirror my Android app to the PC.

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
  <li>
    <strong>Usage:</strong> Enable <em>USB debugging</em> on your Android phone, connect it to the PC with a proper data cable, and run <code>scrcpy</code> — your phone’s screen will appear live on the PC.
  </li>
  <li>
    <strong>Resolution:</strong> Check your phone’s screen resolution — it determines the maximum quality of the mirrored display on your PC.
  </li>
</ul>



<h2>Installation</h2>

<p>
Follow these steps to prepare your Android device and Windows PC for screen mirroring using 
<strong>Scrcpy</strong> and <strong>ADB</strong>. The process involves enabling developer options on your phone, 
turning on USB debugging, and installing Scrcpy on your computer.
</p>

<h3>1. Enable Developer Options & USB Debugging (on Realme C21)</h3>
<ol>
  <li>Open <strong>Settings &gt; About phone</strong>.</li>
  <li>Find <strong>Build number</strong> (or Software version) and tap it 7 times until you see “You are now a developer”.</li>
  <li>Return to <strong>Settings &gt; System &gt; Developer options</strong> (or search “Developer options”).</li>
  <li>Enable <strong>USB debugging</strong>.
    <div>If prompted when connecting later, accept the computer’s RSA key on the phone (check “Always allow from this computer”).</div>
  </li>
</ol>

<h3>2. Install Scrcpy (Windows)</h3>
<ol>
  <li>Download the <a href="https://github.com/Genymobile/scrcpy/releases" target="_blank">Scrcpy Windows ZIP</a> and extract it to a folder, e.g. <code>C:\tools\scrcpy</code>.</li>
  <li>Connect your phone via USB cable (use a data cable, not charge-only).</li>
  <li>Open a Command Prompt or PowerShell in that folder and run:
    <pre>.\scrcpy.exe</pre>
  </li>
</ol>






<h2>Usage - Workflow to start mirroring</h2>

<ol>
  <li>Connect phone to PC with USB cable.</li>
  <li>Accept the “Allow USB debugging?” prompt on your phone.</li>
  <li>Start screen mirror:
    <pre>scrcpy</pre>
  </li>
</ol>



<h2>Technologies Used</h2>
<ul>
<li>Android</li>
<li>Adb (Android Debug Bridge) </li>
<li>Scrcpy</li>
<li>Screen Mirroring</li>
<li>Windows 10</li>
</ul>

  <h2>Important concepts</h2>

  <p>
Before using <strong>Scrcpy</strong> and <strong>ADB</strong>, it’s helpful to understand how these tools work together.
Scrcpy handles the screen mirroring process, while ADB provides the communication channel between your Android device and PC.
Knowing these core concepts will help you troubleshoot issues and optimize performance.
</p>

  <h3>Scrcpy</h3>
  <p>Scrcpy (Screen Copy) is the dedicated, high-performance application that executes the screen mirroring. It works by pushing a small server program onto the Android device via ADB. This server captures the device's screen contents and uses the phone's <strong>hardware video encoder</strong> (H.264) to rapidly compress the video stream. This highly efficient stream is then sent through the ADB tunnel to the PC, where the Scrcpy application quickly decodes and displays it. This method ensures <strong>minimal latency</strong> suitable for live video.</p>

  <h3>ADB - Android Debug Bridge</h3>
  <p>ADB is the <strong>low-level communication protocol</strong> that creates a high-bandwidth, stable connection (a "tunnel") between your Windows PC and the Android device, usually over the USB cable. Scrcpy relies entirely on ADB to provide the dedicated pipe through which the compressed video data travels. ADB is the <strong>backbone</strong> that enables all PC-to-Android debugging and data transfer.</p>

  <img src='./figs/adb-schema.png' alt='adb schema'>

  The ADB Client on the Host Machine : is the command-line program (adb) or a software interface (like in Android Studio) that sends debugging and operational commands to the ADB Server.



<h2>Demo</h2>

<p>
This demo section doesn’t show the entire setup process — only the key parts that matter most in practice. 
It focuses on what you actually see on your PC screen after starting <code>scrcpy</code> 
and how different connected devices perform during mirroring.
</p>

<h3>pc - phone connection</h3>

The following image show what happen after you invoke scrcpy from the command line - you see the android device on the pc screen. 
Make sure USB debugging is enabled on your Android phone.

<img src='./figs/run-scrcpy.png'/>


Once you click the app partner tv + and start watching, it rotate and the pc screen will be occupied at its full

<h3>connected devices</h3>

THe tablet has 15% better resolution but no audio 

<img src='./figs/devices.png'/>


<h2>Points of interest</h2>
<ul>
    <li><strong>Should I use a cable or Wi-Fi?</strong> You should use a <strong>USB cable</strong> for the best experience, as it provides extremely low latency and a more stable connection, which is ideal for watching live sports</li>
    <li><strong>Should I use a special cable?</strong> You should use any <strong>standard USB data cable</strong> (not a cheap "charge-only" cable) that supports the full file-sharing and adb data transfer required for debugging.</li>
   <li><strong>Do I need a developer account?</strong> No, you do not need a developer account, but you must <strong>enable the Developer Options and USB Debugging</strong> settings on your Android phone.</li>
</ul>




