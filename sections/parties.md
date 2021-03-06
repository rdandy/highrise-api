Parties
=======

For the full XML representation of parties, [check out the data reference](https://github.com/basecamp/highrise-api/blob/master/sections/data_reference.md#party).


Search parties
--------------

* `GET /parties/search.xml?state=CA&zip=90210&custom_field=foobar&etc=...` returns people and companies that match your search criteria. Search by any criteria you can on the Contacts tab, including custom fields. Combine criteria to narrow results.

Results are paged in groups of 25. Use `?n=25` to check for the next 25 results and so on.

**Response:**

``` xml
<parties type="array">
  <party type="Person">
    ...
  </party>
  <party type="Company">
    ...
  </party>
</parties>
```

Strict party search
-------------------

Add `&strict=1` after the query parameters to return strict name results. 

For example: `/parties/search.xml?name=jon&strict=1` returns any contacts with the name `Jon`. 

And `/parties/search.xml?name=jo&strict=1` does **not** return any contacts with `Jo` in their name. 


Get recently viewed parties
---------------------------

* `GET /parties/parties.xml?scope=recently_viewed` returns the last 50 people and companies viewed.

**Response:**

``` xml
<parties type="array">
  <party type="Person">
    ...
  </party>
  <party type="Company">
    ...
  </party>
</parties>
```


Get deleted parties
-------------------

* `GET /parties/deletions.xml?since=20070425154546` returns deleted parties in order of deletion time, older to newer.

Includes party type, id, and deletion time. Pass the optional `since` query parameter to only return deletions since that time.

**Response:**

``` xml
<deletions type="array">
  <deletion type="Person">
    <id type="integer">1</id>
    <deleted-at type="datetime">2007-08-27T03:11:52Z</deleted-at>
  </deletion>
  <deletion type="Company">
    <id type="integer">2</id>
    <deleted-at type="datetime">2008-03-12T14:37:13Z</deleted-at>
  </deletion>
  ...
</deletions>
```
