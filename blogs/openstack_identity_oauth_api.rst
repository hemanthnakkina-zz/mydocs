==========================================
How to use OpenStack Identity OAUTH API
==========================================


This document is to provide use cases for OpenStack Identity OAUTH API.
Idea is to provide the sequence of cli and rest api commands.


Commands using OpenStack CLI
=============================

1. Create a Consumer::

    ocata@ocata-VirtualBox:~/devstack$ openstack consumer create --description "consumer_1"
    +-------------+----------------------------------+
    | Field       | Value                            |
    +-------------+----------------------------------+
    | description | consumer_1                       |
    | id          | fa83205900e04c2abffd108574918b76 |
    | secret      | 4b890f5be14e48f6b683a58bf0d132c7 |
    +-------------+----------------------------------+

2. Create Request Token::

    ocata@ocata-VirtualBox:~/devstack$ openstack request token create --consumer-key fa83205900e04c2abffd108574918b76 --consumer-secret 4b890f5be14e48f6b683a58bf0d132c7 --project demo
    +---------+----------------------------------+
    | Field   | Value                            |
    +---------+----------------------------------+
    | expires | 2017-05-17T14:32:00.000000Z      |
    | id      | 62f19d89e21649ffa0ad92edace14f56 |
    | key     | 62f19d89e21649ffa0ad92edace14f56 |
    | secret  | 999f74dfee284a0db8b4e1cbed560c7b |
    +---------+----------------------------------+

3. Authorize the request token::

    ocata@ocata-VirtualBox:~/devstack$ openstack request token authorize --request-key  62f19d89e21649ffa0ad92edace14f56 --role admin
    +----------------+----------+
    | Field          | Value    |
    +----------------+----------+
    | oauth_verifier | xUnJdXMN |
    +----------------+----------+

4. Create access token::

    ocata@ocata-VirtualBox:~/devstack$ openstack access token create --consumer-key fa83205900e04c2abffd108574918b76 --consumer-secret 4b890f5be14e48f6b683a58bf0d132c7 --request-key 62f19d89e21649ffa0ad92edace14f56 --request-secret 999f74dfee284a0db8b4e1cbed560c7b --verifier xUnJdXMN
    +---------+----------------------------------+
    | Field   | Value                            |
    +---------+----------------------------------+
    | expires | 2017-05-18T06:38:30.000000Z      |
    | id      | 6b606ee9d0dd4104ac2fd060c522fb11 |
    | key     | 6b606ee9d0dd4104ac2fd060c522fb11 |
    | secret  | 78540fc7cec44847b8e391ccd2edc0ee |
    +---------+----------------------------------+

5. Create a token using access token::

   TODO


Commands using REST API
========================

TODO
