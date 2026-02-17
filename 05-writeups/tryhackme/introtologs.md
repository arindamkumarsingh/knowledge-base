# Intro

Logs serve as a record for the past events happened in your computer. Logs pattern can help us identify any potential threats. But since system produces vast amt of logs and files, the log analysis becomes an important skill to learn. So there exists some tools which helps in this analysis.

In digital world, even an attempt of logging in to granting access to the user, has its own digital footprint.

A log file generally contains:

* A timestamp of the event
* name of the application which generated the query
* Type of entry and other details.

Log files size can increase exponentially depending on the number of interactions in the system.

Some W's :-

* **What** happened?
* **When** did it happen?
* **Where** did it happpen?
* **Who** is responsibele? 
* **Were** they successful?
* **What** is the result of their actions?

# Some common log filestype



*    Application Logs: Messages about specific applications, including status, errors, warnings, etc.
*    Audit Logs: Activities related to operational procedures crucial for regulatory compliance.
*    Security Logs: Security events such as logins, permissions changes, firewall activity, etc.
*    Server Logs: Various logs a server generates, including system, event, error, and access logs.
*    System Logs: Kernel activities, system errors, boot sequences, and hardware status.
*    Network Logs: Network traffic, connections, and other network-related events.
* Database Logs: Activities within a database system, such as queries and updates.
*    Web Server Logs: Requests processed by a web server, including URLs, response codes, etc.

## Structure

* SEMI STRUCTURED

    * Syslog - syslog.txt file, do `cat`.
    * Windows event log(EVTX)

* Structured

    * CSV ( Comma seperated Values) and TSV( Tab seperated values) - This is used mainly due to their tabular structure.
    * JSON , used for  their compatability with modern programming language.
    * W3C (elf) - customizable for web server
    * eXtensible markup language(XML)\
    
* Unstructured

    * clf.log - Used specifically for Apache server.
    * combined.log - Used specifically for Nginx server.

#  Formats

Specific guidelines how logs to be written, what to be logged etc.

<img src="/home/arindam-kumar-singh/Pictures/Screenshots/Screenshot from 2026-02-17 18-43-34.png" alt="Description" width="300" height="200">
