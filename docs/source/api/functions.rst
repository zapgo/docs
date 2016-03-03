.. _http-api:

Public API
==========

The ZapGo server exposes an HTTP API that can be used to manage users and transactions.

Create a transaction (``/transactions``)
----------------------------------------

Creates a transaction and submits it for validation.

**Method**: POST

Inputs
~~~~~~

The input is a JSON document passed as part of the body of the request.

The format of the JSON document is the following:

.. code-block:: json

    {
        "tx_type": "<string>",
        "currency": "<string>",
        "amount": "<string>",
        "account": "<string>",
        "to_from_reference": "<string>",
    }

Description of the payload:

- ``tx_type``: transaction type::

    ====================  ==============
    ``send_interwallet``  Send funds to another user.
    ``send_bitcoin``      Send bitcoin to an bitcoin address.
    ====================  ==============

