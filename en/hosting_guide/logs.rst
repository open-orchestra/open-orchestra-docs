Logs
====

Our Back Office logging is based on `Monolog`_.
Open Orchestra provides an interface to display all the user actions on the website.

.. image:: ../../images/log_preview.png

Configuration
-------------

Monolog uses channels to record the log.
To link a channel and a record, you will have to define an handler in a configuration file.

For instance, if you want to store the logs in mongo, you will have to define a handler with the database connection parameters.
The level entry indicates the information type to record in the logs.
Each level is a number which value is standardized in the PSR-3 recommendation.
For instance 200 is the value for the "info" level.
The different levels are defined in the `Monolog documentation`_

.. code-block:: yaml

        mongo:
            type: mongo
            level: 200
            mongo:
                host: "localhost"
                database: "%open_orchestra_cms.mongodb.database%"
                collection: log
            channels: [openorchestra]


The ``channels`` key defines the channels where the log are published.
If no channel is specified then the logs are written in all channels.
It's possible to put multiple channels or exclude one.
The services which have the channel ``openorchestra`` write only in this chanel
and our handler shows logs which are in the ``openorchestra`` channel.

The different possibilities of configuration about channels are explained in the `channels documentation`_.

Processor
---------
When you publish your log, some information may be missing.
Monolog allows you to add a processor which will fill up the logging information by adding some context.

To do it, you can create a service, tag it with ``monolog.processor``.
You can refer to the Monolog `processor documentation`_ for further example.

Logger
------

The services that write the logs are event subscribers.
They should be injected the ``Symfony\Bridge\Monolog\Logger`` in order to be functional and be tagged with ``monolog.logger``.

For instance:

.. code-block:: yaml

    open_orchestra_log.subscriber.node:
        class: %open_orchestra_log.subscriber.node.class%
        arguments: [@logger]
        tags:
            - { name: kernel.event_subscriber }
            - { name: monolog.logger, channel: openorchestra }

In Open Orchestra an event is dispatched on most user actions (ie. creation, update of elements...).
This event is caught to publish the log message in the right channel.
A log message takes two parameters, a translation key and a context (data array about the message).
The messages are located in the translation file, for instance:

.. code-block:: yaml

    open_orchestra_log:
        node:
            update: Update a node with node id node_id, node version node_version and node language node_language

In this example, the variables (node_id, node_version, node_language) are defined in the context,
they are replaced on display.

The different subscribers are in ``OpenOrchestra\LogBundle\EventSubscriber``.

.. _`Monolog`: https://github.com/Seldaek/monolog
.. _`Monolog documentation`: https://github.com/Seldaek/monolog/blob/master/README.mdown#log-levels
.. _`processor documentation`: http://symfony.com/fr/doc/current/cookbook/logging/monolog.html
.. _`channels documentation`: http://symfony.com/doc/current/cookbook/logging/channels_handlers.html