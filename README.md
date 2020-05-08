# litecoin-fork-guide
Dependencies:
 
sudo apt-get install git
 
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils
 
sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev
 
sudo apt-get install libboost-all-dev
 
sudo apt-get install software-properties-common
 
sudo add-apt-repository ppa:bitcoin/bitcoin
 
sudo apt-get update
 
sudo apt-get install libdb4.8-dev libdb4.8++-dev
 
sudo apt-get install libminiupnpc-dev
 
sudo apt-get install libzmq3-dev
 
sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler
 
sudo apt-get install libqt4-dev libprotobuf-dev protobuf-compiler
 
git clone -b 0.8 https://github.com/litecoin-project/litecoin.git
 ```
find . -type f -print0 | xargs -0 sed -i 's/litecoin/testcoin/g'
find . -type f -print0 | xargs -0 sed -i 's/Litecoin/Testcoin/g'
find . -type f -print0 | xargs -0 sed -i 's/LiteCoin/Testcoin/g'
find . -type f -print0 | xargs -0 sed -i 's/LITECOIN/TESTCOIN/g'
find . -type f -print0 | xargs -0 sed -i 's/LTC/TST/g'
```
```
find . -type f -print0 | xargs -0 sed -i 's/9333/2333/g'
find . -type f -print0 | xargs -0 sed -i 's/9332/2332/g'
 ```
 ```
openssl ecparam -genkey -name secp256k1 -out alertkey.pem
openssl ec -in alertkey.pem -text > alertkey.hex
openssl ecparam -genkey -name secp256k1 -out testnetalert.pem
openssl ec -in testnetalert.pem -text > testnetalert.hex
openssl ecparam -genkey -name secp256k1 -out genesiscoinbase.pem
openssl ec -in testnetalert.pem -text > genesiscoinbase.hex
```
date +%s
 
 #paste the code to generate genesis hash
 ```
if (false && block.GetHash() != hashGenesisBlock)
        {
            printf("Searching for genesis block...\n");
            // This will figure out a valid hash and Nonce if you're
            // creating a different genesis block:
            uint256 hashTarget = CBigNum().SetCompact(block.nBits).getuint256();
            uint256 thash;
            char scratchpad[SCRYPT_SCRATCHPAD_SIZE];
 
            loop
            {
#if defined(USE_SSE2)
                // Detection would work, but in cases where we KNOW it always has SSE2,
                // it is faster to use directly than to use a function pointer or conditional.
#if defined(_M_X64) || defined(__x86_64__) || defined(_M_AMD64) || (defined(MAC_OSX) && defined(__i386__))
                // Always SSE2: x86_64 or Intel MacOS X
                scrypt_1024_1_1_256_sp_sse2(BEGIN(block.nVersion), BEGIN(thash), scratchpad);
#else
                // Detect SSE2: 32bit x86 Linux or Windows
                scrypt_1024_1_1_256_sp(BEGIN(block.nVersion), BEGIN(thash), scratchpad);
#endif
#else
                // Generic scrypt
                scrypt_1024_1_1_256_sp_generic(BEGIN(block.nVersion), BEGIN(thash), scratchpad);
#endif
                if (thash <= hashTarget)
                    break;
                if ((block.nNonce & 0xFFF) == 0)
                {
                    printf("nonce %08X: hash = %s (target = %s)\n", block.nNonce, thash.ToString().c_str(), hashTarget.ToString().c_str());
                }
                ++block.nNonce;
                if (block.nNonce == 0)
                {
                    printf("NONCE WRAPPED, incrementing time\n");
                    ++block.nTime;
                }
            }
            printf("block.nTime = %u \n", block.nTime);
            printf("block.nNonce = %u \n", block.nNonce);
            printf("block.GetHash = %s\n", block.GetHash().ToString().c_str());
        }
```
#end
```
in src/qt/aboutdialog.cpp
 
Fix line 22: ui->copyrightLabel->setText(tr("Copyright") + QString(" &copy; 2009-%1 ").arg(COPYRIGHT_YEAR) + tr("The Bitcoin developers") + QString("<br>") + tr("Copyright") + QString(" &copy; ") + tr("2011-%1 The Litecoin developers").arg(ABOUTDIALOG_COPYRIGHT_YEAR)+ QString("<br>") + tr("Copyright") +QString(" &copy; ") + tr("%1 Funcoin Developer").arg(2017));
 
in src/qt/splashscreen.cpp
 
line 22, add int line4 = 39;
Fix line 30 and add 31: QString copyrightText3   = QChar(0xA9)+QString(" %1 ").arg(2017) + QString(tr("Funcoin Developer"));
Change line 48: pixPaint.drawText(paddingLeftCol2,paddingTopCol2+line4,versionText);
Add line 54: pixPaint.drawText(paddingLeftCol2,paddingTopCol2+line3,copyrightText3);
 
in src/qt/res/bitcoin-qt.rc:
 
Fix line 11: #define COPYRIGHT_STR          "2009-" STRINGIZE(COPYRIGHT_YEAR) " The Bitcoin developers 2011-" STRINGIZE(COPYRIGHT_YEAR) " The Litecoin developers 2017 Funcoin Developer"
 
in src/qt/aboutdialog.ui:
 
Below line 94, paste:
Copyright &amp;copy; 2011-YYYY The Litecoin developers
Copyright &amp;copy; 2017 Testcoin Developer</string>
 
1228, net.cpp
 
perl script:
 
#!/usr/bin/perl
 
# Twobits twobit integer dotted quad to reverse hex convertor
#  designed for q&d use to put seeds into pnSeeds in *coins
 
my $ip;
 
if (@ARGV) {
    $ip = shift @ARGV;
} else {
    print "Enter an (dotted quad) ip address: ";
    chomp( $ip = <STDIN> );
}
 
printf "0x%08x\n",  unpack 'N', pack 'C4', reverse split '\.', $ip;
```
