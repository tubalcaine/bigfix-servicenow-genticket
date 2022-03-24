# bigfix-servicenow-genticket
## A proof-of-concept integration between BigFix and ServiceNow

This sample Python script will query for BigFix actions back a
number of days and will generate a ticket in ServiceNow for any 
new action failure. Failure is defined by the states listed in the
session relevance query near the start of the script.

A record of the action/endpoints for which a ticket has been generated
is stored in a JSON file, and this serves as the "database" between runs.
This actually scales remarkably well, but I consider the whole script
to be only a "proof of concept."

First of all, there is a comprehensive BigFix REST API Python module
named "besapi" that you should use for anything with a production
intent, because that is actively maintained, is installable with "pip",
and will almost certainly stay up-to-date with REST API changes.

This is coded to directly use ServiceNow table APIs, which works
where permitted, and does not require any customization. I am not
at all a ServiceNow expert, but it is my impression that doing this
bypasses edits, validations, and other controls that most enterprises
put on input fields. More than likely, your ServiceNow team will
have a "higher level" call for submitting tickets/events that would
prefer you use. You should be able to modify this code to be compliant.

Finally, this code has the "classic" API automation problem:
How do you give API Service Account passwords securely? The answer
is this code does not. Local password policies make a single solution
to this problematic. This is meant to get you started, not be
a production-ready tool.

I welcome you to branch, and if you find a solution to the password
problem, or if you rewrite this to use _besapi_, then by all means 
send me a pull request and I would be glad to merge your contribution

This also needs unit tests.
