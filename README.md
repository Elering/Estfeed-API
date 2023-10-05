# ESTFEED

---

## OpenAPI

/openapi - API description for market participants

## Update: November 2022

Each API includes marketParticipantContext with the following elements:
* marketParticipantIdentification - EIC X-code of the market participant sending the API query
* marketParticipantRole - defines the role in which the specific query is sent; for example a market participant who is an open supplier can query information as an open supplier, as a BRP, and as a named supplier
* purpose - defines the purpose of the query, e.g. when querying customer's metering points the purpose should be to determine whether the customer has the right to change supplier (check that is mandatory according to the Network Code on the Operation of the Electricity Market)
* commodityType - defines whether the query is an action for electricity or natural gas market, relevant as there are market participants that act in both electricity and gas market

Reasons for including this information with each API:
* to provide a clear understanding of who and why makes queries to the Datahub and how the queried data is intended to be used 
* to be technically able to separate specific actions by the market participants

## Update: April 2023

We have added for comments new interface descritpions:
- agreementCoordination-v2
- balanceState
- connectionState-v2 
- directMessage
- forwardInvoice
- networkBill

## Update: July 2023

Added latest openapi descriptions.

> NB! Includes now not yet developed API endpoints also!

## Update: October 2023
Updated status and timeline of interfaces.

meteringData has significant changes:
- we changed timeslot description. 
- Previously timeslot was defined by position but now it is defined by absolute time.
        
        "meterEic": "69YH5LHV6NFM84YP",
        "periods": [
        {
          "r": "PT15M",
          "aI": [
            {
              "pS": "2023-10-05T09:00:00Z",
              "inQty": {
                "rTime": "2023-10-05T09:40:12.247Z",
                "rType": "E",
                "kwh": 0,
                "m3": 0
              },
              "outQty": {
                "rTime": "2023-10-05T09:40:12.248Z",
                "rType": "E",
                "kwh": 0,
                "m3": 0
        

## Interface status 

| Service                    | Status                                                                                                                       | Timeline           |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------|--------------------|
| agreement                  | implemented                                                                                                                  |                    |
| agreementCoordination      | notMVP                                                                                                                       | planned 2024 Q3 Q4 |
| balanceState               | rfc                                                                                                                          | expected 2024 Feb  |
| connectionState            | notMVP                                                                                                                       | planned 2024 Q3 Q4 |
| customer                   | rfc                                                                                                                          | expected 2024 Feb  |
| directMessage              | notMVP                                                                                                                       | planned 2024 Q3 Q4 |
| eic                        | notMVP                                                                                                                       | planned 2024 Q3 Q4 |
| gridagreementmeteringpoint | N/A                                                                                                                          |                    |
| jointInvoice               | rfc                                                                                                                          | expected 2024 Feb  |
| meteringData               | meter-data - implemented<br/>meter-data/search - implemented<br/>meter-data/status - waiting<br/>meter-data/change - waiting | expected ?         |
| meteringPoint              | implemented                                                                                                                  |                    |
| networkBill                | rfc                                                                                                                          | expected 2024 Feb  |

notMVP - will be implemented after go-live.<br/>
rfc - interface spec, waiting in development queue.