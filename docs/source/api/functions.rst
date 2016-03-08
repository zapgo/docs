.. _http-api:

=================
API: Transactions
=================

HTTP API endpoints for creating and listing various transaction types.

Send Wallet (``/transactions/send_wallet``)
-------------------------------------------

Creates a transaction to the specified user wallet.

**Method**: POST

Inputs
~~~~~~

The input is a JSON document passed as part of the body of the request.

Example input:

.. code-block:: json

    {
        "account": "ZAR",
        "amount": 20,
        "recipient": testuser@gmail.com,
    }

Description of the payload:


- ``to_from_reference``: Unique identifier of the recipient wallet, such as the wallet address. This type of send can only be used to send to wallets of the same currency as the account from which funds are being sent. If a username, email-address, or mobile number is provided and that user has multiple accounts for the same currency, funds will be sent to the user's default account.

- ``amount``: Amount to be sent to recipient

- ``account``: Account from which funds should be sent


Account Transfer (``/transactions/account_transfer``)
-----------------------------------------------------

Creates a transaction which transfers funds to another account. This API call should be preceded by
/quote/account_transfer.

**Method**: POST

Inputs
~~~~~~

The input is a JSON document passed as part of the body of the request.

Example input:

.. code-block:: json

    {
        "quote_reference": "zT1HOnWhPjzoIRM5SVGZ",
    }

Description of the payload:


- ``quote_reference``: Unique reference number of the quote specifying the details of the transaction to be created. This quote reference is obtained by running /quote/account_transfer.

Send Crypto (``/transactions/send_crypto``)
-------------------------------------------

Creates a transaction which sends a cryptocurrency (e.g. BTC, ETH, LTC) to a given address. This API call should be preceded by
/quote/send_crypto.

**Method**: POST

Inputs
~~~~~~

The input is a JSON document passed as part of the body of the request.

Example input:

.. code-block:: json

    {
        "quote_reference": "fIGKHI1Liyr7i54IehlU",
    }

Description of the payload:


- ``quote_reference``: Unique reference number of the quote specifying the details of the transaction to be created. This quote reference is obtained by running /quote/send_crypto.

Send Forex (``/transactions/send_forex``)
-----------------------------------------

Creates a transaction which transfers funds to another account. This API call should be preceded by
/quote/send_forex.

**Method**: POST

Inputs
~~~~~~

The input is a JSON document passed as part of the body of the request.

Example input:

.. code-block:: json

    {
        "quote_reference": "Byfx3pz21VhXZzjH1Eiw",
    }

Description of the payload:


- ``quote_reference``: Unique reference number of the quote specifying the details of the transaction to be created. This quote reference is obtained by running ``/quote/send_forex``.

List Transactions (``/transactions``)
-------------------------------------

Lists all transactions.

**Method**: GET

Outputs
~~~~~~~

Example output:

.. code-block:: json

    {
    "count": 4,
    "next": null,
    "previous": null,
    "results": [
        {
            "tx_type": "load_bitcoin",
            "transaction_code": "MEFdxPfl7cY8WRU7RH4p",
            "description": "Bitcoin Top Up",
            "full_description": null,
            "status": "Waiting",
            "message": null,
            "to_from_reference": "19GKntapgsYonGsHEEC5y7F2jeCttTyfJc",
            "to_from_type": "invalid",
            "currency": "ZAR",
            "amount": "100.0000",
            "charged_fee": "0.00",
            "balance": "0.00",
            "link_slug": "cryptocurrency",
            "link_id": null,
            "fee_id": 55,
            "created_timestamp": "2016-02-29T13:29:57.209226Z",
            "updated_timestamp": "2016-02-29T13:30:00.934139Z",
            "user": {
                "username": "wi@zapgo.co",
                "email": "wi@zapgo.co"
            },
            "meta": {
                "bitcoin_address": "19GKntapgsYonGsHEEC5y7F2jeCttTyfJc",
                "qr_code": "https://chart.googleapis.com/chart?chl=bitcoin%3A19GKntapgsYonGsHEEC5y7F2jeCttTyfJc%3Famount%3D0.01339124&cht=qr&chs=300&choe=UTF-8",
                "amount_required": 0.01339124,
                "amount_confident": 0.0,
                "amount_confirmed": 0.0,
                "expiry_timestamp": 1456753200000,
                "amount_unconfirmed": 0.0,
                "bitcoin_uri": "bitcoin:19GKntapgsYonGsHEEC5y7F2jeCttTyfJc?amount=0.01339124"
            }
        },
        {
            "tx_type": "load_bitcoin",
            "transaction_code": "LCwAHkpeQrbHR9p1PSaI",
            "description": "Bitcoin Top Up",
            "full_description": null,
            "status": "Waiting",
            "message": null,
            "to_from_reference": "1NQYFLXiqXrGkDJrRRcWLnAK6sTWNG5n7Y",
            "to_from_type": "invalid",
            "currency": "ZAR",
            "amount": "2.0000",
            "charged_fee": "0.00",
            "balance": "0.00",
            "link_slug": "cryptocurrency",
            "link_id": null,
            "fee_id": 54,
            "created_timestamp": "2016-02-25T18:59:50.271030Z",
            "updated_timestamp": "2016-02-25T18:59:54.437213Z",
            "user": {
                "username": "wi@zapgo.co",
                "email": "wi@zapgo.co"
            },
            "meta": {
                "bitcoin_address": "1NQYFLXiqXrGkDJrRRcWLnAK6sTWNG5n7Y",
                "qr_code": "https://chart.googleapis.com/chart?chl=bitcoin%3A1NQYFLXiqXrGkDJrRRcWLnAK6sTWNG5n7Y%3Famount%3D0.00027981&cht=qr&chs=300&choe=UTF-8",
                "amount_required": 0.00027981,
                "amount_confident": 0.0,
                "amount_confirmed": 0.0,
                "expiry_timestamp": 1456427393000,
                "amount_unconfirmed": 0.0,
                "bitcoin_uri": "bitcoin:1NQYFLXiqXrGkDJrRRcWLnAK6sTWNG5n7Y?amount=0.00027981"
            }
        },
        {
            "tx_type": "load_bitcoin",
            "transaction_code": "FtgEjS5NMGvaSd3s4Uij",
            "description": "Bitcoin Top Up",
            "full_description": null,
            "status": "Waiting",
            "message": null,
            "to_from_reference": "13Hko5yTNS3breA9CFgPEzPgVaPhbYskmV",
            "to_from_type": "invalid",
            "currency": "ZAR",
            "amount": "1.0000",
            "charged_fee": "0.00",
            "balance": "0.00",
            "link_slug": "cryptocurrency",
            "link_id": null,
            "fee_id": 53,
            "created_timestamp": "2016-02-23T14:37:25.849321Z",
            "updated_timestamp": "2016-02-23T14:37:29.666615Z",
            "user": {
                "username": "wi@zapgo.co",
                "email": "wi@zapgo.co"
            },
            "meta": {
                "bitcoin_address": "13Hko5yTNS3breA9CFgPEzPgVaPhbYskmV",
                "qr_code": "https://chart.googleapis.com/chart?chl=bitcoin%3A13Hko5yTNS3breA9CFgPEzPgVaPhbYskmV%3Famount%3D0.00014143&cht=qr&chs=300&choe=UTF-8",
                "amount_required": 0.00014143,
                "amount_confident": 0.0,
                "amount_confirmed": 0.0,
                "expiry_timestamp": 1456238848000,
                "amount_unconfirmed": 0.0,
                "bitcoin_uri": "bitcoin:13Hko5yTNS3breA9CFgPEzPgVaPhbYskmV?amount=0.00014143"
            }
        },
        {
            "tx_type": "load_bitcoin",
            "transaction_code": "QyRvZESJvcvjck3ZFO8l",
            "description": "Bitcoin Top Up",
            "full_description": null,
            "status": "Waiting",
            "message": null,
            "to_from_reference": "1Eg1emZgmGid49ZktTDmZcaUFCHm8fVsPC",
            "to_from_type": "invalid",
            "currency": "ZAR",
            "amount": "50.0000",
            "charged_fee": "0.00",
            "balance": "0.00",
            "link_slug": "cryptocurrency",
            "link_id": null,
            "fee_id": 52,
            "created_timestamp": "2016-02-23T10:52:47.882859Z",
            "updated_timestamp": "2016-02-23T10:52:50.465166Z",
            "user": {
                "username": "wi@zapgo.co",
                "email": "wi@zapgo.co"
            },
            "meta": {
                "bitcoin_address": "1Eg1emZgmGid49ZktTDmZcaUFCHm8fVsPC",
                "qr_code": "https://chart.googleapis.com/chart?chl=bitcoin%3A1Eg1emZgmGid49ZktTDmZcaUFCHm8fVsPC%3Famount%3D0.00698838&cht=qr&chs=300&choe=UTF-8",
                "amount_required": 0.00698838,
                "amount_confident": 0.0,
                "amount_confirmed": 0.0,
                "expiry_timestamp": 1456225369000,
                "amount_unconfirmed": 0.0,
                "bitcoin_uri": "bitcoin:1Eg1emZgmGid49ZktTDmZcaUFCHm8fVsPC?amount=0.00698838"
            }
        }]
    }