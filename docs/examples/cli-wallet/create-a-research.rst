*****************
Create research
*****************

1. :doc:`Start wallet <../../blockchain interaction/cli-wallet/wallet>`
2. :doc:`Create a research group <./create-a-research-group>`
3. To propose creation of research run ``propose_create_research`` command, which takes following parameters:

* creator name
* research title
* research abstract
* research permlink
* id of research group
* percent of reward to share with reviewers (0 to 5000)
* percent of research tokens to leave to dropped author (0 to 5000)
* list of disciplines ids (i.e. [8, 152] (see below how to get a list of all disciplines))
* broadcast: boolean showing whether or not you want to broadcast this transaction
* propose_create_research "yourAccountName" "research title" "research abstract" "research-permlink" 0 0 1000 [0, 100] true

After transaction was included in block, proposal to start a research will be created.

To list proposals in research group use following method and provide desired research group id::

    list_research_group_proposals id_of_research_group

As result you should see a list of all proposals in research group. 

4. To vote for specific proposal use ``vote_proposal`` method::

    vote_proposal "yourAccountName" id_of_proposal id_of_research_group true

When enough accounts vote for proposal and quorum percent is achieved - proposal will be accepted and research is created. 

5. To list all researches of research group use ``get_researches_by_research_group`` command.

Get list of all disciplines
---------------------------

``list_all_disciplines``