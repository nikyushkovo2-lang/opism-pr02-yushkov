# Практична робота № 2

**Дисципліна:** Основи побудови інформаційних систем та мереж (ОК-13)

**Тема:** Структура повідомлень прикладного протоколу HTTP. Формування запиту вручну

| Поле | Значення |
|---|---|
| Студент | Юшков Микита Олександрович |
| Група | 21 |
| Номер варіанта | 8 |
| Індивідуальний домен | `netbsd.org` |
| Чужий домен (варіант +15) | `nau.edu.ua` |
| Середовище виконання | Windows (PowerShell) |
| Дата виконання | 24.11.2026 |

## Частина A. Збір експериментальних даних

Запити A.1–A.4 сформовано вручну у змінній за Додатком Г. Повні виводи наведено нижче.

### Завдання A.1. Формування запиту вручну

Команда:

```powershell
$d = "netbsd.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 80)
$s = $c.GetStream()
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET / HTTP/1.1`r`nHost: $d`r`nConnection: close`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a1-manual.txt
$c.Close()
```

**Текст запиту (передано через `$w.Write()`):**

```http
GET / HTTP/1.1
Host: netbsd.org
Connection: close

```

Вивід:

```text
HTTP/1.1 200 OK
Date: Tue, 24 Nov 2026 09:54:20 GMT
Server: Apache/2.4.62 (Unix)
Last-Modified: Tue, 03 Nov 2026 21:30:03 GMT
ETag: "3194-65f65f72f7593"
Accept-Ranges: bytes
Content-Length: 12692
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Connection: close
Content-Type: text/html

<!DOCTYPE html>

<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <!-- Copyright (c) 1994-2026
	 The NetBSD Foundation, Inc.  ALL RIGHTS RESERVED. -->
    <link rel="author" href="mailto:www@NetBSD.org">
    <link rel="shortcut icon" href="./favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="global.css" type="text/css">
    <link rel="stylesheet" href="donations/thermo/fundraiser.css" type="text/css">
    <link rel="alternate" type="application/rss+xml" title="NetBSD news"
	  href="//www.NetBSD.org/changes/rss-netbsd.xml">
    <title>The NetBSD Project</title>
    <meta name="verify-v1" content="guJT5SZUh4XMF/emgSnXZPc6GkWkhP7PvMdYBc/auJI=">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
  </head>

  <body class="website"><div class="webpage">
    <!-- For non-visual user agents: -->
    <div id="top"><a href="#mainContent" id="skiplink" tabindex="1">Skip to main content.</a></div>

      <!-- mobile menu icon -->
      <input id="hamburger" type="checkbox">
      <label class="menuicon" for="hamburger"><span></span><span></span><span></span></label>

      <div id="navBar" role="navigation">
      <div id="centralHeader">
	<div id="logo">
		<a href="./"><img id="projectLogo" src="./images/NetBSD-smaller-tb.png" alt="" height="120"></a>
	</div>
	<a href="//www.NetBSD.org/donations/#how-to-donate">
		<div id="fundraiser">
			<br>
			<div id="fundraiser-amount">
				<div id="fundraiser-raised"></div>
			</div>
		</div>
  	</a>
        </div>
	<span class="doNotDisplay">
          Navigation:
        </span>
	<ul>
	<li><a href="./">
		  Home</a><ul>
	<li><a href="./changes/">
		    Recent changes</a></li>
	<li><a href="//blog.NetBSD.org/">
		    NetBSD blog</a></li>
	<li><a href="./gallery/presentations/">
		    Presentations</a></li>
	</ul>
	</li>
	<li>
	<a href="./about/">
		  About</a><ul>
	<li><a href="./people/developers.html">
		    Developers</a></li>
	<li><a href="./gallery/">
		    Gallery</a></li>
	<li><a href="//wiki.NetBSD.org/ports/">
		    Ports</a></li>
	<li><a href="//www.pkgsrc.org/">
		    Packages</a></li>
	</ul>
	</li>
	<li>
	<a href="./docs/">
		  Documentation</a><ul>
	<li><a href="./docs/misc/index.html">
		    FAQ &amp; HOWTOs</a></li>
	<li><a href="./docs/guide/en/">
		    The Guide</a></li>
	<li><a href="//man.NetBSD.org/">
		    Manual pages</a></li>
	<li><a href="//wiki.NetBSD.org/">
		    Wiki</a></li>
	</ul>
	</li>
	<li>
	<a href="./support/">
		  Support</a><ul>
	<li><a href="./community/">
		    Community</a></li>
	<li><a href="./mailinglists/">
		    Mailing lists</a></li>
	<li><a href="./support/send-pr.html">
		    Bug reports</a></li>
	<li><a href="./support/security/">
		    Security</a></li>
	</ul>
	</li>
	<li>
	<a href="./developers/">
		  Developers</a><ul>
	<li><a href="//cvsweb.NetBSD.org/">
		    CVSWeb</a></li>
	<li><a href="//nxr.NetBSD.org/">
		    Cross-reference</a></li>
	<li><a href="//releng.NetBSD.org/">
		    Release engineering</a></li>
	<li><a href="//wiki.NetBSD.org/projects/">
		    Projects list</a></li>
	</ul>
	</li>
	</ul>
      </div>

    <div id="content">
      <div id="mainContent">
          <h1>The NetBSD Project</h1>
	  <p class="twoThirds">
	    NetBSD is a free, fast, secure, and highly portable Unix-like
	    Open Source operating system. It is available for a wide
	    range of platforms, from large-scale servers and powerful
	    desktop systems to handheld and embedded devices.
	  </p>
	  <p>
	    <span class="more"><a href="./about/">&raquo;&nbsp;Learn more</a></span>
	  </p>
	  <h2>11.1 available!</h2>
	  <p>
	          The NetBSD project is pleased to announce
		  <span class="more">
  		  <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;NetBSD 11.1&nbsp;&laquo;</a></span>,
		  the first update to the nineteenth major release of NetBSD.
	  </p>
	  <h2><img src="images/download-icon-orange.png" alt="" class="icon">Get NetBSD</h2>
<div class="itemizedlist">
      <p>
	NetBSD 11.1, released on November 2, 2026.
        <span class="more">
          <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;Release Notes&nbsp;&laquo;</a></span>
    <div class="informaltable">

<table class="downloadtable">
  <thead><tr>
    <th style="text-align:left">CPU</th>
    <th style="text-align:left">Machines</th>
    <th style="text-align:left">Install media</th>
  </tr></thead>
  <tbody>
    <tr>
      <td><a class="ulink" href="//wiki.NetBSD.org/ports/amd64/" target="_top">amd64</a></td>
      <td>64-bit x86-family machines with AMD or Intel CPUs</td>
      <td>
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-install.img.gz" target="_top">USB image</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-dvd.iso" target="_top">DVD</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64.iso" target="_top">CD</a>
      </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">arm</a></td>
    <td>
      ARM systems like Raspberry Pi, PINE64, ODROID,
      "ServerReady" machines
      <a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">more</a>
    </td>
    <td>
      <a class="ulink" href="https://armbsd.org" target="_top">Various boards</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbarm-earmv6hf/binary/gzimg/rpi.img.gz" target="_top">original RPi</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/i386/" target="_top">i386</a></td>
    <td>32-bit x86-family generic machines</td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-install.img.gz" target="_top">USB image</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-dvd.iso" target="_top">DVD</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386.iso" target="_top">CD</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbmips/" target="_top">mips</a></td>
    <td>
      MIPS systems like EdgeRouter, Loongson, Malta
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64eb/binary/gzimg/octeon.img.gz" target="_top">octeon</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64el" target="_top">mips64el</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mipsel" target="_top">mipsel</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbppc/" target="_top">powerpc</a></td>
    <td>
      PowerPC systems like Nintendo Wii, DHT Walnut, RouterBOARD
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/binary/gzimg/wii.img.gz" target="_top">wii</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/" target="_top">others</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/sparc64/" target="_top">sparc64</a></td>
    <td>Sun UltraSPARC</td>
    <td>
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64-dvd.iso" target="_top">DVD</a>,
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64.iso" target="_top">CD</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">others</a></td>
    <td>
      Amiga, Alpha, Apple PowerPC/68K, Dreamcast, SPARC32, VAX,
      <a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">more architectures</a>
    </td>
  <td><a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images" target="_top">various</a></td>
  </tr>
  </tbody>
</table>
    </div>
<p><span class="more">
  <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/hashes/NetBSD-11.1_hashes.asc" target="_top">
    A signed list of hashes for the NetBSD 11.1 distribution.
  </a>
</span><br>
   The <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/PGP/security-officer@netbsd.org.asc">NetBSD Security Officer's
   PGP key</a> used to sign the list of hashes.</p>

	<h2><img src="images/donate-icon-orange.png" alt="" class="icon">Donate</h2>
		<p>
		Donations to The NetBSD Foundation allow the project to purchase
		build hardware and fund development.<br>
		Some recently funded projects are:
		</p>
		<ul>
			<li><a href="http://victory.NetBSD.org/pkgsrc/packages/reports/HEAD/evbarm64-9.0/">arm64 package build server</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/wifi_renewal_restarted">Wi-Fi renewal</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/lldb_now_works_on_i386">LLDB and upstream LLVM support</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/accomplishment_of_porting_ptrace_2">ptrace and GDB improvements</a></li>
		</ul>
		Please consider <a href="/donations/">donating</a> if you would like to see more of this work:
		<ul class="donationLinks">
			<li><a href="https://www.NetBSD.org/stripe.html">
			<img src="images/donate-icon-stripe.png" alt="" height="16">
			Donate using Stripe</a></li>
			<li><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=paypal%40NetBSD.org&currency_code=USD&source=url">
			<img src="images/donate-icon-paypal.png" alt="" height="16">
			Donate or Subscribe with PayPal</a></li>
			<li><a href="https://github.com/sponsors/NetBSD">
			<img src="images/donate-icon-github.png" alt="" height="16">
			Sponsor NetBSD on GitHub</a></li>
		</ul>
	  </div>


      <div id="news">
	  <h2><img src="images/develop-icon-orange.png" alt="" class="icon">Latest News (<a href="//www.NetBSD.org/changes/rss-netbsd.xml">RSS</a>)</h2>
	  <ul>

	    <!-- this part automatically generated from changes/index.html through
		 Makefile-magic -->

	    <!-- NEWS::START -->
<li><a href="changes/#netbsd11.1">NetBSD 11.1 available</a><br/>2 November 2026</li>
<li><a href="changes/#netbsd10.2">NetBSD 10.2 available</a><br/>15 September 2026</li>
<li><a href="changes/#netbsd9.5">NetBSD 9.5 available and EOL for netbsd-9</a><br/>31 August 2026</li>
<li><a href="changes/#netbsd11.0">NetBSD 11.0 available</a><br/>30 July 2026</li>
	    <!-- NEWS::END -->
	  </ul>

	  <!-- this part automatically generated from gallery/events.html through
	       Makefile-magic -->

	    <!-- EVENTS::START -->
	<h3>Upcoming Events</h3>
	<ul>
<li><a href="gallery/events.html#fosdem2027">FOSDEM '27, Brussels, Belgium</a><br/>Jan 2027</li>
<li><a href="gallery/events.html#asiabsdcon2027">AsiaBSDCon 2027, Tokyo, Japan</a><br/>Mar 2027</li>
<li><a href="gallery/events.html#bsdcan2027">BSDCan 2027, Vancouver, Canada</a><br/>July 2027</li>
<li><a href="gallery/events.html#eurobsdcon2027">EuroBSDcon 2027, Bratislava, Slovakia</a><br/>Sep 2027</li>
	  <li>
	    <span class="more">
	      <a href="gallery/events.html">&raquo; Archive</a>
	    </span>
	  </li>
	</ul>
	    <!-- EVENTS::END -->
      </div>
      </div> <!-- mainContent -->


    <!-- ##### Footer ##### -->
    <!-- $NetBSD: index.html,v 1.2237 2026/11/03 20:37:05 nia Exp $ -->
	<div id="footerLogo" style="vertical-align: middle; display: flex; align-items: baseline; justify-content: center;">
		<a href="//www.wwu.edu"><img src="images/westernlogo_sm.png" class="sponsor" alt="Western Washington University, sponsor"></a>
		<a href="//www.columbia.edu"><img src="images/columbia.jpg" class="sponsor" alt="Columbia University, sponsor"></a>
		<a href="//www.fastly.com"><img src="images/fastly.png" class="sponsor" alt="fastly, sponsor"></a>
		<a href="//www.twosigma.com"><img src="images/twosigma_logo.png" class="sponsor" alt="Two Sigma Investments, LLC, sponsor"></a>
		<a href="//futo.tech"><img src="images/FUTO_regular.png" class="sponsor" alt="FUTO, sponsor"></a>
	</div>
    </div>
    <div id="footer">
      <div class="rowOfBoxes">
	<div id="footerContent">
	  <span class="footfeed">
	    <a href="//www.NetBSD.org/cgi-bin/feedback.cgi">
	      Contact</a> |
	  </span>
	  <span class="footcopy"><a href="about/disclaimer.html">
	    Disclaimer</a> |
	    <span class="copyright">
	      Copyright &copy; 1994-2026 The NetBSD Foundation, Inc.
	    </span>
	    ALL RIGHTS RESERVED.<br>
	    NetBSD<sup>&reg;</sup> is a registered trademark of The NetBSD Foundation, Inc.
	  </span>
	</div>
      </div>
    </div>
  </div></body>
</html>
```

---

### Завдання A.2. Запит без поля `Host` у версії 1.1

Команда:

```powershell
$d = "netbsd.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 80)
$s = $c.GetStream()
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET / HTTP/1.1`r`nConnection: close`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a2-nohost-11.txt
$c.Close()
```

Вивід:

```text
HTTP/1.1 400 Bad Request
Date: Tue, 24 Nov 2026 09:55:33 GMT
Server: Apache/2.4.62 (Unix)
Content-Length: 226
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
</p>
</body></html>
```

---

### Завдання A.3. Вплив поля `Host` на відповідь сервера

#### A.3.1. Чуже доменне ім’я в полі `Host`

Команда:

```powershell
$d = "netbsd.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 80)
$s = $c.GetStream()
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET / HTTP/1.1`r`nHost: nau.edu.ua`r`nConnection: close`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a3-1-foreign-host.txt
$c.Close()
```

Вивід:

```text
HTTP/1.1 200 OK
Date: Tue, 24 Nov 2026 09:57:14 GMT
Server: Apache/2.4.62 (Unix)
Last-Modified: Tue, 03 Nov 2026 21:30:03 GMT
ETag: "3194-65f65f72f7593"
Accept-Ranges: bytes
Content-Length: 12692
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Connection: close
Content-Type: text/html

<!DOCTYPE html>

<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <!-- Copyright (c) 1994-2026
	 The NetBSD Foundation, Inc.  ALL RIGHTS RESERVED. -->
    <link rel="author" href="mailto:www@NetBSD.org">
    <link rel="shortcut icon" href="./favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="global.css" type="text/css">
    <link rel="stylesheet" href="donations/thermo/fundraiser.css" type="text/css">
    <link rel="alternate" type="application/rss+xml" title="NetBSD news"
	  href="//www.NetBSD.org/changes/rss-netbsd.xml">
    <title>The NetBSD Project</title>
    <meta name="verify-v1" content="guJT5SZUh4XMF/emgSnXZPc6GkWkhP7PvMdYBc/auJI=">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
  </head>

  <body class="website"><div class="webpage">
    <!-- For non-visual user agents: -->
    <div id="top"><a href="#mainContent" id="skiplink" tabindex="1">Skip to main content.</a></div>

      <!-- mobile menu icon -->
      <input id="hamburger" type="checkbox">
      <label class="menuicon" for="hamburger"><span></span><span></span><span></span></label>

      <div id="navBar" role="navigation">
      <div id="centralHeader">
	<div id="logo">
		<a href="./"><img id="projectLogo" src="./images/NetBSD-smaller-tb.png" alt="" height="120"></a>
	</div>
	<a href="//www.NetBSD.org/donations/#how-to-donate">
		<div id="fundraiser">
			<br>
			<div id="fundraiser-amount">
				<div id="fundraiser-raised"></div>
			</div>
		</div>
  	</a>
        </div>
	<span class="doNotDisplay">
          Navigation:
        </span>
	<ul>
	<li><a href="./">
		  Home</a><ul>
	<li><a href="./changes/">
		    Recent changes</a></li>
	<li><a href="//blog.NetBSD.org/">
		    NetBSD blog</a></li>
	<li><a href="./gallery/presentations/">
		    Presentations</a></li>
	</ul>
	</li>
	<li>
	<a href="./about/">
		  About</a><ul>
	<li><a href="./people/developers.html">
		    Developers</a></li>
	<li><a href="./gallery/">
		    Gallery</a></li>
	<li><a href="//wiki.NetBSD.org/ports/">
		    Ports</a></li>
	<li><a href="//www.pkgsrc.org/">
		    Packages</a></li>
	</ul>
	</li>
	<li>
	<a href="./docs/">
		  Documentation</a><ul>
	<li><a href="./docs/misc/index.html">
		    FAQ &amp; HOWTOs</a></li>
	<li><a href="./docs/guide/en/">
		    The Guide</a></li>
	<li><a href="//man.NetBSD.org/">
		    Manual pages</a></li>
	<li><a href="//wiki.NetBSD.org/">
		    Wiki</a></li>
	</ul>
	</li>
	<li>
	<a href="./support/">
		  Support</a><ul>
	<li><a href="./community/">
		    Community</a></li>
	<li><a href="./mailinglists/">
		    Mailing lists</a></li>
	<li><a href="./support/send-pr.html">
		    Bug reports</a></li>
	<li><a href="./support/security/">
		    Security</a></li>
	</ul>
	</li>
	<li>
	<a href="./developers/">
		  Developers</a><ul>
	<li><a href="//cvsweb.NetBSD.org/">
		    CVSWeb</a></li>
	<li><a href="//nxr.NetBSD.org/">
		    Cross-reference</a></li>
	<li><a href="//releng.NetBSD.org/">
		    Release engineering</a></li>
	<li><a href="//wiki.NetBSD.org/projects/">
		    Projects list</a></li>
	</ul>
	</li>
	</ul>
      </div>

    <div id="content">
      <div id="mainContent">
          <h1>The NetBSD Project</h1>
	  <p class="twoThirds">
	    NetBSD is a free, fast, secure, and highly portable Unix-like
	    Open Source operating system. It is available for a wide
	    range of platforms, from large-scale servers and powerful
	    desktop systems to handheld and embedded devices.
	  </p>
	  <p>
	    <span class="more"><a href="./about/">&raquo;&nbsp;Learn more</a></span>
	  </p>
	  <h2>11.1 available!</h2>
	  <p>
	          The NetBSD project is pleased to announce
		  <span class="more">
  		  <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;NetBSD 11.1&nbsp;&laquo;</a></span>,
		  the first update to the nineteenth major release of NetBSD.
	  </p>
	  <h2><img src="images/download-icon-orange.png" alt="" class="icon">Get NetBSD</h2>
<div class="itemizedlist">
      <p>
	NetBSD 11.1, released on November 2, 2026.
        <span class="more">
          <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;Release Notes&nbsp;&laquo;</a></span>
    <div class="informaltable">

<table class="downloadtable">
  <thead><tr>
    <th style="text-align:left">CPU</th>
    <th style="text-align:left">Machines</th>
    <th style="text-align:left">Install media</th>
  </tr></thead>
  <tbody>
    <tr>
      <td><a class="ulink" href="//wiki.NetBSD.org/ports/amd64/" target="_top">amd64</a></td>
      <td>64-bit x86-family machines with AMD or Intel CPUs</td>
      <td>
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-install.img.gz" target="_top">USB image</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-dvd.iso" target="_top">DVD</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64.iso" target="_top">CD</a>
      </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">arm</a></td>
    <td>
      ARM systems like Raspberry Pi, PINE64, ODROID,
      "ServerReady" machines
      <a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">more</a>
    </td>
    <td>
      <a class="ulink" href="https://armbsd.org" target="_top">Various boards</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbarm-earmv6hf/binary/gzimg/rpi.img.gz" target="_top">original RPi</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/i386/" target="_top">i386</a></td>
    <td>32-bit x86-family generic machines</td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-install.img.gz" target="_top">USB image</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-dvd.iso" target="_top">DVD</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386.iso" target="_top">CD</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbmips/" target="_top">mips</a></td>
    <td>
      MIPS systems like EdgeRouter, Loongson, Malta
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64eb/binary/gzimg/octeon.img.gz" target="_top">octeon</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64el" target="_top">mips64el</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mipsel" target="_top">mipsel</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbppc/" target="_top">powerpc</a></td>
    <td>
      PowerPC systems like Nintendo Wii, DHT Walnut, RouterBOARD
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/binary/gzimg/wii.img.gz" target="_top">wii</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/" target="_top">others</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/sparc64/" target="_top">sparc64</a></td>
    <td>Sun UltraSPARC</td>
    <td>
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64-dvd.iso" target="_top">DVD</a>,
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64.iso" target="_top">CD</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">others</a></td>
    <td>
      Amiga, Alpha, Apple PowerPC/68K, Dreamcast, SPARC32, VAX,
      <a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">more architectures</a>
    </td>
  <td><a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images" target="_top">various</a></td>
  </tr>
  </tbody>
</table>
    </div>
<p><span class="more">
  <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/hashes/NetBSD-11.1_hashes.asc" target="_top">
    A signed list of hashes for the NetBSD 11.1 distribution.
  </a>
</span><br>
   The <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/PGP/security-officer@netbsd.org.asc">NetBSD Security Officer's
   PGP key</a> used to sign the list of hashes.</p>

	<h2><img src="images/donate-icon-orange.png" alt="" class="icon">Donate</h2>
		<p>
		Donations to The NetBSD Foundation allow the project to purchase
		build hardware and fund development.<br>
		Some recently funded projects are:
		</p>
		<ul>
			<li><a href="http://victory.NetBSD.org/pkgsrc/packages/reports/HEAD/evbarm64-9.0/">arm64 package build server</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/wifi_renewal_restarted">Wi-Fi renewal</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/lldb_now_works_on_i386">LLDB and upstream LLVM support</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/accomplishment_of_porting_ptrace_2">ptrace and GDB improvements</a></li>
		</ul>
		Please consider <a href="/donations/">donating</a> if you would like to see more of this work:
		<ul class="donationLinks">
			<li><a href="https://www.NetBSD.org/stripe.html">
			<img src="images/donate-icon-stripe.png" alt="" height="16">
			Donate using Stripe</a></li>
			<li><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=paypal%40NetBSD.org&currency_code=USD&source=url">
			<img src="images/donate-icon-paypal.png" alt="" height="16">
			Donate or Subscribe with PayPal</a></li>
			<li><a href="https://github.com/sponsors/NetBSD">
			<img src="images/donate-icon-github.png" alt="" height="16">
			Sponsor NetBSD on GitHub</a></li>
		</ul>
	  </div>


      <div id="news">
	  <h2><img src="images/develop-icon-orange.png" alt="" class="icon">Latest News (<a href="//www.NetBSD.org/changes/rss-netbsd.xml">RSS</a>)</h2>
	  <ul>

	    <!-- this part automatically generated from changes/index.html through
		 Makefile-magic -->

	    <!-- NEWS::START -->
<li><a href="changes/#netbsd11.1">NetBSD 11.1 available</a><br/>2 November 2026</li>
<li><a href="changes/#netbsd10.2">NetBSD 10.2 available</a><br/>15 September 2026</li>
<li><a href="changes/#netbsd9.5">NetBSD 9.5 available and EOL for netbsd-9</a><br/>31 August 2026</li>
<li><a href="changes/#netbsd11.0">NetBSD 11.0 available</a><br/>30 July 2026</li>
	    <!-- NEWS::END -->
	  </ul>

	  <!-- this part automatically generated from gallery/events.html through
	       Makefile-magic -->

	    <!-- EVENTS::START -->
	<h3>Upcoming Events</h3>
	<ul>
<li><a href="gallery/events.html#fosdem2027">FOSDEM '27, Brussels, Belgium</a><br/>Jan 2027</li>
<li><a href="gallery/events.html#asiabsdcon2027">AsiaBSDCon 2027, Tokyo, Japan</a><br/>Mar 2027</li>
<li><a href="gallery/events.html#bsdcan2027">BSDCan 2027, Vancouver, Canada</a><br/>July 2027</li>
<li><a href="gallery/events.html#eurobsdcon2027">EuroBSDcon 2027, Bratislava, Slovakia</a><br/>Sep 2027</li>
	  <li>
	    <span class="more">
	      <a href="gallery/events.html">&raquo; Archive</a>
	    </span>
	  </li>
	</ul>
	    <!-- EVENTS::END -->
      </div>
      </div> <!-- mainContent -->


    <!-- ##### Footer ##### -->
    <!-- $NetBSD: index.html,v 1.2237 2026/11/03 20:37:05 nia Exp $ -->
	<div id="footerLogo" style="vertical-align: middle; display: flex; align-items: baseline; justify-content: center;">
		<a href="//www.wwu.edu"><img src="images/westernlogo_sm.png" class="sponsor" alt="Western Washington University, sponsor"></a>
		<a href="//www.columbia.edu"><img src="images/columbia.jpg" class="sponsor" alt="Columbia University, sponsor"></a>
		<a href="//www.fastly.com"><img src="images/fastly.png" class="sponsor" alt="fastly, sponsor"></a>
		<a href="//www.twosigma.com"><img src="images/twosigma_logo.png" class="sponsor" alt="Two Sigma Investments, LLC, sponsor"></a>
		<a href="//futo.tech"><img src="images/FUTO_regular.png" class="sponsor" alt="FUTO, sponsor"></a>
	</div>
    </div>
    <div id="footer">
      <div class="rowOfBoxes">
	<div id="footerContent">
	  <span class="footfeed">
	    <a href="//www.NetBSD.org/cgi-bin/feedback.cgi">
	      Contact</a> |
	  </span>
	  <span class="footcopy"><a href="about/disclaimer.html">
	    Disclaimer</a> |
	    <span class="copyright">
	      Copyright &copy; 1994-2026 The NetBSD Foundation, Inc.
	    </span>
	    ALL RIGHTS RESERVED.<br>
	    NetBSD<sup>&reg;</sup> is a registered trademark of The NetBSD Foundation, Inc.
	  </span>
	</div>
      </div>
    </div>
  </div></body>
</html>
```

#### A.3.2. Неіснуюче ім’я в полі `Host`

Команда:

```powershell
$d = "netbsd.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 80)
$s = $c.GetStream()
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET / HTTP/1.1`r`nHost: opism-pr02.invalid`r`nConnection: close`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a3-2-invalid-host.txt
$c.Close()
```

Вивід:

```text
HTTP/1.1 200 OK
Date: Tue, 24 Nov 2026 09:58:09 GMT
Server: Apache/2.4.62 (Unix)
Last-Modified: Tue, 03 Nov 2026 21:30:03 GMT
ETag: "3194-65f65f72f7593"
Accept-Ranges: bytes
Content-Length: 12692
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Connection: close
Content-Type: text/html

<!DOCTYPE html>

<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <!-- Copyright (c) 1994-2026
	 The NetBSD Foundation, Inc.  ALL RIGHTS RESERVED. -->
    <link rel="author" href="mailto:www@NetBSD.org">
    <link rel="shortcut icon" href="./favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="global.css" type="text/css">
    <link rel="stylesheet" href="donations/thermo/fundraiser.css" type="text/css">
    <link rel="alternate" type="application/rss+xml" title="NetBSD news"
	  href="//www.NetBSD.org/changes/rss-netbsd.xml">
    <title>The NetBSD Project</title>
    <meta name="verify-v1" content="guJT5SZUh4XMF/emgSnXZPc6GkWkhP7PvMdYBc/auJI=">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
  </head>

  <body class="website"><div class="webpage">
    <!-- For non-visual user agents: -->
    <div id="top"><a href="#mainContent" id="skiplink" tabindex="1">Skip to main content.</a></div>

      <!-- mobile menu icon -->
      <input id="hamburger" type="checkbox">
      <label class="menuicon" for="hamburger"><span></span><span></span><span></span></label>

      <div id="navBar" role="navigation">
      <div id="centralHeader">
	<div id="logo">
		<a href="./"><img id="projectLogo" src="./images/NetBSD-smaller-tb.png" alt="" height="120"></a>
	</div>
	<a href="//www.NetBSD.org/donations/#how-to-donate">
		<div id="fundraiser">
			<br>
			<div id="fundraiser-amount">
				<div id="fundraiser-raised"></div>
			</div>
		</div>
  	</a>
        </div>
	<span class="doNotDisplay">
          Navigation:
        </span>
	<ul>
	<li><a href="./">
		  Home</a><ul>
	<li><a href="./changes/">
		    Recent changes</a></li>
	<li><a href="//blog.NetBSD.org/">
		    NetBSD blog</a></li>
	<li><a href="./gallery/presentations/">
		    Presentations</a></li>
	</ul>
	</li>
	<li>
	<a href="./about/">
		  About</a><ul>
	<li><a href="./people/developers.html">
		    Developers</a></li>
	<li><a href="./gallery/">
		    Gallery</a></li>
	<li><a href="//wiki.NetBSD.org/ports/">
		    Ports</a></li>
	<li><a href="//www.pkgsrc.org/">
		    Packages</a></li>
	</ul>
	</li>
	<li>
	<a href="./docs/">
		  Documentation</a><ul>
	<li><a href="./docs/misc/index.html">
		    FAQ &amp; HOWTOs</a></li>
	<li><a href="./docs/guide/en/">
		    The Guide</a></li>
	<li><a href="//man.NetBSD.org/">
		    Manual pages</a></li>
	<li><a href="//wiki.NetBSD.org/">
		    Wiki</a></li>
	</ul>
	</li>
	<li>
	<a href="./support/">
		  Support</a><ul>
	<li><a href="./community/">
		    Community</a></li>
	<li><a href="./mailinglists/">
		    Mailing lists</a></li>
	<li><a href="./support/send-pr.html">
		    Bug reports</a></li>
	<li><a href="./support/security/">
		    Security</a></li>
	</ul>
	</li>
	<li>
	<a href="./developers/">
		  Developers</a><ul>
	<li><a href="//cvsweb.NetBSD.org/">
		    CVSWeb</a></li>
	<li><a href="//nxr.NetBSD.org/">
		    Cross-reference</a></li>
	<li><a href="//releng.NetBSD.org/">
		    Release engineering</a></li>
	<li><a href="//wiki.NetBSD.org/projects/">
		    Projects list</a></li>
	</ul>
	</li>
	</ul>
      </div>

    <div id="content">
      <div id="mainContent">
          <h1>The NetBSD Project</h1>
	  <p class="twoThirds">
	    NetBSD is a free, fast, secure, and highly portable Unix-like
	    Open Source operating system. It is available for a wide
	    range of platforms, from large-scale servers and powerful
	    desktop systems to handheld and embedded devices.
	  </p>
	  <p>
	    <span class="more"><a href="./about/">&raquo;&nbsp;Learn more</a></span>
	  </p>
	  <h2>11.1 available!</h2>
	  <p>
	          The NetBSD project is pleased to announce
		  <span class="more">
  		  <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;NetBSD 11.1&nbsp;&laquo;</a></span>,
		  the first update to the nineteenth major release of NetBSD.
	  </p>
	  <h2><img src="images/download-icon-orange.png" alt="" class="icon">Get NetBSD</h2>
<div class="itemizedlist">
      <p>
	NetBSD 11.1, released on November 2, 2026.
        <span class="more">
          <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;Release Notes&nbsp;&laquo;</a></span>
    <div class="informaltable">

<table class="downloadtable">
  <thead><tr>
    <th style="text-align:left">CPU</th>
    <th style="text-align:left">Machines</th>
    <th style="text-align:left">Install media</th>
  </tr></thead>
  <tbody>
    <tr>
      <td><a class="ulink" href="//wiki.NetBSD.org/ports/amd64/" target="_top">amd64</a></td>
      <td>64-bit x86-family machines with AMD or Intel CPUs</td>
      <td>
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-install.img.gz" target="_top">USB image</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-dvd.iso" target="_top">DVD</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64.iso" target="_top">CD</a>
      </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">arm</a></td>
    <td>
      ARM systems like Raspberry Pi, PINE64, ODROID,
      "ServerReady" machines
      <a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">more</a>
    </td>
    <td>
      <a class="ulink" href="https://armbsd.org" target="_top">Various boards</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbarm-earmv6hf/binary/gzimg/rpi.img.gz" target="_top">original RPi</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/i386/" target="_top">i386</a></td>
    <td>32-bit x86-family generic machines</td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-install.img.gz" target="_top">USB image</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-dvd.iso" target="_top">DVD</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386.iso" target="_top">CD</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbmips/" target="_top">mips</a></td>
    <td>
      MIPS systems like EdgeRouter, Loongson, Malta
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64eb/binary/gzimg/octeon.img.gz" target="_top">octeon</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64el" target="_top">mips64el</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mipsel" target="_top">mipsel</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbppc/" target="_top">powerpc</a></td>
    <td>
      PowerPC systems like Nintendo Wii, DHT Walnut, RouterBOARD
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/binary/gzimg/wii.img.gz" target="_top">wii</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/" target="_top">others</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/sparc64/" target="_top">sparc64</a></td>
    <td>Sun UltraSPARC</td>
    <td>
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64-dvd.iso" target="_top">DVD</a>,
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64.iso" target="_top">CD</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">others</a></td>
    <td>
      Amiga, Alpha, Apple PowerPC/68K, Dreamcast, SPARC32, VAX,
      <a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">more architectures</a>
    </td>
  <td><a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images" target="_top">various</a></td>
  </tr>
  </tbody>
</table>
    </div>
<p><span class="more">
  <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/hashes/NetBSD-11.1_hashes.asc" target="_top">
    A signed list of hashes for the NetBSD 11.1 distribution.
  </a>
</span><br>
   The <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/PGP/security-officer@netbsd.org.asc">NetBSD Security Officer's
   PGP key</a> used to sign the list of hashes.</p>

	<h2><img src="images/donate-icon-orange.png" alt="" class="icon">Donate</h2>
		<p>
		Donations to The NetBSD Foundation allow the project to purchase
		build hardware and fund development.<br>
		Some recently funded projects are:
		</p>
		<ul>
			<li><a href="http://victory.NetBSD.org/pkgsrc/packages/reports/HEAD/evbarm64-9.0/">arm64 package build server</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/wifi_renewal_restarted">Wi-Fi renewal</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/lldb_now_works_on_i386">LLDB and upstream LLVM support</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/accomplishment_of_porting_ptrace_2">ptrace and GDB improvements</a></li>
		</ul>
		Please consider <a href="/donations/">donating</a> if you would like to see more of this work:
		<ul class="donationLinks">
			<li><a href="https://www.NetBSD.org/stripe.html">
			<img src="images/donate-icon-stripe.png" alt="" height="16">
			Donate using Stripe</a></li>
			<li><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=paypal%40NetBSD.org&currency_code=USD&source=url">
			<img src="images/donate-icon-paypal.png" alt="" height="16">
			Donate or Subscribe with PayPal</a></li>
			<li><a href="https://github.com/sponsors/NetBSD">
			<img src="images/donate-icon-github.png" alt="" height="16">
			Sponsor NetBSD on GitHub</a></li>
		</ul>
	  </div>


      <div id="news">
	  <h2><img src="images/develop-icon-orange.png" alt="" class="icon">Latest News (<a href="//www.NetBSD.org/changes/rss-netbsd.xml">RSS</a>)</h2>
	  <ul>

	    <!-- this part automatically generated from changes/index.html through
		 Makefile-magic -->

	    <!-- NEWS::START -->
<li><a href="changes/#netbsd11.1">NetBSD 11.1 available</a><br/>2 November 2026</li>
<li><a href="changes/#netbsd10.2">NetBSD 10.2 available</a><br/>15 September 2026</li>
<li><a href="changes/#netbsd9.5">NetBSD 9.5 available and EOL for netbsd-9</a><br/>31 August 2026</li>
<li><a href="changes/#netbsd11.0">NetBSD 11.0 available</a><br/>30 July 2026</li>
	    <!-- NEWS::END -->
	  </ul>

	  <!-- this part automatically generated from gallery/events.html through
	       Makefile-magic -->

	    <!-- EVENTS::START -->
	<h3>Upcoming Events</h3>
	<ul>
<li><a href="gallery/events.html#fosdem2027">FOSDEM '27, Brussels, Belgium</a><br/>Jan 2027</li>
<li><a href="gallery/events.html#asiabsdcon2027">AsiaBSDCon 2027, Tokyo, Japan</a><br/>Mar 2027</li>
<li><a href="gallery/events.html#bsdcan2027">BSDCan 2027, Vancouver, Canada</a><br/>July 2027</li>
<li><a href="gallery/events.html#eurobsdcon2027">EuroBSDcon 2027, Bratislava, Slovakia</a><br/>Sep 2027</li>
	  <li>
	    <span class="more">
	      <a href="gallery/events.html">&raquo; Archive</a>
	    </span>
	  </li>
	</ul>
	    <!-- EVENTS::END -->
      </div>
      </div> <!-- mainContent -->


    <!-- ##### Footer ##### -->
    <!-- $NetBSD: index.html,v 1.2237 2026/11/03 20:37:05 nia Exp $ -->
	<div id="footerLogo" style="vertical-align: middle; display: flex; align-items: baseline; justify-content: center;">
		<a href="//www.wwu.edu"><img src="images/westernlogo_sm.png" class="sponsor" alt="Western Washington University, sponsor"></a>
		<a href="//www.columbia.edu"><img src="images/columbia.jpg" class="sponsor" alt="Columbia University, sponsor"></a>
		<a href="//www.fastly.com"><img src="images/fastly.png" class="sponsor" alt="fastly, sponsor"></a>
		<a href="//www.twosigma.com"><img src="images/twosigma_logo.png" class="sponsor" alt="Two Sigma Investments, LLC, sponsor"></a>
		<a href="//futo.tech"><img src="images/FUTO_regular.png" class="sponsor" alt="FUTO, sponsor"></a>
	</div>
    </div>
    <div id="footer">
      <div class="rowOfBoxes">
	<div id="footerContent">
	  <span class="footfeed">
	    <a href="//www.NetBSD.org/cgi-bin/feedback.cgi">
	      Contact</a> |
	  </span>
	  <span class="footcopy"><a href="about/disclaimer.html">
	    Disclaimer</a> |
	    <span class="copyright">
	      Copyright &copy; 1994-2026 The NetBSD Foundation, Inc.
	    </span>
	    ALL RIGHTS RESERVED.<br>
	    NetBSD<sup>&reg;</sup> is a registered trademark of The NetBSD Foundation, Inc.
	  </span>
	</div>
      </div>
    </div>
  </div></body>
</html>
```

#### A.3.3. Запит HTTP/1.0 без поля `Host`

Команда:

```powershell
$d = "netbsd.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 80)
$s = $c.GetStream()
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET / HTTP/1.0`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a3-3-http10.txt
$c.Close()
```

Вивід:

```text
HTTP/1.1 200 OK
Date: Tue, 24 Nov 2026 09:59:07 GMT
Server: Apache/2.4.62 (Unix)
Last-Modified: Tue, 03 Nov 2026 21:30:03 GMT
ETag: "3194-65f65f72f7593"
Accept-Ranges: bytes
Content-Length: 12692
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Connection: close
Content-Type: text/html

<!DOCTYPE html>

<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <!-- Copyright (c) 1994-2026
	 The NetBSD Foundation, Inc.  ALL RIGHTS RESERVED. -->
    <link rel="author" href="mailto:www@NetBSD.org">
    <link rel="shortcut icon" href="./favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="global.css" type="text/css">
    <link rel="stylesheet" href="donations/thermo/fundraiser.css" type="text/css">
    <link rel="alternate" type="application/rss+xml" title="NetBSD news"
	  href="//www.NetBSD.org/changes/rss-netbsd.xml">
    <title>The NetBSD Project</title>
    <meta name="verify-v1" content="guJT5SZUh4XMF/emgSnXZPc6GkWkhP7PvMdYBc/auJI=">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
  </head>

  <body class="website"><div class="webpage">
    <!-- For non-visual user agents: -->
    <div id="top"><a href="#mainContent" id="skiplink" tabindex="1">Skip to main content.</a></div>

      <!-- mobile menu icon -->
      <input id="hamburger" type="checkbox">
      <label class="menuicon" for="hamburger"><span></span><span></span><span></span></label>

      <div id="navBar" role="navigation">
      <div id="centralHeader">
	<div id="logo">
		<a href="./"><img id="projectLogo" src="./images/NetBSD-smaller-tb.png" alt="" height="120"></a>
	</div>
	<a href="//www.NetBSD.org/donations/#how-to-donate">
		<div id="fundraiser">
			<br>
			<div id="fundraiser-amount">
				<div id="fundraiser-raised"></div>
			</div>
		</div>
  	</a>
        </div>
	<span class="doNotDisplay">
          Navigation:
        </span>
	<ul>
	<li><a href="./">
		  Home</a><ul>
	<li><a href="./changes/">
		    Recent changes</a></li>
	<li><a href="//blog.NetBSD.org/">
		    NetBSD blog</a></li>
	<li><a href="./gallery/presentations/">
		    Presentations</a></li>
	</ul>
	</li>
	<li>
	<a href="./about/">
		  About</a><ul>
	<li><a href="./people/developers.html">
		    Developers</a></li>
	<li><a href="./gallery/">
		    Gallery</a></li>
	<li><a href="//wiki.NetBSD.org/ports/">
		    Ports</a></li>
	<li><a href="//www.pkgsrc.org/">
		    Packages</a></li>
	</ul>
	</li>
	<li>
	<a href="./docs/">
		  Documentation</a><ul>
	<li><a href="./docs/misc/index.html">
		    FAQ &amp; HOWTOs</a></li>
	<li><a href="./docs/guide/en/">
		    The Guide</a></li>
	<li><a href="//man.NetBSD.org/">
		    Manual pages</a></li>
	<li><a href="//wiki.NetBSD.org/">
		    Wiki</a></li>
	</ul>
	</li>
	<li>
	<a href="./support/">
		  Support</a><ul>
	<li><a href="./community/">
		    Community</a></li>
	<li><a href="./mailinglists/">
		    Mailing lists</a></li>
	<li><a href="./support/send-pr.html">
		    Bug reports</a></li>
	<li><a href="./support/security/">
		    Security</a></li>
	</ul>
	</li>
	<li>
	<a href="./developers/">
		  Developers</a><ul>
	<li><a href="//cvsweb.NetBSD.org/">
		    CVSWeb</a></li>
	<li><a href="//nxr.NetBSD.org/">
		    Cross-reference</a></li>
	<li><a href="//releng.NetBSD.org/">
		    Release engineering</a></li>
	<li><a href="//wiki.NetBSD.org/projects/">
		    Projects list</a></li>
	</ul>
	</li>
	</ul>
      </div>

    <div id="content">
      <div id="mainContent">
          <h1>The NetBSD Project</h1>
	  <p class="twoThirds">
	    NetBSD is a free, fast, secure, and highly portable Unix-like
	    Open Source operating system. It is available for a wide
	    range of platforms, from large-scale servers and powerful
	    desktop systems to handheld and embedded devices.
	  </p>
	  <p>
	    <span class="more"><a href="./about/">&raquo;&nbsp;Learn more</a></span>
	  </p>
	  <h2>11.1 available!</h2>
	  <p>
	          The NetBSD project is pleased to announce
		  <span class="more">
  		  <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;NetBSD 11.1&nbsp;&laquo;</a></span>,
		  the first update to the nineteenth major release of NetBSD.
	  </p>
	  <h2><img src="images/download-icon-orange.png" alt="" class="icon">Get NetBSD</h2>
<div class="itemizedlist">
      <p>
	NetBSD 11.1, released on November 2, 2026.
        <span class="more">
          <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;Release Notes&nbsp;&laquo;</a></span>
    <div class="informaltable">

<table class="downloadtable">
  <thead><tr>
    <th style="text-align:left">CPU</th>
    <th style="text-align:left">Machines</th>
    <th style="text-align:left">Install media</th>
  </tr></thead>
  <tbody>
    <tr>
      <td><a class="ulink" href="//wiki.NetBSD.org/ports/amd64/" target="_top">amd64</a></td>
      <td>64-bit x86-family machines with AMD or Intel CPUs</td>
      <td>
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-install.img.gz" target="_top">USB image</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-dvd.iso" target="_top">DVD</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64.iso" target="_top">CD</a>
      </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">arm</a></td>
    <td>
      ARM systems like Raspberry Pi, PINE64, ODROID,
      "ServerReady" machines
      <a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">more</a>
    </td>
    <td>
      <a class="ulink" href="https://armbsd.org" target="_top">Various boards</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbarm-earmv6hf/binary/gzimg/rpi.img.gz" target="_top">original RPi</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/i386/" target="_top">i386</a></td>
    <td>32-bit x86-family generic machines</td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-install.img.gz" target="_top">USB image</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-dvd.iso" target="_top">DVD</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386.iso" target="_top">CD</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbmips/" target="_top">mips</a></td>
    <td>
      MIPS systems like EdgeRouter, Loongson, Malta
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64eb/binary/gzimg/octeon.img.gz" target="_top">octeon</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64el" target="_top">mips64el</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mipsel" target="_top">mipsel</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbppc/" target="_top">powerpc</a></td>
    <td>
      PowerPC systems like Nintendo Wii, DHT Walnut, RouterBOARD
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/binary/gzimg/wii.img.gz" target="_top">wii</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/" target="_top">others</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/sparc64/" target="_top">sparc64</a></td>
    <td>Sun UltraSPARC</td>
    <td>
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64-dvd.iso" target="_top">DVD</a>,
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64.iso" target="_top">CD</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">others</a></td>
    <td>
      Amiga, Alpha, Apple PowerPC/68K, Dreamcast, SPARC32, VAX,
      <a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">more architectures</a>
    </td>
  <td><a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images" target="_top">various</a></td>
  </tr>
  </tbody>
</table>
    </div>
<p><span class="more">
  <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/hashes/NetBSD-11.1_hashes.asc" target="_top">
    A signed list of hashes for the NetBSD 11.1 distribution.
  </a>
</span><br>
   The <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/PGP/security-officer@netbsd.org.asc">NetBSD Security Officer's
   PGP key</a> used to sign the list of hashes.</p>

	<h2><img src="images/donate-icon-orange.png" alt="" class="icon">Donate</h2>
		<p>
		Donations to The NetBSD Foundation allow the project to purchase
		build hardware and fund development.<br>
		Some recently funded projects are:
		</p>
		<ul>
			<li><a href="http://victory.NetBSD.org/pkgsrc/packages/reports/HEAD/evbarm64-9.0/">arm64 package build server</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/wifi_renewal_restarted">Wi-Fi renewal</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/lldb_now_works_on_i386">LLDB and upstream LLVM support</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/accomplishment_of_porting_ptrace_2">ptrace and GDB improvements</a></li>
		</ul>
		Please consider <a href="/donations/">donating</a> if you would like to see more of this work:
		<ul class="donationLinks">
			<li><a href="https://www.NetBSD.org/stripe.html">
			<img src="images/donate-icon-stripe.png" alt="" height="16">
			Donate using Stripe</a></li>
			<li><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=paypal%40NetBSD.org&currency_code=USD&source=url">
			<img src="images/donate-icon-paypal.png" alt="" height="16">
			Donate or Subscribe with PayPal</a></li>
			<li><a href="https://github.com/sponsors/NetBSD">
			<img src="images/donate-icon-github.png" alt="" height="16">
			Sponsor NetBSD on GitHub</a></li>
		</ul>
	  </div>


      <div id="news">
	  <h2><img src="images/develop-icon-orange.png" alt="" class="icon">Latest News (<a href="//www.NetBSD.org/changes/rss-netbsd.xml">RSS</a>)</h2>
	  <ul>

	    <!-- this part automatically generated from changes/index.html through
		 Makefile-magic -->

	    <!-- NEWS::START -->
<li><a href="changes/#netbsd11.1">NetBSD 11.1 available</a><br/>2 November 2026</li>
<li><a href="changes/#netbsd10.2">NetBSD 10.2 available</a><br/>15 September 2026</li>
<li><a href="changes/#netbsd9.5">NetBSD 9.5 available and EOL for netbsd-9</a><br/>31 August 2026</li>
<li><a href="changes/#netbsd11.0">NetBSD 11.0 available</a><br/>30 July 2026</li>
	    <!-- NEWS::END -->
	  </ul>

	  <!-- this part automatically generated from gallery/events.html through
	       Makefile-magic -->

	    <!-- EVENTS::START -->
	<h3>Upcoming Events</h3>
	<ul>
<li><a href="gallery/events.html#fosdem2027">FOSDEM '27, Brussels, Belgium</a><br/>Jan 2027</li>
<li><a href="gallery/events.html#asiabsdcon2027">AsiaBSDCon 2027, Tokyo, Japan</a><br/>Mar 2027</li>
<li><a href="gallery/events.html#bsdcan2027">BSDCan 2027, Vancouver, Canada</a><br/>July 2027</li>
<li><a href="gallery/events.html#eurobsdcon2027">EuroBSDcon 2027, Bratislava, Slovakia</a><br/>Sep 2027</li>
	  <li>
	    <span class="more">
	      <a href="gallery/events.html">&raquo; Archive</a>
	    </span>
	  </li>
	</ul>
	    <!-- EVENTS::END -->
      </div>
      </div> <!-- mainContent -->


    <!-- ##### Footer ##### -->
    <!-- $NetBSD: index.html,v 1.2237 2026/11/03 20:37:05 nia Exp $ -->
	<div id="footerLogo" style="vertical-align: middle; display: flex; align-items: baseline; justify-content: center;">
		<a href="//www.wwu.edu"><img src="images/westernlogo_sm.png" class="sponsor" alt="Western Washington University, sponsor"></a>
		<a href="//www.columbia.edu"><img src="images/columbia.jpg" class="sponsor" alt="Columbia University, sponsor"></a>
		<a href="//www.fastly.com"><img src="images/fastly.png" class="sponsor" alt="fastly, sponsor"></a>
		<a href="//www.twosigma.com"><img src="images/twosigma_logo.png" class="sponsor" alt="Two Sigma Investments, LLC, sponsor"></a>
		<a href="//futo.tech"><img src="images/FUTO_regular.png" class="sponsor" alt="FUTO, sponsor"></a>
	</div>
    </div>
    <div id="footer">
      <div class="rowOfBoxes">
	<div id="footerContent">
	  <span class="footfeed">
	    <a href="//www.NetBSD.org/cgi-bin/feedback.cgi">
	      Contact</a> |
	  </span>
	  <span class="footcopy"><a href="about/disclaimer.html">
	    Disclaimer</a> |
	    <span class="copyright">
	      Copyright &copy; 1994-2026 The NetBSD Foundation, Inc.
	    </span>
	    ALL RIGHTS RESERVED.<br>
	    NetBSD<sup>&reg;</sup> is a registered trademark of The NetBSD Foundation, Inc.
	  </span>
	</div>
      </div>
    </div>
  </div></body>
</html>
```

---

### Завдання A.4. Два запити в одному з’єднанні

Команда:

```powershell
$d = "netbsd.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 80)
$s = $c.GetStream()
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET /opism-pr02-12345 HTTP/1.1`r`nHost: $d`r`n`r`nGET / HTTP/1.1`r`nHost: $d`r`nConnection: close`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a4-pipeline.txt
$c.Close()
```

Вивід:

```text
HTTP/1.1 404 Not Found
Date: Tue, 24 Nov 2026 10:00:07 GMT
Server: Apache/2.4.62 (Unix)
Last-Modified: Tue, 03 Nov 2026 21:30:10 GMT
ETag: "19cd-65f65f791ac29;661025c2f109a
Accept-Ranges: bytes
Content-Length: 6605
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Content-Type: text/html

<html lang="en">
<head>
<meta charset="utf-8">
<meta name="generator" content="Website XSL Stylesheet V2.6.0">
<link rel="home" href="../." title="Welcome to The NetBSD Project: Of course it runs NetBSD.">
<link rel="up" href="../." title="Welcome to The NetBSD Project: Of course it runs NetBSD.">
<link rel="previous" href="../developers/." title="NetBSD Developer Documentation">
<link rel="next" href="../errors/forbidden.html" title="403 Forbidden">
<link rel="first" href="../about/." title="About NetBSD">
<link rel="last" href="../support/." title="NetBSD support">
<link rel="stylesheet" href="../global.css" type="text/css">
<link rel="stylesheet" href="../donations/thermo/fundraiser.css" type="text/css">
  <link rel="stylesheet" href="/global.css" type="text/css">
  <link rel="stylesheet" href="/donations/thermo/fundraiser.css" type="text/css">

  <title>404 Not Found</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
</head>
<body class="website"><div class="webpage" id="errors-index">
<div id="top"><a href="#mainContent" id="skiplink" tabindex="1">Skip to main content.</a></div>
<input id="hamburger" type="checkbox"><label class="menuicon" for="hamburger"><span></span><span></span><span></span></label><div id="navBar" role="navigation">
<div id="centralHeader"><div id="logo">
<a href="/"><img id="projectLogo" alt="" height="120" src="/images/NetBSD-smaller-tb.png"></a><a href="/"><div id="fundraiser">
<br><div id="fundraiser-amount"><div id="fundraiser-raised"></div></div>
</div></a>
</div></div>
<span class="doNotDisplay">
	  Navigation:
	</span><ul>
<li>
<a href="/">
	  Home</a><ul>
<li><a href="/changes/">
	    Recent changes</a></li>
<li><a href="//blog.NetBSD.org/">
	    NetBSD blog</a></li>
<li><a href="/gallery/presentations/">
	    Presentations</a></li>
</ul>
</li>
<li>
<a href="/about/">
	  About</a><ul>
<li><a href="/people/developers.html">
	    Developers</a></li>
<li><a href="/gallery/">
	    Gallery</a></li>
<li><a href="//wiki.NetBSD.org/ports/">
	    Ports</a></li>
<li><a href="//www.pkgsrc.org/">
	    Packages</a></li>
</ul>
</li>
<li>
<a href="/docs/">
	  Documentation</a><ul>
<li><a href="/docs/misc/index.html">
	    FAQ &amp; HOWTOs</a></li>
<li><a href="/docs/guide/en/">
	    The Guide</a></li>
<li><a href="//man.NetBSD.org/">
	    Manual pages</a></li>
<li><a href="//wiki.NetBSD.org/">
	    Wiki</a></li>
</ul>
</li>
<li>
<a href="/support/">
	  Support</a><ul>
<li><a href="/community/">
	    Community</a></li>
<li><a href="/mailinglists/">
	    Mailing lists</a></li>
<li><a href="/support/send-pr.html">
	    Bug reports</a></li>
<li><a href="/support/security/">
	    Security</a></li>
</ul>
</li>
<li>
<a href="/developers/">
	  Developers</a><ul>
<li><a href="//cvsweb.NetBSD.org/">
	    CVSWeb</a></li>
<li><a href="//nxr.NetBSD.org/">
	    Cross-reference</a></li>
<li><a href="//releng.NetBSD.org/">
	    Release engineering</a></li>
<li><a href="//wiki.NetBSD.org/projects/">
	    Projects list</a></li>
</ul>
</li>
</ul>
</div>
<div id="content"><div id="mainContent" class="fullWidth"><div class="rowOfBoxes">
<h1>404 Not Found</h1>
<div class="sect1">
<div class="titlepage"></div>

<div class="table">
<a name="table-404"></a><table id="table-404">
  <tr>
    <td width="140">
      <span class="inlinemediaobject"><img src="/images/NetBSD-flag.png" width="90" alt="NetBSD Logo"></span>
    </td>
    <td>
       <p>
	 There is no current document that matches your request. 
	 It is possible you typed the address incorrectly, or that 
	 the document has moved or been obsoleted.
       </p>

       <p>
	 Please use the search field in the upper right corner of this page
	 to search for content on www.NetBSD.org or use one of the links
	 below.
       </p>

       <p>
         If you feel you have received this page in error, please <a class="ulink" href="//www.NetBSD.org/cgi-bin/feedback.cgi" target="_top">let us know</a>.
       </p>
    </td>
  </tr>
</table>
</div>

</div>
<div class="sect1">
<div class="titlepage"><div><div><h2 class="title" style="clear: both">
<a name="info"></a>Useful Links:</h2></div></div></div>


<div class="table">
<a name="info-table"></a><table width="100%" id="info-table">
<tr>
<td width="50%">
<div class="itemizedlist"><ul class="itemizedlist" style="list-style-type: disc; ">
<li class="listitem">
      <a class="ulink" href="/" target="_top">NetBSD Home Page</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/releases/formal-11/" target="_top">Latest release - 11.1</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/donations/#how-to-donate/" target="_top">Donate! to NetBSD</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/support/security/" target="_top">Security and NetBSD</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/mirrors/" target="_top">Mirror sites</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/ports/" target="_top">Supported platforms</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/support/hardware/" target="_top">Supported hardware</a>
  </li>
</ul></div>
</td>
<td width="50%">
<div class="itemizedlist"><ul class="itemizedlist" style="list-style-type: disc; ">
<li class="listitem">
      <a class="ulink" href="/about/" target="_top">About NetBSD</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/changes/" target="_top">Latest news</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/docs/" target="_top">Documentation and FAQs</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/support/send-pr.html" target="_top">Bug reports</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/mailinglists/" target="_top">Mailing lists</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/contrib/" target="_top">Contributing to NetBSD</a>
  </li>
<li class="listitem">
      <a class="ulink" href="/docs/pkgsrc/" target="_top">The NetBSD
      Packages Collection</a>
  </li>
</ul></div>
</td>
</tr>
</table>
</div>

</div>
</div></div></div>
<div class="navfoot"></div>
<div id="footer"><div id="footerContent"><p style="text-align:center;"><span class="footfeed"><a href="//www.NetBSD.org/cgi-bin/feedback.cgi">
	  Contact</a> |
      </span><span class="footcopy"><a href="/about/disclaimer.html">
      Disclaimer</a> |

      <span class="copyright">Copyright © 1994-2026 The NetBSD Foundation, Inc. </span>ALL RIGHTS RESERVED.<br>NetBSD<sup>®</sup> is a registered trademark of The NetBSD
	Foundation, Inc.</span></p></div></div>
</div></body>
</html>
HTTP/1.1 200 OK
Date: Tue, 24 Nov 2026 10:00:07 GMT
Server: Apache/2.4.62 (Unix)
Last-Modified: Tue, 03 Nov 2026 21:30:03 GMT
ETag: "3194-65f65f72f7593"
Accept-Ranges: bytes
Content-Length: 12692
X-Frame-Options: SAMEORIGIN
X-Xss-Protection: 1; mode=block
Connection: close
Content-Type: text/html

<!DOCTYPE html>

<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <!-- Copyright (c) 1994-2026
	 The NetBSD Foundation, Inc.  ALL RIGHTS RESERVED. -->
    <link rel="author" href="mailto:www@NetBSD.org">
    <link rel="shortcut icon" href="./favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="global.css" type="text/css">
    <link rel="stylesheet" href="donations/thermo/fundraiser.css" type="text/css">
    <link rel="alternate" type="application/rss+xml" title="NetBSD news"
	  href="//www.NetBSD.org/changes/rss-netbsd.xml">
    <title>The NetBSD Project</title>
    <meta name="verify-v1" content="guJT5SZUh4XMF/emgSnXZPc6GkWkhP7PvMdYBc/auJI=">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0">
  </head>

  <body class="website"><div class="webpage">
    <!-- For non-visual user agents: -->
    <div id="top"><a href="#mainContent" id="skiplink" tabindex="1">Skip to main content.</a></div>

      <!-- mobile menu icon -->
      <input id="hamburger" type="checkbox">
      <label class="menuicon" for="hamburger"><span></span><span></span><span></span></label>

      <div id="navBar" role="navigation">
      <div id="centralHeader">
	<div id="logo">
		<a href="./"><img id="projectLogo" src="./images/NetBSD-smaller-tb.png" alt="" height="120"></a>
	</div>
	<a href="//www.NetBSD.org/donations/#how-to-donate">
		<div id="fundraiser">
			<br>
			<div id="fundraiser-amount">
				<div id="fundraiser-raised"></div>
			</div>
		</div>
  	</a>
        </div>
	<span class="doNotDisplay">
          Navigation:
        </span>
	<ul>
	<li><a href="./">
		  Home</a><ul>
	<li><a href="./changes/">
		    Recent changes</a></li>
	<li><a href="//blog.NetBSD.org/">
		    NetBSD blog</a></li>
	<li><a href="./gallery/presentations/">
		    Presentations</a></li>
	</ul>
	</li>
	<li>
	<a href="./about/">
		  About</a><ul>
	<li><a href="./people/developers.html">
		    Developers</a></li>
	<li><a href="./gallery/">
		    Gallery</a></li>
	<li><a href="//wiki.NetBSD.org/ports/">
		    Ports</a></li>
	<li><a href="//www.pkgsrc.org/">
		    Packages</a></li>
	</ul>
	</li>
	<li>
	<a href="./docs/">
		  Documentation</a><ul>
	<li><a href="./docs/misc/index.html">
		    FAQ &amp; HOWTOs</a></li>
	<li><a href="./docs/guide/en/">
		    The Guide</a></li>
	<li><a href="//man.NetBSD.org/">
		    Manual pages</a></li>
	<li><a href="//wiki.NetBSD.org/">
		    Wiki</a></li>
	</ul>
	</li>
	<li>
	<a href="./support/">
		  Support</a><ul>
	<li><a href="./community/">
		    Community</a></li>
	<li><a href="./mailinglists/">
		    Mailing lists</a></li>
	<li><a href="./support/send-pr.html">
		    Bug reports</a></li>
	<li><a href="./support/security/">
		    Security</a></li>
	</ul>
	</li>
	<li>
	<a href="./developers/">
		  Developers</a><ul>
	<li><a href="//cvsweb.NetBSD.org/">
		    CVSWeb</a></li>
	<li><a href="//nxr.NetBSD.org/">
		    Cross-reference</a></li>
	<li><a href="//releng.NetBSD.org/">
		    Release engineering</a></li>
	<li><a href="//wiki.NetBSD.org/projects/">
		    Projects list</a></li>
	</ul>
	</li>
	</ul>
      </div>

    <div id="content">
      <div id="mainContent">
          <h1>The NetBSD Project</h1>
	  <p class="twoThirds">
	    NetBSD is a free, fast, secure, and highly portable Unix-like
	    Open Source operating system. It is available for a wide
	    range of platforms, from large-scale servers and powerful
	    desktop systems to handheld and embedded devices.
	  </p>
	  <p>
	    <span class="more"><a href="./about/">&raquo;&nbsp;Learn more</a></span>
	  </p>
	  <h2>11.1 available!</h2>
	  <p>
	          The NetBSD project is pleased to announce
		  <span class="more">
  		  <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;NetBSD 11.1&nbsp;&laquo;</a></span>,
		  the first update to the nineteenth major release of NetBSD.
	  </p>
	  <h2><img src="images/download-icon-orange.png" alt="" class="icon">Get NetBSD</h2>
<div class="itemizedlist">
      <p>
	NetBSD 11.1, released on November 2, 2026.
        <span class="more">
          <a href="releases/formal-11/NetBSD-11.1.html">&raquo;&nbsp;Release Notes&nbsp;&laquo;</a></span>
    <div class="informaltable">

<table class="downloadtable">
  <thead><tr>
    <th style="text-align:left">CPU</th>
    <th style="text-align:left">Machines</th>
    <th style="text-align:left">Install media</th>
  </tr></thead>
  <tbody>
    <tr>
      <td><a class="ulink" href="//wiki.NetBSD.org/ports/amd64/" target="_top">amd64</a></td>
      <td>64-bit x86-family machines with AMD or Intel CPUs</td>
      <td>
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-install.img.gz" target="_top">USB image</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64-dvd.iso" target="_top">DVD</a>,
        <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-amd64.iso" target="_top">CD</a>
      </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">arm</a></td>
    <td>
      ARM systems like Raspberry Pi, PINE64, ODROID,
      "ServerReady" machines
      <a class="ulink" href="//wiki.NetBSD.org/ports/evbarm/" target="_top">more</a>
    </td>
    <td>
      <a class="ulink" href="https://armbsd.org" target="_top">Various boards</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbarm-earmv6hf/binary/gzimg/rpi.img.gz" target="_top">original RPi</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/i386/" target="_top">i386</a></td>
    <td>32-bit x86-family generic machines</td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-install.img.gz" target="_top">USB image</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386-dvd.iso" target="_top">DVD</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-i386.iso" target="_top">CD</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbmips/" target="_top">mips</a></td>
    <td>
      MIPS systems like EdgeRouter, Loongson, Malta
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64eb/binary/gzimg/octeon.img.gz" target="_top">octeon</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mips64el" target="_top">mips64el</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbmips-mipsel" target="_top">mipsel</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/evbppc/" target="_top">powerpc</a></td>
    <td>
      PowerPC systems like Nintendo Wii, DHT Walnut, RouterBOARD
    </td>
    <td>
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/binary/gzimg/wii.img.gz" target="_top">wii</a>,
      <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/evbppc/" target="_top">others</a>
    </td>
  </tr>
  <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/sparc64/" target="_top">sparc64</a></td>
    <td>Sun UltraSPARC</td>
    <td>
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64-dvd.iso" target="_top">DVD</a>,
       <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images/NetBSD-11.1-sparc64.iso" target="_top">CD</a>
    </td>
  </tr>
    <tr>
    <td><a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">others</a></td>
    <td>
      Amiga, Alpha, Apple PowerPC/68K, Dreamcast, SPARC32, VAX,
      <a class="ulink" href="//wiki.NetBSD.org/ports/" target="_top">more architectures</a>
    </td>
  <td><a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/NetBSD-11.1/images" target="_top">various</a></td>
  </tr>
  </tbody>
</table>
    </div>
<p><span class="more">
  <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/hashes/NetBSD-11.1_hashes.asc" target="_top">
    A signed list of hashes for the NetBSD 11.1 distribution.
  </a>
</span><br>
   The <a class="ulink" href="https://cdn.NetBSD.org/pub/NetBSD/security/PGP/security-officer@netbsd.org.asc">NetBSD Security Officer's
   PGP key</a> used to sign the list of hashes.</p>

	<h2><img src="images/donate-icon-orange.png" alt="" class="icon">Donate</h2>
		<p>
		Donations to The NetBSD Foundation allow the project to purchase
		build hardware and fund development.<br>
		Some recently funded projects are:
		</p>
		<ul>
			<li><a href="http://victory.NetBSD.org/pkgsrc/packages/reports/HEAD/evbarm64-9.0/">arm64 package build server</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/wifi_renewal_restarted">Wi-Fi renewal</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/lldb_now_works_on_i386">LLDB and upstream LLVM support</a></li>
			<li><a href="https://blog.NetBSD.org/tnf/entry/accomplishment_of_porting_ptrace_2">ptrace and GDB improvements</a></li>
		</ul>
		Please consider <a href="/donations/">donating</a> if you would like to see more of this work:
		<ul class="donationLinks">
			<li><a href="https://www.NetBSD.org/stripe.html">
			<img src="images/donate-icon-stripe.png" alt="" height="16">
			Donate using Stripe</a></li>
			<li><a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=paypal%40NetBSD.org&currency_code=USD&source=url">
			<img src="images/donate-icon-paypal.png" alt="" height="16">
			Donate or Subscribe with PayPal</a></li>
			<li><a href="https://github.com/sponsors/NetBSD">
			<img src="images/donate-icon-github.png" alt="" height="16">
			Sponsor NetBSD on GitHub</a></li>
		</ul>
	  </div>


      <div id="news">
	  <h2><img src="images/develop-icon-orange.png" alt="" class="icon">Latest News (<a href="//www.NetBSD.org/changes/rss-netbsd.xml">RSS</a>)</h2>
	  <ul>

	    <!-- this part automatically generated from changes/index.html through
		 Makefile-magic -->

	    <!-- NEWS::START -->
<li><a href="changes/#netbsd11.1">NetBSD 11.1 available</a><br/>2 November 2026</li>
<li><a href="changes/#netbsd10.2">NetBSD 10.2 available</a><br/>15 September 2026</li>
<li><a href="changes/#netbsd9.5">NetBSD 9.5 available and EOL for netbsd-9</a><br/>31 August 2026</li>
<li><a href="changes/#netbsd11.0">NetBSD 11.0 available</a><br/>30 July 2026</li>
	    <!-- NEWS::END -->
	  </ul>

	  <!-- this part automatically generated from gallery/events.html through
	       Makefile-magic -->

	    <!-- EVENTS::START -->
	<h3>Upcoming Events</h3>
	<ul>
<li><a href="gallery/events.html#fosdem2027">FOSDEM '27, Brussels, Belgium</a><br/>Jan 2027</li>
<li><a href="gallery/events.html#asiabsdcon2027">AsiaBSDCon 2027, Tokyo, Japan</a><br/>Mar 2027</li>
<li><a href="gallery/events.html#bsdcan2027">BSDCan 2027, Vancouver, Canada</a><br/>July 2027</li>
<li><a href="gallery/events.html#eurobsdcon2027">EuroBSDcon 2027, Bratislava, Slovakia</a><br/>Sep 2027</li>
	  <li>
	    <span class="more">
	      <a href="gallery/events.html">&raquo; Archive</a>
	    </span>
	  </li>
	</ul>
	    <!-- EVENTS::END -->
      </div>
      </div> <!-- mainContent -->


    <!-- ##### Footer ##### -->
    <!-- $NetBSD: index.html,v 1.2237 2026/11/03 20:37:05 nia Exp $ -->
	<div id="footerLogo" style="vertical-align: middle; display: flex; align-items: baseline; justify-content: center;">
		<a href="//www.wwu.edu"><img src="images/westernlogo_sm.png" class="sponsor" alt="Western Washington University, sponsor"></a>
		<a href="//www.columbia.edu"><img src="images/columbia.jpg" class="sponsor" alt="Columbia University, sponsor"></a>
		<a href="//www.fastly.com"><img src="images/fastly.png" class="sponsor" alt="fastly, sponsor"></a>
		<a href="//www.twosigma.com"><img src="images/twosigma_logo.png" class="sponsor" alt="Two Sigma Investments, LLC, sponsor"></a>
		<a href="//futo.tech"><img src="images/FUTO_regular.png" class="sponsor" alt="FUTO, sponsor"></a>
	</div>
    </div>
    <div id="footer">
      <div class="rowOfBoxes">
	<div id="footerContent">
	  <span class="footfeed">
	    <a href="//www.NetBSD.org/cgi-bin/feedback.cgi">
	      Contact</a> |
	  </span>
	  <span class="footcopy"><a href="about/disclaimer.html">
	    Disclaimer</a> |
	    <span class="copyright">
	      Copyright &copy; 1994-2026 The NetBSD Foundation, Inc.
	    </span>
	    ALL RIGHTS RESERVED.<br>
	    NetBSD<sup>&reg;</sup> is a registered trademark of The NetBSD Foundation, Inc.
	  </span>
	</div>
      </div>
    </div>
  </div></body>
</html>
```

**Кількість відповідей:** 2.

**Коди стану:** 404 Not Found та 200 OK відповідно.

---

### Завдання A.5. Запит за допомогою клієнтської програми

Команда:

```powershell
curl.exe -v --http1.1 http://netbsd.org/ -o NUL 2>&1 | Tee-Object -FilePath raw/a5-curl.txt
```

Вивід:

```text
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 199.233.217.205...
* TCP_NODELAY set
* Connected to netbsd.org (199.233.217.205) port 80 (#0)

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0> GET / HTTP/1.1

> Host: netbsd.org

> User-Agent: curl/7.55.1

> Accept: */*

> 

< HTTP/1.1 200 OK

< Date: Tue, 24 Nov 2026 10:01:05 GMT

< Server: Apache/2.4.62 (Unix)

< Last-Modified: Tue, 03 Nov 2026 21:30:03 GMT

< ETag: "3194-65f65f72f7593"

< Accept-Ranges: bytes

< Content-Length: 12692

< X-Frame-Options: SAMEORIGIN

< X-Xss-Protection: 1; mode=block

< Content-Type: text/html

< 

{ [4088 bytes data]

100 12692  100 12692    0     0  12692      0  0:00:01 --:--:--  0:00:01 16250
* Connection #0 to host netbsd.org left intact
```

---

### Завдання A.6. Запит через захищене з’єднання

**Ресурс:** `iana.org`

**Підстава:** у A.1 отримано 200 OK, а не код класу 3xx. OpenSSL не знайдено, тому застосовано SslStream; заміна потребує погодження, якщо викладач вимагає OpenSSL.

Команда:

```powershell
$d = "iana.org"
$c = New-Object System.Net.Sockets.TcpClient($d, 443)
$s = New-Object System.Net.Security.SslStream($c.GetStream(), $false)
$s.AuthenticateAsClient($d)
$w = New-Object System.IO.StreamWriter($s)
$w.Write("GET / HTTP/1.1`r`nHost: $d`r`nConnection: close`r`n`r`n")
$w.Flush()
(New-Object System.IO.StreamReader($s)).ReadToEnd() | Tee-Object -FilePath raw/a6-tls.txt
$s.Close()
$c.Close()
```

**Текст запиту (передано через `$w.Write()`):**

```http
GET / HTTP/1.1
Host: iana.org
Connection: close

```

Вивід:

```text
HTTP/1.1 301 Moved Permanently
Date: Tue, 24 Nov 2026 10:03:31 GMT
Server: Apache
Location: https://www.iana.org/
Cache-Control: max-age=345600
Expires: Sat, 28 Nov 2026 10:03:31 GMT
Content-Length: 229
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://www.iana.org/">here</a>.</p>
</body></html>
```

---

## Частина B. Розбір полів заголовка
Кількість полів: 10. Походження є оцінкою, а не підтвердженою конфігурацією сервера.

| № | Поле | Значення | Призначення | Походження | Обґрунтування |
|---|---|---|---|---|---|
| 1 | Date | Tue, 24 Nov 2026 09:54:20 GMT | Час формування повідомлення | сервер (імовірно) | Типове поле відповіді сервера |
| 2 | Server | Apache/2.4.62 (Unix) | Ідентифікація серверного ПЗ | не визначено | Поле може належати і проксі, що використовує Apache |
| 3 | Last-Modified | Tue, 03 Nov 2026 21:30:03 GMT | Час останньої зміни ресурсу | сервер (імовірно) | Пов'язано з метаданими ресурсу |
| 4 | ETag | `"3194-65f65f72f7593"` | Ідентифікатор версії представлення | сервер (імовірно) | Типовий валідатор кешу ресурсу |
| 5 | Accept-Ranges | bytes | Підтримка запитів діапазонів байтів | сервер (імовірно) | Характеристика доступу до ресурсу |
| 6 | Content-Length | 12692 | Розмір тіла у байтах | не визначено | Може встановлюватися або перераховуватися посередником |
| 7 | X-Frame-Options | SAMEORIGIN | Обмежує вбудовування сторінки у фрейми | не визначено | Політику може задавати сервер або проксі |
| 8 | X-Xss-Protection | 1; mode=block | Застарілий механізм браузерного XSS-фільтра | не визначено | Може додаватися на різних рівнях |
| 9 | Connection | close | Закриття поточного з’єднання після відповіді | не визначено | Поле стосується поточного транспортного сегмента |
| 10 | Content-Type | text/html | Тип представлення тіла | сервер (імовірно) | Відповідає отриманому HTML |

## Частина C. Обговорення
Для аудиторного обговорення підготовлено таблицю проб і перелік заголовків вище. Результати інших студентів не надано.

---

## Частина D. Висновки
**D.1. Неочевидні результати.**

Найбільш несподіваним результатом стала реакція сервера netbsd.org на зміну значення поля Host. У пробах A.3.1 та A.3.2 отримано рядок `HTTP/1.1 200 OK`, хоча передано чуже та неіснуюче доменні імена. Значення Content-Length дорівнювало 12692, а ETag залишився таким самим, як у A.1. Це дозволяє припустити, що сервер використовує віртуальний хост за замовчуванням. Водночас повна відсутність Host у HTTP/1.1 призвела до коду 400, а в HTTP/1.0 — до коду 200. Отже, наявність поля та відповідність його значення конкретному домену виявилися різними умовами обробки запиту.

У завданні A.4 перший запит завершився кодом 404, але другий отримав код 200 через те саме TCP-з’єднання. Це демонструє, що помилка пошуку ресурсу не обов’язково перериває обмін повідомленнями. У A.6 захищене з’єднання з резервним вузлом iana.org повернуло код 301, тому використання TLS саме по собі не означає отримання кінцевої сторінки без перенаправлення.

**D.2. Походження заголовків.**

Найскладніше було встановити походження поля Server: воно повідомляє назву програмного забезпечення, але не дає достатньо інформації для розмежування кінцевого сервера та можливого проксі. 

**D.3. Відкрите питання.**

Без відповіді залишилося питання, чи справді однакові відповіді на різні значення Host пояснюються конфігурацією віртуального хоста за замовчуванням, чи іншим механізмом маршрутизації. Для остаточного підтвердження потрібні додаткові відомості про конфігурацію вузла.

---

## Контрольні питання

1. Порожній рядок (CRLF CRLF після останнього поля) завершує секцію заголовків. Без нього сервер не знає, чи завершено її передачу. У PowerShell запит передавався одним блоком, тому окремо очікування до порожнього рядка не спостерігалося.
2. A.1, A.3.1, A.3.2 та A.3.3 містять рядок `HTTP/1.1 200 OK`, а A.2 — `HTTP/1.1 400 Bad Request`. У HTTP/1.1 Host обов’язковий і дозволяє серверу вибрати потрібний віртуальний хост. Результат із невідомими іменами узгоджується з використанням хоста за замовчуванням. У HTTP/1.0 Host не обов’язковий. Версія в рядку відповіді A.3.3 при цьому 1.1.
3. A.4 містить дві відповіді: `HTTP/1.1 404 Not Found` і `HTTP/1.1 200 OK`. Відповідь залежить від шляху, тобто вузол обслуговує ресурси, а не лише перенаправляє весь трафік. Два запити оброблено в одному з’єднанні, що дає змогу зменшити витрати на встановлення окремих TCP-з’єднань. Друга відповідь містить `Connection: close`.
4. Curl додав `User-Agent: curl/7.55.1` для ідентифікації клієнта та `Accept: */*` для позначення готовності прийняти будь-який медіатип. На відміну від A.1, він не надсилав Connection: close.
5. У A.1 немає явних ознак посередника, наприклад Via або X-Cache. Це не доводить відсутності проміжних вузлів: вони можуть не розкривати свою присутність у доступних заголовках.
6. Три рядки з власного виводу наведено в Додатку В. Необхідно звірити їх із матеріалом лекції 2.

---

## Додаток В. Відповіді на питання 6

| № | Рядок | Джерело |
|---|---|---|
| 1 | `ETag: "3194-65f65f72f7593"` | A.1 |
| 2 | `X-Xss-Protection: 1; mode=block` | A.1 |
| 3 | `* TCP_NODELAY set` | A.5 |

---

## Додаток Д. Зведення результатів завдання A.3
Вузол: netbsd.org:80. Збіг визначено за кодом і тілом відповіді, без урахування часу Date.

| Проба | Host | Версія запиту | Код | Тіло, байт (Content-Length) | Збіг з A.1 |
|---|---|---|---|---:|---|
| A.1 | netbsd.org | 1.1 | 200 | 12692 | — |
| A.2 | відсутнє | 1.1 | 400 | 226 | ні |
| A.3.1 | nau.edu.ua | 1.1 | 200 | 12692 | так |
| A.3.2 | opism-pr02.invalid | 1.1 | 200 | 12692 | так |
| A.3.3 | відсутнє | 1.0 | 200 | 12692 | так |

Відсутність Host у HTTP/1.1 спричинила відмову. Заміна значення Host на інше або неіснуюче ім’я не змінила отриманої сторінки. У HTTP/1.0 запит без Host також успішний.

---

## Декларування використання технологій штучного інтелекту

Рівень Р3 — ШІ як співвиконавець. Використання ШІ: так.

| № | Інструмент | Етап | Дослівний текст запиту | Використання результату |
|---|---|---|---|---|
| 1 | ChatGPT | Виконання практичної | Допоможи зробити практичну | Підготовка команд PowerShell та аналіз наданих виводів |
| 2 | ChatGPT | Уточнення варіанта | 8 | Підстановка індивідуальних доменів |
| 3 | ChatGPT | Заповнення звіту | як перше зробити | Вставлення фактичних виводів у звіт |
| 4 | ChatGPT | Оформлення | https://github.com/Nekretos/Practical-2  можешь оформить похоже | Адаптація структури звіту за прикладом без запозичення чужих результатів |

Виводи частини A отримано студентом під час виконання команд і надано у восьми файлах. ШІ використано для їх аналізу та оформлення. Заміна OpenSSL на SslStream потребує погодження з викладачем; рядки Додатка В потрібно звірити з лекцією 2.

---

ОПІСМ (ОК-13) · Практична робота № 2
