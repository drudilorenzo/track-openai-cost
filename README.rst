.. image:: https://img.shields.io/badge/chatGPT-74aa9c.svg?logo=openai
.. image:: https://img.shields.io/pypi/pyversions/setuptools.svg

==================
OpenAI Cost Logger
==================

* Simple **cost logger** for **OpenAI requests**.
* Track the cost of every request you make to OpenAI and visualize them in a user-friendly way.
* Homepage on `PyPI <https://pypi.org/project/openai-cost-logger/>`_.
* `Demo file <https://github.com/drudilorenzo/track-openai-cost/blob/master/demo.ipynb>`_ with a usage example.

How to install:
---------------
* .. code-block:: python

      pip install openai-cost-logger

* .. code-block:: python

      from openai_cost_logger import OpenAICostLogger
      from openai_cost_logger import OpenAICostLoggerViz
      from openai_cost_logger import OpenAICostLoggerUtils
      from openai_cost_logger import OpenAICostLogger_Singleton
      from openai_cost_logger import DEFAULT_LOG_PATH, MODELS_COST

Key Features:
-------------
* Track the cost of every request you make and save them in a JSON file.
* Choose the feature you want to track (prompt_tokens, completion_tokens, completion, prompt, etc.).
* Check the cost of your requests filtering by model or strftime aggregation (see the docs).

Models supported:
-------------------
* The generation of responses is totally up to the user. The library supports every model whose response contains the fields **usage.prompt_tokens** and **usage.total_tokens** (e.g. chat completions, embeddings, etc.).

Multithreading:
---------------
* Be aware that the classic cost logger is not thread-safe.
* If you want to use it in a multithreading environment, you should use the **thread-safe** version of the logger: ``OpenAICostLogger_Singleton``. The interface is the same as the classic logger. This will prevent multiple threads from writing to the same file at the same time.

Note:
-----
* Every cost is specified per **million tokens**.
* If you don't specify the cost, the library will look to the **MODELS_COST** dictionary and get the cost of the model you are using. Be aware that if the model is not in the dictionary, an exception will be raised.

Viz example:
-------------
.. image:: images/example.png
   :alt: Viz example (prints + plot)
   :align: center
