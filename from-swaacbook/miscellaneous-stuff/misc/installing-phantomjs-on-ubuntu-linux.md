
# Table of Contents

1.  [Installing PhantomJS on Ubuntu Linux](#installing-phantomjs-on-ubuntu-linux)


<a id="installing-phantomjs-on-ubuntu-linux"></a>

# Installing PhantomJS on Ubuntu Linux

-   published date: 2015-04-09 06:13
-   keywords: ["devops", "karma", "phantomjs", "testing", "vagrant", "virtual-machines"]
-   source: <https://gist.github.com/julionc/7476620>

I found this while testing an AngularJS client on travis-ci.

Install these to get PhantomJS to work on Ubuntu 14.04:

    sudo apt-get update
    sudo apt-get install build-essential chrpath libssl-dev libxft-dev
    sudo apt-get install libfreetype6 libfreetype6-dev
    sudo apt-get install libfontconfig1 libfontconfig1-dev

