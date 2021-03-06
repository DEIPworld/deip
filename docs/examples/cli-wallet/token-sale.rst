*****************
How to token sale
*****************

Start research token sale
=========================

1. :doc:`Start wallet <../../blockchain interaction/cli-wallet/wallet>`
2. :doc:`Create a research <./create-a-research>`
3. To propose to start token sale run ``propose_start_token_sale`` command, which takes following parameters:

* creator name
* research group id
* id of research
* research start time (Unix timestamp (UTC time))
* research end time (Unix timestamp (UTC time))
* amount for sale (up to 10000, which is 100% of all research tokens)
* softcap (i.e. "1.000 TESTS")
* hardcap (i.e. "10.000 TESTS")
* broadcast: boolean showing whether or not you want to broadcast this transaction::

    propose_start_token_sale "yourAccountName" 53 2 1539710709 1539750700 1000 "1.000 TESTS" "10.000 TESTS" true

After transaction was included in block, proposal to start a research token sale will be created.

4. To list proposals in research group use following method and provide desired research group id::

    list_research_group_proposals id_of_research_group

As result you should see a list of all proposals in research group. 

5. To vote for specific proposal use ``vote_proposal`` method::

    vote_proposal "yourAccountName" id_of_proposal id_of_research_group true

When enough accounts vote for proposal and quorum percent is achieved - proposal will be accepted and research token sale is created. Keep in mind that token sale will not start until specified 'start time'. 

6. To list all token sales use ``list_research_token_sales`` command with following parameters:

* lower bound id to start listing from (suggested to set to 0 unless you want to list starting from some specific id)
* limit of entries to list (default: 100, maximum: 1000)::

    list_research_token_sales 0 100

Token sale statuses
-------------------
| 1 - Active (token sale is **ongoing**) 
| 2 - Finished (token sale is **completed**) 
| 3 - Expired (token sale is **expired**) 
| 4 - Inactive (token sale is **not started yet**)

Contribute to token sale
========================

To contribute to token sale you can use ``contribute_to_token_sale`` command with following parameters:

* contributor (account name of contributor)
* research token sale id
* amount (amount in DEIP Tokens to contribute with, i.e. "1.000 TESTS")
* broadcast::

    contribute_to_token_sale bob 1 "10.000 TESTS" true

If softcap and endtime is reached - all contributors will get their tokens. If hardcap is reached after someone's contribution - token sale finishes immediately.

To list account's research tokens use ``list_account_research_tokens account_name`` command.