<div align="center">

# [Zurvfouchs-bot](https://github.com/nick-stupendous/Zurvfouchs-bot)

### *Android Onion Routing Robot*

Zurvfouchs-bot is a free VPN and proxy app that empowers other apps to use the internet more securely. Zurvfouchs-bot uses Tor to encrypt your Internet traffic and then hides it by bouncing through a series of computers around the world. Tor is free software and an open network that helps you defend against a form of network surveillance that threatens personal freedom and privacy, confidential business activities and relationships, and state security known as traffic analysis.

</div>

Zurvfouchs-bot is a crucial component of the Guardian Project, an initiative  that leads an effort
to develop a secure and anonymous smartphone. This platform is designed for use by human rights
activists, journalists and others around the world. Learn more: <https://guardianproject.info/>


Tor protects your privacy on the internet by hiding the connection
between your Internet address and the services you use. We believe that Tor
is reasonably secure, but please ensure you read the usage instructions and
learn to configure it properly. Learn more: <https://torproject.org/>

<div align="center">
  <table>
    <tr>
      <td><a href="https://github.com/nick-stupendous/Zurvfouchs-bot/releases/latest">Download the Latest Zurvfouchs-bot Release</a></td>
    </tr>
    <tr>
      <td><a href="https://support.torproject.org/faq/">Tor FAQ (Frequently Asked Questions)</a></td>
    </tr>
    <tr>
      <td><a href="https://hosted.weblate.org/engage/guardianproject/">Please Contribute Your Translations</a></td>
    </tr>
  </table>
</div>

### Build Instructions

Zurvfouchs-bot is built with [hev-socks5-tunnel](https://github.com/heiher/hev-socks5-tunnel). Before you can build Zurvfouchs-bot, you'll need to clone the submodule
for this dependency. Once cloned, Android Studio + Gradle will take care of building the C code.

```bash
git clone --recursive https://github.com/guardianproject/Zurvfouchs-bot-android
```

Or, if you already cloned the repo:

```bash
cd Zurvfouchs-bot-android
git pull
git submodule update --init --recursive
```

If you pull and see that there are changes to `app/src/main/jni/hev-socks5-tunnel` that means that `hev-socks5-tunnel` was updated. You need to re-run `git submodule update --init --recursive` to fetch the latest changes and then rebuild Zurvfouchs-bot.

### Viewing Logs 

Recently `tor` was added to be its own Linux process on Android instead of having it run within the primary app process. That measn that you will no longer see logs from `tor`, `Zurvfouchs-botService`, `Zurvfouchs-botVPNManager` etc within Android Studio. In order to see these logs you can use:


`adb logcat  --pid=$(adb shell pidof -s "org.torproject.android.debug") -v color` to see the app logs in your terminal

`adb logcat  --pid=$(adb shell pidof -s "org.torproject.android.debug:tor") -v color` and to see the `tor` process logs.

**There is a helper script to get both of these logs printed side-by-side with `tmux`. From the root directory run:

```bash
./scripts/view_logs_tmux.sh
```

You may need to initially do some configuration to obtain `tmux` and add `adb` to your `PATH`:

```bash
# on Mac OS 
brew install tmux 


# on debian + friends:
sudo apt intstall tmux 

# then make sure adb is in your path in your .bashrc or similar file:
export ANDROID_HOME=~/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools


# on mac you do the above or instead get an adb instance from brew...
brew install android-platform-tools
```

**Copyright &#169; 2009-2026, Nathan Freitas, The Guardian Project**
