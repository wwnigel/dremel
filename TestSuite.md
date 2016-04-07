#Test suite for the OpenDremel project

# Purpose of the test suite #
As any other test suite should give us guarantee that product is fine.
it shold test all capabilities.
Other DB products have perfect test suites (SQLLite for example). We suggest to
extend this page with the design ideas from the other DBMS  engines test suites and how
to adapte them to the OpenDremel

# Data formats #

OpenDremel will take input and outpput data in form of http://code.google.com/p/protobuf/
It mean that potions of data will be in protobuf format, and query output will be in it also.