# High vulnerabilities in Curl and Libcurl

The maintainers of curl, the popular command-line tool and library for transferring data with URLs, will release curl 8.4.0 on October 11, 2023. This version will include a fix for two common vulnerabilities and exposures (CVEs), one of which the curl maintainers rate as “HIGH” severity and described as “probably the worst curl security flaw in a long time.”

The CVE IDs are:

#### [CVE-2023-38545](https://curl.se/docs/CVE-2023-38545.html): severity HIGH (affects both libcurl and the curl tool)

- SOCKS5 heap buffer overflow
- In short, if you using sock5 proxy server with curl, you are at risk

#### [CVE-2023-38546](https://curl.se/docs/CVE-2023-38546.html): severity LOW (affects libcurl only, not the tool)

- allow attacker to insert cookies into running programme if the condition are met (it is low severity because it required quite a few number of condition)

---

# Recommendation

Both Windows and MacOS have pre-installed curl version. It's not easy to patch those pre-installed versions. Hence we suggest to wait for system patches issued by operating system vendors.

If you have installed curl/libcurl by yourself (e.g. in your MacOS, or any VM/container you manage on your machine), you should upgrade that curl/libcurl to latest version now.

---

## Patching Curl on Windows:

**Recommendation**: Wait for an official patch from Microsoft whenever possible, as manual patching can potentially disrupt OS updates.

## Patching Curl on macOS:

**Recommendation**: On macOS, you can use Homebrew to easily install and manage curl, and it won't disrupt the macOS version of curl.

- **Install curl using Homebrew**:

```shell
brew install curl
```

- **Make Brew Curl the default in your shell**:

```shell
echo 'export PATH="$(brew --prefix)/opt/curl/bin:$PATH"' >> ~/.zshrc
```

- **Source the Updated Configuration**:

```shell
ource ~/.zshrc
```

> Note: When patches for macOS become available, it is also recommended to promptly update your macOS system to ensure security and compatibility.

## Patching Curl on Linux:

**Recommendation**: On Linux, choose the patch that's compatible with your specific Linux distribution. Visit the [official documentation](https://everything.curl.dev/get/linux) for detailed instructions

Follow the documentation provided on the above link for your Linux distribution to ensure a successful and compatible Curl patch installation.

..
.

---

Reference:

- [Github Discussion](https://github.com/curl/curl/discussions/12026)
