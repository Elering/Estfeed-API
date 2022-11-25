# ESTFEED

---

## OpenAPI
/openapi - API descritpion for market participants

## Update: November 2022
Each API includes marketParticipantContext with the following elements:
* marketParticipantIdentification - EIC X-code of the market participant sending the API query
* marketParticipantRole - defines the role in which the specific query is sent; for example a market participant who is an open supplier can query information as an open supplier, as a BRP, and as a named supplier
* purpose - defines the purpose of the query, e.g. when querying customer's metering points the purpose should be to determine whether the customer has the right to change supplier (check that is mandatory according to the Network Code on the Operation of the Electricity Market)
* commodityType - defines whether the query is an action for electricity or natural gas market, relevant as there are market participants that act in both electricity and gas market

Reasons for including this information with each API:
* to provide a clear understanding of who and why makes queries to the Datahub and how the queried data is intended to be used 
* to be technically able to separate specific actions by the market participants
