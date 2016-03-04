.. _http-api:

Public API
==========

The ZapGo server exposes an HTTP API that can be used to manage users and transactions.

Create a transaction (``/transactions``)
----------------------------------------

Creates a transaction and returns the result.

**Method**: POST

Inputs
~~~~~~

The input is a JSON document passed as part of the body of the request.

The format of the JSON document is the following:

.. code-block:: json

    {
        "tx_type": "<string>",
        "to_from_reference": "<string>",
        "amount": "<string>",
        "currency": "<string>",
        "account": "<string>",
    }

    or

    {
        "quote_reference": "<string>",
    }

Description of the payload:

- ``tx_type``: transaction type

    ====================  ==================================================================================================
    ``send_interwallet``  Funds are sent to the user associated with the unique reference specified in the to_from_reference
    ====================  ==================================================================================================

- ``to_from_reference``: unique identifier of the recipient: email address, mobile number, username or bitcoin address

- ``amount``: amount to be sent to recipient

- ``currency``: currency code of the currency in which the amount has been specified. e.g. 'ZAR', 'BTC', 'XBT'

- ``account``: account from which funds should be sent

- ``quote_reference``: the quote_reference that was returned when using the ``/quote_forex`` or ``/quote_airtime`` endpoints. When a quote_reference is provided, no other parameters need to be specified.
