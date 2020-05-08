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
 
find . -type f -print0 | xargs -0 sed -i 's/litecoin/testcoin/g'
find . -type f -print0 | xargs -0 sed -i 's/Litecoin/Testcoin/g'
find . -type f -print0 | xargs -0 sed -i 's/LiteCoin/Testcoin/g'
find . -type f -print0 | xargs -0 sed -i 's/LITECOIN/TESTCOIN/g'
find . -type f -print0 | xargs -0 sed -i 's/LTC/TST/g'
