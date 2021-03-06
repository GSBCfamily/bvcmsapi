OData API
=========

* The APIs are all readonly and follow the `OData standard <http://www.odata.org/>`_. See that link for more details.
* All OData calls also include links to return metadata about the return if that is needed. An example can be found by issuing an authenticated ``GET`` to ``https://trialdb.tpsdb.com/api/$metadata#People``.
* We return a max of 1000 records per request. If more than that match, then the result will include the link to the next page (via the ``$skip`` parameter).
* Authentication to the OData API requires a user with both the ``Developer`` and ``APIOnly`` roles (``APIOnly`` might not exist and will need to be created).

**NOTE:** The examples below explicitly set the authorization header, but you can also set it like so::

    curl --user "apionly:MyApiPasswordToRuleThemAll" "https://trialdb.tpsdb.com/api/People?$top=5"

People ("Donors")
-----------------

Get the top 5 people records. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/People?$top=5"

Contributions ("Donor Info")
----------------------------

Get the top 5 contribution records. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/Contributions?$top=5"

Get all contributions since ``2014-12-30``. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/Contributions?$filter=ContributionDate+ge+2014-12-30"

Same as above, but with greater time granularity. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/Contributions?$filter=ContributionDate+ge+2014-12-30T23:59:59.99Z"

Funds
-----

Get contribution fund details. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/Funds"

Lookups
-------

Lookups are good to find more details about records (i.e. such as campuses and/or family positions). They have defaults in our system, but allow for additional configurable lookups customized by the church.

Get all marital status lookups. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/lookup/MaritalStatuses"

Get all campus lookups. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/lookup/Campuses"

Get all family position lookups. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/lookup/FamilyPositions"

Get all contribution type lookups. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/lookup/ContributionTypes"

Get all gender lookups. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/lookup/Genders"

Organizations
-------------

Get the organization member under org "2181006" with a people ID of "1". ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/OrganizationMembers?$filter=OrganizationId+eq+2181006+and+PeopleId+eq+1"

Get all organizations. ::

    curl -H "Authorization: Basic YXBpb25seTpNeUFwaVBhc3N3b3JkVG9SdWxlVGhlbUFsbA==" "https://trialdb.tpsdb.com/api/Organizations

